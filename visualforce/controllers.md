# Visualforce Standard Controller

  1. Visualforce uses the traditional model–view–controller (MVC) paradigm, and includes sophisticated built-in controllers to handle standard actions and data access, providing simple and tight integration with the Lightning Platform database. 

  2. These built-in controllers are referred to generally as standard controllers, or even the standard controller.

  3. The MVC design pattern makes it easy to separate the view and its styling from the underlying database and logic. 

  4.  MVC, the view (the Visualforce page) interacts with a controller, and the controller provides functionality to the page.

    * For example, the controller can contain the logic to be executed when a button is clicked

    *  A controller also typically interacts with the model (the database)—making available data that the view might want to display, or pushing changes back to the database.

  5. Most standard and all custom objects have standard controllers that can be used to interact with the data associated with the object, so you don’t need to write the code for the controller yourself. 

  6. You can extend the standard controllers to add new functionality, or create custom controllers from scratch. Here you’ll learn about the standard controllers.

# Find a Record ID and Add It to the Request URL

  1. If you want to use the standard controller to reference a specific record, it needs to know the record identifier, or ID, of the record to work with. 
  
  2. It uses the ID to retrieve the data, and to save it back to the database when the record’s data is changed.

  3. When your Visualforce pages interact with other pages in your organization, you can automatically pass in the record’s identifier, and your Visualforce page can use that to look up and display that record’s data.  

  4. But during development your pages are stand-alone, so for your page to display data from a record in the database, you need to provide the record ID manually. The easiest way to do this is to add it as a GET parameter in the request URL.

# Record ID and Add It to the Request URL Example

  1. Open the Developer Console and click File | New | Visualforce Page to create a new Visualforce page. Enter AccountSummary for the page name.

  2. In the editor, replace any markup with the following.

    * <apex:page>

        <apex:pageBlock title="Account Summary">
          <apex:pageBlockSection>
        	
            
            
          </apex:pageBlockSection>
        </apex:pageBlock>
      </apex:page>

  3.  Click Preview to open a preview of your page that you can look at while you make changes. Make sure you can see the URL field for the preview window. You’ll come right back to this in a few steps.

  4.  In a separate browser window, go to the home page for your organization, and then select the Accounts tab. If the Accounts tab isn’t visible, switch to the Sales application by choosing Sales from the application menu in the upper-right corner.

  5. Ensure the View menu shows All Accounts, and click Go to view all of the account records.

  6. On the All Accounts page, click any account name.

  7. When the account details page finishes loading, look at the URL for the page. The URL will look something like this: https://SalesforceInstance/lightning/r/Account/001D000000JRBes/view.

    * The record’s identifier, its ID, is the series of letters and numbers. In this example, it’s “001D000000JRBes” (but in your organization it’ll be different). It’s unique across all records of all object types in your organization. 

  8. Select the record ID, and copy it to your clipboard. Before you leave the account detail page, take a look at the full page and the information displayed on it. 

    * This wasn’t a detour just to get a record ID. Before you’re done here, you’ll know how to build a page that displays the same information, yourself, in Visualforce code.

  9.  Switch back to the preview page you opened from the Developer Console. Click into the URL field of the browser window, and at the end of the URL enter &id= and then paste in the record ID you copied previously.The URL should be something like this: https://SalesforceInstance/apex/AccountSummary?core.apexpages.request.devconsole=1&id=001D000000JRBes

  10. Press Return to load the page at the new URL.

    * Although loading the preview page with the record ID in it doesn’t look any different yet, adding the ID means you can now ask the standard controller to help you out by loading that record and making it available on the page.

    * To preview your page in the context of Lightning Experience, return to your main browser window where you can see the account detail page. Open your browser’s JavaScript console and enter the following code. Don’t forget to replace pageName with your page’s name:

      - $A.get("e.force:navigateToURL").setParams(
        {"url": "/apex/pageName"}).fire();

    * You can also preview a page with a record ID this way, by adding the record ID parameter to the end of the URL in the JavaScript:

      - $A.get("e.force:navigateToURL").setParams(
        {"url": "/apex/pageName?&id=00141000004jkU0AAI"}).fire();

# Display Data from a Single Record - Add the standard controller for accounts to the page, and then reference account fields to display a record’s data.

  1. At the beginning of your page markup, inside the <apex:page> tag, add the following attribute.

    * standardController="Account"

      - When you save the page now, the preview page will reload as before, except this time the standard controller for accounts is active. When the page loads, the standard controller parses the parameters in the URL, finds the id parameter, and uses its value to retrieve a record and make it available to the page.

  2. In the body of the page, add the following markup.

    * Name: {! Account.name }

      - Now you can see that the record is being retrieved! You should see the name of the account that has the record ID that you added to the URL.

  3. Replace the single line with the account name with the following markup.

    * Name: {! Account.Name } <br/>
      Phone: {! Account.Phone } <br/>
      Industry: {! Account.Industry } <br/>
      Revenue: {! Account.AnnualRevenue } <br/>

    * <apex:page standardController="Account">
        <apex:pageBlock title="Account Summary">
            <apex:pageBlockSection>
            	
                Name: {! Account.Name } <br/>
                Phone: {! Account.Phone } <br/>
                Industry: {! Account.Industry } <br/>
                Revenue: {! Account.AnnualRevenue } <br/>
                
           </apex:pageBlockSection>
        </apex:pageBlock>  
      </apex:page>
    
      - When the page is loaded, and the <apex:page> component is activated, it activates a standard controller for the account object.

      - The standard controller sees that there’s an ID parameter in the URL, and searches for and retrieves the matching account record.

      - The standard controller takes the record and puts it in a variable that it makes available to the page. The variable has the same name as the standard controller’s sObject: Account. It’s an object variable, and contains all of the fields available on the Account sObject.

      - The four Visualforce expressions all reference the Account variable. They use “dot notation” to access individual fields within the Account variable. So, {! Account.Name } gets the name of the account, and so on.

      - The reason the number is displaying as a “raw” value in scientific notation is because the number is being directly output by an expression. 

      - To control the formatting of the value, you need to use a component, and give the component the value to handle. The component will take the raw value and format it appropriately, and then take care of outputting the result onto the page.

# Display Fields from Related Records

  1. For example, while viewing the object details for Account, you might have noticed that the Account object has a field called Account Owner, and that its type is Lookup(User). In other words, this field has a relationship to a User record. By clicking the Account Owner field label link, you’ll discover its Field Name is Owner.

  2. The Owner relationship represents a User. And, if you from Setup click Customize | Users | Fields, you’ll find that User has a Name field. Let’s use this information to display it.

    * In the body of the page, before the account name, add the following line.

      - Account owner: {! Account.Owner.Name } <br/>

    * The “dot notation” (Account.Owner.Name) indicates that you want to traverse the relationship between the records. You know that Account.Owner indicates the Owner field of the account record. 
    
    * The extra Name at the end indicates that the owner field isn’t a simple field representing a string, but a relationship to another record (it’s a Lookup(User)), and that you’d like to get the record represented by the value of the Owner field (it’s a User record), and display the Name field on that record.

  3. If you’ve created your own custom objects (instead of using objects like Account) and want to know how to reference a field, you have to follow a slightly different procedure. From Setup, enter Objects in the Quick Find box, then select Objects, select your object, and then the field.

    * The API Name now indicates the name of the field that you must use in your Visualforce pages. For example, if your field was called Foo, its API Name is Foo__c, and you’d reference it with that name—something like: {! myobject__c.foo__c}.

    