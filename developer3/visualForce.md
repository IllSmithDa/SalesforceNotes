# Visual Force controller 

  1. Standard Controller - This will do all the hardwork for you... point 1 and 2 listed above... fetches one record 

  2. Standard List Controller - fetches multiple records and pass it on to the UI

  3. Every object in SFDC, be it standard object like ACCOUNT, CONTACTS, LEADS.. or your Custom objects like STUDENT MASTER, MARKS... a standard controller is available 

  4. Every object custom and standard object.. like account, oppty, leads, contacts... or custom objects like student master, marks etc...  you always by default have a standard controller for each of these objects...

  5. Standard Controller-- Standard and Custom objects  --  VF page - One record -SOBJECT

  6. Standard List controller-- Standard and Custom objects  --  VF page - Multiple records - COLLECTION

  7. Custom Controller-- Standard and Custom objects  --  VF page + custom controller logic using an apex class -one record

  8. Custom List Controller-- Standard and Custom objects  --  VF page + custom controller logic using an apex class -Multiple records 

  9. Controller extensions -- Standard and Custom objects  -- A controller extension is an apex class that extends the functionality of a std or custom controller.

  10. Standard and custom controller cannot be used together.. in a vf page...
  
  11. Controller - MVC --   standard controller you need not write any code... SFDC platform takes care of data retrieval-SOQL and DMLs (insert, update etc)

  12. Global Actions - short cuts and quick actions to otherwise lengthy actions 

# Invoking Standard and Custom controller 

  1. standardController="Pen__c"

  2. controller="Example" 

    - Example is the custom controller class

# Visual force page using a standard controller 

  1. <apex:page standardController="Account">
     <apex:form >
     <apex:pageBlock title="My Content">
     <apex:pageblockButtons>
         <apex:commandButton action="{!Save}" value="Save"/>
         </apex:pageblockButtons>
         <apex:pageBlockSection title="My Content Section" columns="2">
             <apex:inputField value="{!Account.name}"/>
             <apex:inputField value="{!Account.fax}"/>
             <apex:inputField value="{!Account.phone}"/>
             <apex:inputField value="{!Account.accountNumber }"/>
         </apex:pageBlockSection>
     </apex:pageBlock>
     </apex:form>    
     </apex:page>

    * Save is a method that saves the record to the Account Object

# Getter and Setter 

  1. When we want to refer Apex class variables in the visualforce page we need to use Apex getter and setter methods. 

  2. Setter 

    * This will take the value from the visualforce page and stores to the Apex variable name.

  3. Getter 

    * his method will return a value to a visualforce page whenever a name variable is called.

      - get method ( )

    * When visualforce page want to get the value of a variable defined in the Apex. It will invoke get method of that variable.

    When visualforce page want to get the value of a variable defined in the Apex. It will invoke get method of that variable.

    * Example : <apex:outputlabel > {!name} </apex:outputlabel>.

       - In the above example, Visualforce page is trying to use name variable which is declared in Apex class. So it invokes automatically getname( ) method in the Apex class and this method will return the value of that variable.

    * Setter method

      - Setter method  will take the value from the visualforce page and stores to the Apex variable name.To understand about setter method ( ), let us write an Apex class for passing the values and saving the values to Apex variables.

# Custom Controller Example 

  1. <apex:page controller="Example" >
         <apex:form >
         <apex:pageBlock title="My Content">
             <apex:pageBlockSection title="My Content Section" columns="2">
             <apex:outputLabel >Enter name:</apex:outputLabel>
                 <apex:inputText value="{!name}"/>
                 <apex:commandButton value="Click" Action="{!showmessage}"      reRender="One"/>
                 <apex:outputLabel id="One">{!message}</apex:outputLabel>
             </apex:pageBlockSection>
             </apex:pageBlock>
         </apex:form>
     </apex:page>

      * reRender once will keep the value the same even if you refresh preserving the current value until new one is given or session has ended

      * The Action attribute is the logic that occurs when the button is clicked

   2. public with sharing class Example {
          public string name{set;get;}
          public string message{get;set;}
          public void showmessage(){
              message='Welcome'+name;
          }
      }

# Controller Extensions

  1. You can either extend a standard controller or extend a custom controller
  
  2. A controller extension is an apex class that extends the functionality of a std or custom controller.

  3. use controller extensions when you want to leverage the built-in functionality of a std controller but override one or more actions,such as edit,view,save or delete.You want to add

# Controller Example 

<apex:page standardController="Account" extensions="myControllerExtension">
    <apex:form >
        <apex:pageBlock title="My Content"> 
            <apex:pageBlockSection title="My Content Section" columns="2">

                <Apex:commandButton value="Greeting" Action="{!ShowGreeting}" reRender="One" />
                <Apex:outPutLabel id="One"> {!message} </Apex:outPutLabel> 
                
                <apex:inputField value="{!Account.name}" required="False"/> 
                <apex:inputField value="{!Account.Industry}" required="False"/>
                <apex:commandButton value="Save" action="{!save}"/>
                
            </apex:pageBlockSection>            
      </apex:pageBlock>
    </apex:form>
</apex:page>
 
  * The Name field of the Account object has its field requirements overwritten by setting Name as required field no longer by setting required attribute to false 

2. public class myControllerExtension {

      public string message{get;set;} 
      
      public myControllerExtension(ApexPages.StandardController stdController)   {
           //code
      }
  
      public void ShowGreeting() {
          message = 'How are you?' ;
      }
    }

# Order of Operation in VF Pages 

  1. https://developer.salesforce.com/docs/atlas.en-us.200.0.pages.meta/pages/pages_controller_postback_request.htm

  2. During a postback request, the view state is decoded and used as the basis for updating the values on the page.

  3. After the view state is decoded, expressions are evaluated and set methods on the controller and any controller extensions, including set methods in controllers defined for custom components, are executed.

    * These method calls do not update the data unless all methods are executed successfully. For example, if one of the methods updates a property and the update is not valid due to validation rules or an incorrect data type, the data is not updated and the page redisplays with the appropriate error messages.

  4. The action that triggered the postback request is executed. If that action completes successfully, the data is updated. If the postback request returns the user to the same page, the view state is updated.

  5. The resulting HTML is sent to the browser.

# Order of execution simplified 

  1. Constructor 

  2. Action

  3. Getters