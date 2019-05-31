# Server-Side Controller Concepts

  1. Server calls are expensive, and can take a bit of time. Milliseconds when things are good, and long seconds when the network is congested. You don’t want apps to be locked up while waiting for server responses.

    * The solution to staying responsive while waiting is that server responses are handled asynchronously. 

    *  What this means is, when you click the Create Expense button, your client-side controller fires off a server request and then keeps processing. It not only doesn’t wait for the server, it forgets it ever made the request! 

    * Then, when the response comes back from the server, code that was packaged up with the request, called a callback function, runs and handles the response, including updating client-side data and the user interface.

# Querying for Data from Salesforce

  1. The first step is to create your Apex controller. Apex controllers contain remote methods your Lightning components can call. In this case, to query for and receive expenses data from Salesforce.

    * public with sharing class ExpensesController {

          // STERN LECTURE ABOUT WHAT'S MISSING HERE COMING SOON
          @AuraEnabled
          public static List<Expense__c> getExpenses() {
              return [SELECT Id, Name, Amount__c, Client__c, Date__c, 
                             Reimbursed__c, CreatedDate 
                      FROM Expense__c];
          }

      }

      - Apex controller method  and it runs a SOQL query and returns the results. 
    
    * There are only two specific things that make this method available to your Lightning Components code

      - The @AuraEnabled annotation before the method declaration. “Aura” is the name of the framework at the core of Lightning Components. You’ve seen it used in the namespace for some of the core tags, such as <aura:component>. Now you know where it comes from.

      - The static keyword. All @AuraEnabled controller methods must be static methods, and either public or global scope. 

    * If these requirements remind you of remote methods for Visualforce’s JavaScript remoting feature, that’s not a coincidence. The requirements are the same, because the architecture is very similar at key points.

    * One other thing worth noting is that the method doesn’t do anything special to package the data for Lightning Components.

    * It just returns the SOQL query results directly. The Lightning Components framework handles all the marshalling/unmarshalling work involved in most situations. 

# Loading Data from Salesforce

  1. The next step is to wire up the expenses component to the server-side Apex controller

  2. Change the opening <aura:component> tag of the expenses component to point at the Apex controller, like this.

    * <aura:component controller="ExpensesController">

        - However, pointing to the Apex controller doesn’t actually load any data, or call the remote method. Like the auto-wiring between the component and (client-side) controller, this pointing simply lets these two pieces “know about” each other. 

        - This “knowing” even takes the same form, another value provider, which we’ll see in a moment. But the auto-wiring only goes so far. It remains our job to complete the circuit.

    * In this case, completing the circuit means the following.

        - When the expenses component is loaded,

        - Query Salesforce for existing expense records, and

        - Add those records to the expenses component attribute.

  3. The first item, triggering behavior when the expenses component is first loaded, requires us to write an init handler.

      * <aura:handler name="init" action="{!c.doInit}" value="{!this}"/>

        - The <aura:handler> tag is how you say that a component can, well, handle a specific event. 

        - In this case, we’re saying that we’ll handle the init event, and that we’ll handle it with the doInit action handler in our controller.

        -Setting value="{!this}" marks this as a “value event.” Just know that you should always add this attribute-value pair to an init event

  4.  Both of the remaining steps take place in the doInit action handler, so let’s look at it. Add the following code to the expense component’s controller.

    * // Load expenses from Salesforce
      doInit: function(component, event, helper) {
          
          // Create the action
          var action = component.get("c.getExpenses");
          
          // Add callback behavior for when response is received
          action.setCallback(this, function(response) {
              var state = response.getState();
              if (state === "SUCCESS") {
                  component.set("v.expenses", response.getReturnValue());
              }
              else {
                  console.log("Failed with state: " + state);
              }
          });
          // Send action off to be executed
          $A.enqueueAction(action);
      },
    * here’s the outline of what this code does:

      - Create a remote method call.

      - Set up what should happen when the remote method call returns

      - Queue up the remote method call

    * var action = component.get("c.getExpenses");

      - This line of code creates our remote method call, or remote action. And at first the component.get() part looks familiar. We’ve done that many times at this point.

      - Instead of using v.something, now it is c.something. In fact, c is also used in epxression in the component markup. 

      - Here the c represents the Apex controller. 

      - So, c. can be used in the Component markup, which refers to client controller

      - c. can be used in a client controller to refer to the server side controller

      - c: can be used in markup to referto a defauilt namespace

      - v.something returns to a us reference to a child component when used in client controller

    * $A.enqueueAction(action);

      - $A is framework global variable that provides a number of important functions and services. 

      - $A.enqueueAction(action) adds the server call that we’ve just configured to the Aura component framework request queue.

      - It queues up the server request. As far as your controller action is concerned, that’s the end of it. You’re not guaranteed when, or if, you’ll hear back.

