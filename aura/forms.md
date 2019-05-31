# Salesforce Lightning Design System or SLDS

  1. SLDS is automatically available to your components when they run inside Lightning Experience or the Salesforce app.

  2. Can be known as the one.app container.

  3. However, SLDS is not available by default in a stand-alone app, or when you use your components in Lightning Out or Lightning Components for Visualforce.

    * These are different app containers, and they provide different services and resources. 

  4. Example of creating a new expensesApp.app Lightning application

    * <aura:application extends="force:slds">
       
        <!-- This component is the real "app" -->
        <!-- c:expenses/ -->
      </aura:application>

      -  We can now use SLDS tools and techniques, without worrying about where the SLDS resources—style sheets, icons, and so on—come from

      - The extends="force:slds" attribute activates SLDS in this app, by including the same Lightning Design System styles provided by Lightning Experience and the Salesforce app

      - But note that this harness app is just a wrapper, a shell. The real app is the expenses component, which we haven’t created. 

      - By way of the wrapper app, our components use the extends="force:slds" mechanism to get access to SLDS when they run from this application.

      - When they run inside Lightning Experience or the Salesforce app, with no code changes, they use that container’s automatic inclusion of SLDS.

# The expenses App Component - What it looks like 

  1.  <aura:component>
          <!-- PAGE HEADER -->
          <lightning:layout class="slds-page-header slds-page-header--object-home">
              <lightning:layoutItem>
                  <lightning:icon iconName="standard:scan_card" alternativeText="My Expenses"/>
              </lightning:layoutItem>
              <lightning:layoutItem padding="horizontal-small">
                  <div class="page-section page-header">
                      <h1 class="slds-text-heading--label">Expenses</h1>
                      <h2 class="slds-text-heading--medium">My Expenses</h2>
                  </div>
              </lightning:layoutItem>
          </lightning:layout>
          <!-- / PAGE HEADER -->
          <!-- NEW EXPENSE FORM -->
          <lightning:layout>
              <lightning:layoutItem padding="around-small" size="6">
              <!-- [[ expense form goes here ]] -->
              </lightning:layoutItem>
          </lightning:layout>
          <!-- / NEW EXPENSE FORM -->
      </aura:component>
    
      * What we’re creating here is the page header using the grid layout provided by the <lightning:layout> and <lightning:layout> components. size="6" creates a <div> container that’s 50% the total width (or size 6 of 12).

      * As you might have noticed, components in the lightning namespace resemble components in Lightning Experience and the Salesforce app

      * Notice the <lightning:icon> component renders your favorite SLDS icons in a snap. Gone are the days when you had to create a helper component for displaying SLDS icons. 

# Form Example 

  1. <div aria-labelledby="newexpenseform">
       <fieldset class="slds-box slds-theme--default slds-container--small">  
          <legend id="newexpenseform" class="slds-text-heading--small
           slds-p-vertical--medium">
           Add Expense
          </legend>
  
       <form class="slds-form--stacked">
           
           <lightning:input aura:id="expenseform" label="Expense Name"
                			 name="expensename"
                            value="{!v.newExpense.Name}"
                            required="true"/> 
           
           <lightning:input type="number" aura:id="expenseform" label="Amount"
                		     name="expenseamount"
                            min="0.1"
                            formatter="currency"
                            step="0.01"
                            value="{!v.newExpense.Amount__c}"
                            messageWhenRangeUnderflow="Enter an amount that's at least $0.10."/>
         
           <lightning:input aura:id="expenseform" label="Client"
                            name="expenseclient"
                            value="{!v.newExpense.Client__c}"
                            placeholder="ABC Co."/>
           
           <lightning:input type="date" aura:id="expenseform" label="Expense Date"
                            name="expensedate"
                            value="{!v.newExpense.Date__c}"/>
       
           <lightning:input type="checkbox" aura:id="expenseform" label="Reimbursed?"  
                            name="expreimbursed"
                            checked="{!v.newExpense.Reimbursed__c}"/>
           
           <lightning:button label="Create Expense" 
                             class="slds-m-top--medium"
                             variant="brand"
                             onclick="{!c.clickCreate}"/>
       </form>
      </fieldset>
    </div>

    * <lightning:input> is the Swiss army knife for input fields that’s infused with the goodness of SLDS styling.

      - Use it whenever you find yourself reaching for the <ui:input> component variety like <ui:inputText>, <ui:inputNumber>, and others.

      - Components in the ui namespace don’t come with SLDS styling and are considered to be legacy components.
    
      - Components in the ui namespace don’t come with SLDS styling and are considered to be legacy components.

    * min specifies the minimum value for the input.

    * There’s an aura:id attribute set on each tag.

      - It sets a (locally) unique ID on each tag it’s added to, and that ID is how you’ll read values out of the form fields. 

      - The fields all share the same ID in this example so that we can access them as an array for field validation. 

