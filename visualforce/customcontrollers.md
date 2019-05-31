# Introduction to Custom Controllers

  1. Custom controllers contain custom logic and data manipulation that can be used by a Visualforce page. 

    * For example, a custom controller can retrieve a list of items to be displayed, make a callout to an external web service, validate and insert data, andmore—and all of these operations will be available to the Visualforce page that uses it as a controller.

  2. Controllers typically retrieve the data to be displayed in a Visualforce page, and contain code that executes in response to page actions, such as a button being clicked. When you use the standard controller, a great deal of, well, standard functionality is provided for you by the platform.

  3. You can write a custom controller using Apex and completely control your app’s logic from start to finish.

# Create a Visualforce Page that Uses a Custom Controller

  1. Open the Developer Console and click File | New | Visualforce Page to create a new Visualforce page. Enter ContactsListController for the page name.

  2. In the editor, replace any markup with the following.

    * <apex:page controller="ContactsListController">
        <apex:form>
          <apex:pageBlock title="Contacts List" id="contacts_list">
              
              <!-- Contacts List goes here -->
          </apex:pageBlock>
        </apex:form>
      </apex:page>

      - When you try to save this page, you’ll get an error, because ContactsListController doesn’t exist yet. No worries, we’ll fix that next. 
  
# Creating the Custom Controller Apex Class

  1. Open the Developer Console and click File | New | Apex Class to create a new Apex class. Enter ContactsListController for the class name.

  2. In the editor, replace any code with the following.

    * public class ContactsListController {
        // Controller code goes here
      }

      - As with Visualforce pages, you need to save your changes to Apex when you change it. It’s not much, and it doesn’t do anything yet, but it does make the error go away on the Visualforce page. So…
  
  3. Switch back to the Visualforce page and save it again. The error message should go away, and the page is saved successfully.
 
  4. Click Preview to open a preview of your page that you can look at while you make changes. A new window should open, showing the standard Salesforce page header and sidebar elements, but no content yet.

    * Click Preview to open a preview of your page that you can look at while you make changes. A new window should open, showing the standard Salesforce page header and sidebar elements, but no content yet.

    * You might have noticed that this custom controller class doesn’t inherit from another class, nor does it implement an interface promising to conform to the requirements of a Visualforce controller.

    * Even complex controllers don’t do these things, because there isn’t any such class to inherit from or interface to implement. This leaves you free to create your own classes and interfaces as your experience with Apex increases.

# Add a Method to Retrieve Records

  1. In the ContactsListController class, replace the // Controller code goes here comment line with the following code.

    * private String sortOrder = 'LastName';
    
      public List<Contact> getContacts() {
        
        List<Contact> results = Database.query(
            'SELECT Id, FirstName, LastName, Title, Email ' +
            'FROM Contact ' +
            'ORDER BY ' + sortOrder + ' ASC ' +
            'LIMIT 10'
        );
        return results;
      }

      - This code adds one private member variable, a string named sortOrder, and one public method, getContacts(). sortOrder is pretty easy to understand, it’s just the name of the field to sort the contacts by.

      - getContacts() is also fairly simple, but if you haven’t seen Apex before, it might be hard to parse at first. The effect of the method is to perform a SOQL query to get a list of contact records, and then return that list of contacts to the method caller.

  2. In the ContactsListWithController page, replace the <!-- Contacts List goes here --> comment line with the following markup.

    * <!-- Contacts List -->
      <apex:pageBlockTable value="{! contacts }" var="ct">
          <apex:column value="{! ct.FirstName }"/>
          <apex:column value="{! ct.LastName }"/>
          <apex:column value="{! ct.Title }"/>
          <apex:column value="{! ct.Email }"/>   
      </apex:pageBlockTable>

      - What’s different is what happens when the {! contacts } expression is evaluated. On this page, Visualforce translates that expression into a call to your controller’s getContacts() method. That method returns a list of contact records, which is exactly what the <apex:pageBlockTable> is expecting.

      - he getContacts() method is called a getter method, and it’s a general pattern, where {! someExpression } in your Visualforce markup automatically connects to a method named getSomeExpression() in your controller. This is the simplest way for your page to get access to the data it needs to display.

# Add a New Action Method

  1. Create action methods in your custom controller to respond to user input on the page.

  2. In the ContactsListController class, below the getContacts() method, add the following two methods.

    * public void sortByLastName() {
        this.sortOrder = 'LastName';
      }
          
      public void sortByFirstName() {
        this.sortOrder = 'FirstName';
      }
      
      - These two methods change the value of the sortOrder private variable. sortOrder is used in the SOQL query that retrieves the contacts, and changing sortOrder will change the order of the results.

  3. n the ContactsListWithController page, replace the two <apex:column> tags for ct.FirstName and ct.LastName with the following markup

    * <apex:column value="{! ct.FirstName }">
          <apex:facet name="header">
              <apex:commandLink action="{! sortByFirstName }" 
                  reRender="contacts_list">First Name
              </apex:commandLink>
          </apex:facet>
      </apex:column>
      <apex:column value="{! ct.LastName }">
          <apex:facet name="header">
              <apex:commandLink action="{! sortByLastName }" 
                  reRender="contacts_list">Last Name
              </apex:commandLink>
          </apex:facet>
      </apex:column>

        - Although the visual appearance remains the same, if you click the First Name and Last Name column headers now, they will change the sort order for the contacts list. Nice!

        - The new markup adds two nested components to each of the <apex:column> components. <apex:column> by itself has a plain text header, but we want to make the header clickable. <apex:facet> lets us set the contents of the column header to whatever we want. 

        - The link is created using the <apex:commandLink> component, with the action attribute set to an expression that references the action method in our controller.

        -  When the link is clicked, it fires the action method in the controller. The action method changes the sort order private variable, and then the table is rerendered. When the table is rerendered, {! contacts } is reevaluated, which reruns the query with whatever sort order was just set. The final result is the table is resorted in the order requested by the user’s click

# Alternatives

  1. An alternative to getters and setters is to use Apex properties. Properties are kind of a combination of a variable with getter and setter methods, with a syntax that groups them together more clearly. A simple property that references a custom object might be declared like this. 

    * public MyObject__c myVariable { get; set; }

  2. Properties can be public or private, and can be read-only, or even write-only, by omitting the get or set. And you can create implementations for the get or set methods, when you want to perform additional logic besides simply saving and retrieving a value. 

  3. Properties are a general feature of Apex, not specific to Visualforce. Apex is a complete programming language, and in addition to being the natural partner for building complex Visualforce pages, it’s used in many other Lightning Platform development contexts. See the Apex topics elsewhere here, and the resources at the end of this page for many ways to learn to use Apex fully.

  3. The lifecycle of a Visualforce request and response can seem complex initially. In particular, it’s important to understand that there’s no specific order in which getters or setters (or properties, if you use them) are called, so you must not introduce order-of-execution dependencies between them