# Server Calls, Asynchronous Execution, and Callback Functions

  1. doInit: function(component, event, helper) {
        // Load expenses from Salesforce
        var action = component.get("c.getExpenses");
        action.setCallback(
            // Here’s my number,
            // Call me maybe
        );
        $A.enqueueAction(action);
    },

    * action.setCallback(this, function(response) { ... });
      
      - 'this' is the scope in which the callback will execute; here 'this' is the action handler function itself. Think of it as an address, or...maybe a number. The function is what gets called when the server response is returned.

      - The overall effect is to create the request, package up the code for what to do when the request is done, and send it off to execute. At that point, the action handler itself stops running.

# Handling the Server Response

  1. Example of a callback function 
    
    * function(response) {
        var state = response.getState();
        if (state === "SUCCESS") {
            component.set("v.expenses", response.getReturnValue());
        }
     }

      - Callback functions take a single parameter, response, which is an opaque object that provides the returned data, if any, and various details about the status of the request.

    * In this specific callback function, we do the following.

      - Get the state of the response.

      - If the state is SUCCESS, that is, our request completed as planned, then:

      - Set the component’s expenses attribute to the value of the response data.

  2. <aura:attribute name="expenses" type="Expense__c[]"/>

    * And our server-side controller action has a method signature that defines its return data type. 

  3. public static List<Expense__c> getExpenses() { ... }

    * The types match, and so we can just assign one to the other. 

# Apex Controllers for Aura Components Example

  1. public with sharing class ExpensesController {
         @AuraEnabled
         public static List<Expense__c> getExpenses() {
             // Perform isAccessible() checking first, then
             return [SELECT Id, Name, Amount__c, Client__c, Date__c, 
                            Reimbursed__c, CreatedDate 
                     FROM Expense__c];
         }
         
         @AuraEnabled
         public static Expense__c saveExpense(Expense__c expense) {
             // Perform isUpdateable() checking first, then
             upsert expense;
             return expense;
         }
     }
  
    * First, we’ve added only one new @AuraEnabled method, saveExpense(). It takes an Expense (Expense__c) object and upserts it. 
        
      - This allows us to use it to both create new records and to update existing records.

    * Next, notice that we created the class with the with sharing keywords. This automatically applies your org’s sharing rules to the records that are available via these methods.

      - For example, users would normally only see their own expense records. Salesforce handles all the complicated SOQL rules for you, automatically, behind the scenes. 
    
    * Using the with sharing keywords is one of the essential security measures you need to take when writing server-side controller code.

      - However, it’s a measure that’s necessary, but not sufficient. 

      - Do you see the comments about performing isAccessible() and isUpdateable() checks? with sharing only takes you so far. In particular, you need to implement object- and field-level security (which you’ll frequently see abbreviated to FLS) yourself.

  2. For example, here’s a version of our getExpenses() method with this security minimally implemented. 
     
     @AuraEnabled
     public static List<Expense__c> getExpenses() {
         
         // Check to make sure all fields are accessible to this user
         String[] fieldsToCheck = new String[] {
             'Id', 'Name', 'Amount__c', 'Client__c', 'Date__c', 
             'Reimbursed__c', 'CreatedDate'
         };
         
         Map<String,Schema.SObjectField> fieldDescribeTokens = 
             Schema.SObjectType.Expense__c.fields.getMap();
         
         for(String field : fieldsToCheck) {
             if( ! fieldDescribeTokens.get(field).getDescribe().isAccessible()) {
                 throw new System.NoAccessException();
             }
         }
         
         // OK, they're cool, let 'em through
         return [SELECT Id, Name, Amount__c, Client__c, Date__c, 
                        Reimbursed__c, CreatedDate 
                 FROM Expense__c];
     }

       * It’s quite an expansion from our initial one-liner, and it’s still just adequate.

       * Also, describe calls are expensive. If your app is calling this method frequently, you should find a way to optimize or cache your access checks per user

       * More details on security covered in another section 