# Attributes for Salesforce Objects (sObjects)

  1. But first we need to look at the value attribute. Each tag has a value on it, set to an expression. For example, {!v.newExpense.Amount__c}. 

  2. v means this is a property of the view value provider. That means that this is an attribute on the component. (Which we haven’t created yet.)

  3. Based on the dot notation, you can tell that newExpense is some kind of structured data type. 

  4. From the “__c” that’s at the end of most of the property names, you can guess that these map back to custom fields, most likely on the Expense custom object.

  5. So, newExpense is probably an Expense object!

  6.  <aura:attribute name="newExpense" type="Expense__c"
       default="{ 'sobjectType': 'Expense__c',
                      'Name': '',
                      'Amount__c': 0,
                      'Client__c': '',
                      'Date__c': '',
                      'Reimbursed__c': false }"/>

    * The default attribute isn’t new, but the format of its value is.

    * It’s a JSON representation of an sObject, specifying the type of the object (again, the API name), and values for each of the fields to set on it by default.
    
# Handle Form Submission in an Action Handler

  1. ({
        clickCreate: function(component, event, helper) {

            var validExpense = component.find('expenseform').reduce(function (validSoFar, inputCmp) {

                // Displays error messages for invalid fields
                inputCmp.showHelpMessageIfInvalid();

                return validSoFar && inputCmp.get('v.validity').valid;
            
            }, true);

            // If we pass error checking, do some real work
            if(validExpense){

                // Create the new expense
                var newExpense = component.get("v.newExpense");
                console.log("Create expense: " + JSON.stringify(newExpense));
                helper.createExpense(component, newExpense);
            }
        }
     })

      * Note that this action handler function is basically divided into three sections, or steps:

        - Setup

        - Process form values

        - If there are no errors, do something

      * For setup, all we do is initialize the state of our error checking. 

        - It’s a simple flag, is this a valid expense?

        - Each time the clickCreate action handler is called, we’ll start on the assumption that the expense data is OK, and then invalidate it if we find a problem.

      * Here’s a rundown of the validExpense flag, with an initial value that’s set to true.

        - component.find('expenseform') gets a reference to the array of <lightning:input> fields that require validation.

        -  If the ID is unique, the reference returns the component. In this case, the ID is not unique and the reference returns an array of components.

        - The JavaScript reduce() method reduces the array to a single value that’s captured by validSoFar, which remains true until it finds an invalid field, changing validSoFar to false.

        - An invalid field can be a required field that’s empty, a field that has a number lower than a specified minimum number, among many others.

        - inputCmp.get('v.validity').valid returns the validity of the current input field in the array. 

        - inputCmp.showHelpMessageIfInvalid() displays an error message for invalid fields. 

        - <lightning:input> provides default error messages that can be customized by attributes like messageWhenRangeUnderflow, which you’ve seen in the expense form example.

      * When your controller needs a way to get to a child component, first set an aura:id on that component in markup, and then use component.find(theId) to get a reference to the component at runtime.

        - component.find() only lets you access direct child components.

      * Validation with <lightning:input> harnesses the power of the underlying HTML input element to process form values so you don’t have to in most cases.

        - Need to validate a telephone number? Use type="tel" and define the pattern attribute using a regular expression.

        - Need to validate a percentage value? Use type="number" with formatter="percent".

      * It’s when validation fails that things get interesting again. When the user enters invalid input, we want two things to happen:

        - Don’t try to create the expense.

        - Show a helpful error message.

        - For the first, we set the validExpense flag to false when the field validity referenced by inputCmp.get('v.validity').valid evaluates to false. For the second, we make use of the built-in validation errors or provide custom messages for the errors. 

        - In the expense form, the required name field displays “Complete this field” if the field is empty and you try to submit the form.

        - You can also provide your own custom message by specifying messageWhenValueMissing="Did you forget me?"

      *  Why don’t we pull the form values out of newExpense? Get the structured variable once, at the start of the action handler, and then just access its properties, instead of what could be a long series of find().get() calls?

        - The reason is simple: because we need references to the individual fields to be able to call showHelpMessageIfInvalid() on them. 

        - It’s also a good practice to validate the raw form data; your validation logic doesn’t know what kinds of processing might happen within the newExpense object.

# Create the New Expense

  1. First, let’s create a place to “store” new expenses. We’ll simply create a local-only array of expenses to hold them. At the top of expenses component markup, right before the newExpense attribute, add a new expenses attribute, which will hold an array of expense objects

    * <aura:attribute name="expenses" type="Expense__c[]"/>

  2. All we need to do is update the expenses array. Which, it turns out, is easy (in the cheater-cheater version of our form), and illustrates yet another important concept.

    * In our controller, we’ve hidden the work of actually creating the new expense behind this function call: helper.createExpense(component, newExpense).

      - In software development, another word for “hiding” is abstraction. And we’re using something called a helper to abstract away our cheating.

    * Three Facts about helpers

      - A component’s helper is the appropriate place to put code to be shared between several different action handlers. 

      - A component’s helper is a great place to put complex processing details, so that the logic of your action handlers remains clear and streamlined.

      - Helper functions can have any function signature. That is, they’re not constrained the way that action handlers in the controller are. Why is this? Because you are calling the helper function directly from your code. By contrast, the framework calls action handlers via the framework runtime. It’s a convention and recommended practice to always provide the component as the first parameter to helper functions. 