# Saving Data to Salesforce

  1. Before we implement the Add Expense form for real, no cheating, let’s first look at how creating a new record is a different challenge from reading existing records.

  2. ith doInit(), we simply read some data, and then updated the user interface of the app.

  3. Creating a new record is more involved. We’re going to read values from the form, create a new expense record locally, send that record off to be saved on the server, and then, when the server tells us it’s saved, update the user interface, using the record returned from the server.

  4. First, make sure you’ve saved the updated version of the Apex controller, the preceding version that includes the saveExpense() method.

  5. Remember when we showed you how to handle the form submission? When at least one of the fields is invalid, you’ll see an error message and the form isn’t submitted. The error message clears when all fields are valid.

  6. Because we put all of the details of (and all the cheating on) creating a new expense into the helper createExpense() function, we don’t need to make any other changes in the controller. 

  7. So, all we need to do is change the createExpense() function in the helper, to do all those complicated things we mentioned previously. Here’s that code. 

    * createExpense: function(component, expense) {

          var action = component.get("c.saveExpense");
          
          action.setParams({
              "expense": expense
          });

          action.setCallback(this, function(response){

              var state = response.getState();

              if (state === "SUCCESS") {
                  var expenses = component.get("v.expenses");
                  expenses.push(response.getReturnValue());
                  component.set("v.expenses", expenses);
              }
          });
          $A.enqueueAction(action);
      },

    * We begin by creating the action, with component.get("c.saveExpense") getting the new Apex controller method.

    * Next we attach a data payload to the action.  
      
      - You just use action.setParams() and provide a JSON-style object with parameter name-parameter value pairs. 
      
      - The one trick, and it’s important, is that your parameter name must match the parameter name used in your Apex method declaration.

    * Next we set the callback for the request.

      - Again, this is what will happen when the server returns a response.

      - If you compare this callback function with our original createExpense helper function, it’s virtually identical (minus the disgusting hack). 

    * If you compare this callback function with our original createExpense helper function, it’s virtually identical (minus the disgusting hack). 

      - The only real difference is, instead of push()ing our local version of the new expense into the array, we’re push()ing the server’s response

      - . Once again the server-side and client-side data types match, so we don’t have to do any extra work.

# Things to Watch Out For

  1. While we’ve covered all of the essentials for connecting your client-side Aura component code with server-side Apex code, there are a couple of things that are kind of worth pointing out before they bite you in the you-know-where.

    * The first issue is case sensitivity, and this boils down to Apex and Salesforce in general are case-insensitive, but JavaScript is case-sensitive. That is, “Name” and “name” are the same in Apex, but different in JavaScript. 

    * So here’s a best practice for you: Always use the exact API name of every object, field, type, class, method, entity, element, elephant, or what have you. Always, everywhere, even when it doesn’t matter. 

  2. The other issue we’d like to draw your attention to is the nature of “required.”

    * <lightning:input aura:id="expenseform" 
                 label="Expense Name"
                 name="expensename"
                 value="{!v.newExpense.Name}"
                 required="true"/> 

      - The <lightning:input> tag has its required attribute set to true. These both illustrate only one meaning of required, which is “set the user interface of this element to indicate the field is required.”

      - In other words, this is cosmetic only. There’s no protection for the quality of your data here.

    * var validExpense = component.find('expenseform').reduce(function (validSoFar, inputCmp) {
          // Displays error messages for invalid fields
          inputCmp.showHelpMessageIfInvalid();
          return validSoFar && inputCmp.get('v.validity').valid;
      }, true);

       - Another meaning of the word “required” is illustrated in the validation logic we wrote for the same field. 

       - The word “required” is nowhere to be seen, but that’s what the validation logic enforces. You must set a value for the expense name field. 

       - Your expense form won’t submit a new expense with an empty name

  3. How do you enforce, and we mean enforce, a data integrity rule about, in this example, expense name? You do it server-side. 

    * And not just anywhere server-side. You put the rule in the field definition, or you encode it into a trigger. 

    * Or, if you’re a belt-and-suspenders kind of engineer, as all right thinking engineers are, both.

    * For true data integrity, when “required” means required, enforce it at the lowest level possible.