# Using the Helper 

  1.  In the Developer Console, click the HELPER button for the expenses component to create the associated helper resource, and then replace the example code with the following. 

    * ({
          createExpense: function(component, expense) {
              var theExpenses = component.get("v.expenses");
       
              // Copy the expense to a new object
              // THIS IS A DISGUSTING, TEMPORARY HACK
              var newExpense = JSON.parse(JSON.stringi  fy(expense));

              theExpenses.push(newExpense); 
              component.set("v.expenses", theExpenses);
          }
      })

      - First we get the array of expenses from the expenses attribute. 

      - Then we add the new expense “record” to it.

      - Then we update (set) the expenses attribute with the changed array

    * component.get("v.expenses") gets a reference to the array stored in the component attribute. component.set("v.expenses", theExpenses) simply sets the component attribute to the same reference.
      Sure, in between, the contents of the array has been added to, but the container is the same: the reference to the array hasn’t actually changed!

      - What component.set() does here isn’t update the value of the expenses attribute. It triggers notification that the expenses attribute has changed. 

      - The effect is that, anywhere in your app that you’ve referenced the expenses attribute in an expression, the value of that expression is updated, and that update cascades everywhere the expenses attribute was used. 

      - This all happens behind the scenes, handled by the Lightning Components framework, as part of the auto-wiring that happens when you use {!v.expenses}

      - To summarize, if this were plain JavaScript, you wouldn’t need the component.set(). In order to trigger underlying effects built into the Aura Components programming model, you do. If you ever write some controller or helper code, test it, and nothing happens, make sure you’ve done the required component.set().

# Displaying the List of Expenses

  1. In the Developer Console, create a new Aura component named expenseItem, and replace the default markup with the following.

    * <aura:component>
          <aura:handler name="init" value="{!this}" action="{!c.doInit}"/>
          <aura:attribute name="formatdate" type="Date"/>
          <aura:attribute name="expense" type="Expense__c"/>
      
          <lightning:card title="{!v.expense.Name}" iconName="standard:scan_card"
                          class="{!v.expense.Reimbursed__c ?
                                 'slds-theme--success' : ''}">
              <aura:set attribute="footer">
                  <p>Date: <lightning:formattedDateTime value="{!v.formatdate}"/></p>
                  <p class="slds-text-title"><lightning:relativeDateTime value="{!v.formatdate}"/></p>
              </aura:set>
              <p class="slds-text-heading--medium slds-p-horizontal--small">
                 Amount: <lightning:formattedNumber value="{!v.expense.Amount__c}" style="currency"/>
              </p>
              <p class="slds-p-horizontal--small">
                  Client: {!v.expense.Client__c}
              </p>
              <p>
                  <lightning:input type="toggle" 
                                   label="Reimbursed?"
                                   name="reimbursed"
                                   class="slds-p-around--small"
                                   checked="{!v.expense.Reimbursed__c}"
                                   messageToggleActive="Yes"
                                   messageToggleInactive="No"
                                   onchange="{!c.clickReimbursed}"/>
              </p>
          </lightning:card>
      </aura:component>

      - This version includes SLDS markup to make it more stylish. Also, using the {!v.expense.Reimbursed__c ? 'slds-theme--success' : ''} expression sets the color green on the container when the expense has been reimbursed.

  2. Next, create a client-side controller expenseItemController.js with the following code.

    * ({
          doInit : function(component, event, helper) {
              var mydate = component.get("v.expense.Date__c");
              if(mydate){
                  component.set("v.formatdate", new Date(mydate));
              }
          },
      })

      - Here we are converting the date that’s returned by the server later to a JavaScript Date object, so that it’s displayed correctly by <lightning:formattedDateTime> and <lightning:relativeDateTime>. 

      - This conversion is handled during component initialization, captured by the <aura:handler> tag. 

      - This is a useful way to handle the initialization event and we’ll use this again later when we load data from Salesforce.

  3. In the Developer Console, create an Aura component named expensesList, and replace the default markup with the following.

    * <aura:component>
          <aura:attribute name="expenses" type="Expense__c[]"/>
          <lightning:card title="Expenses">
              <p class="slds-p-horizontal--small">
                  <aura:iteration items="{!v.expenses}" var="expense">
                      <c:expenseItem expense="{!expense}"/>
                  </aura:iteration>
              </p>
          </lightning:card>
      </aura:component>

      - This is a component that displays a list of expenses. It has one attribute, expenses, which is an array of expense (Expense__c) objects. 

      - It uses an <aura:iteration> to create an <c:expenseItem> for each of those expense objects.

  4. Now add the expensesList component to the end of expenses component. Add it right before the ending </aura:component> tag in expenses.cmp.

    * <c:expensesList expenses="{!v.expenses}"/>

      - What did we just do? We added the expensesList component to and passed the main expenses attribute into it

      - So now the instance of expenses that expensesList has is the same as the instance of expenses that the expenses component has.

      - They are references to the same array of records, and through the magic of Lightning Components, when the main expenses array is updated, the expensesList component will “notice” and rerender its list. 