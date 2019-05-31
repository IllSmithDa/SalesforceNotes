# Visualforce Forms

  1. Ceeating and editing data is a fundamental aspect of any app. Visualforce provides everything you need to easily create pages that can create new records, or retrieve a record, edit its values, and save the changes back to the database. 

# Create a Basic Form

  1. Use <apex:form> and <apex:inputField> to create a page to edit data. Combine <apex:commandButton> with the save action built into the standard controller to create a new record, or save changes to an existing one.

  2. A page that lets someone edit and update a record needs to do all of the following.

    * Look up the record to edit and retrieve it from the database.

    * Put the relevant record data on the page in an editing form.

    * Receive a form submission with changed data.

    * Validate the new values.

    * Save valid changes back to the database.

    * Provide appropriate messages to the person submitting the changes, whether the new data is saved successfully or if there are errors.

# Form Example 

  1. Open the Developer Console and click File | New | Visualforce Page to create a new Visualforce page. Enter AccountEdit for the page name.

  2. In the editor, replace any markup with the following.

    * <apex:page standardController="Account">
        <h1>Edit Account</h1>
        <apex:form>
          <apex:inputField value="{! Account.Name }"/>
          <apex:commandButton action="{! save }" value="Save" />
        </apex:form>
      </apex:page>

  3. Click Preview to open a preview of your page that you can look at while you make changes. A new window should open, showing a form with a single empty field in the body.

  4. In the preview window, add the ID for an account to the URL, and press ENTER. The URL should be something like this: https://SalesforceInstance/apex/AccountEdit?core.apexpages.request.devconsole=1&id=001D000000JRBes 

    * The page uses the standard controller for accounts, defined in the <apex:page> component.

    * <apex:form> is a Visualforce component that packages everything inside it into something that can be sent back to the server as part of a page action. If you need to send data back to Salesforce, most of the time you’ll do it inside an <apex:form>.

    * <apex:inputField> creates an onscreen form field for the record data field that’s associated with it. You do this by providing an expression that references the relevant field in the value attribute. Here that expression is {! Account.Name }, which you should have no difficulty guessing is the account’s Name field.

    * Finally, <apex:commandButton> adds a button to the page’s user interface. This button fires an action when it’s clicked. In this case, the action is the save() action method in the standard controller. Like with <apex:inputField>, you connect the<apex:commandButton> with its action by referencing the action method to be called in an expression provided to the <apex:commandButton> action attribute.

# Add Field Labels and Platform Styling

  1. Place form elements within <apex:pageBlock> and <apex:pageBlockSection> tags to organize and group them, and to have the form adopt the platform visual style.

  2. Inside the <apex:form> component, wrap the two form elements in <apex:pageBlock> and <apex:pageBlockSection> tags, so that your markup looks like this.

  3. The <apex:inputField> component renders the appropriate input widget based on a standard or custom object field’s type. 

 
# Display Form Errors and Messages

  1. Use <apex:pageMessages> to display any form handling errors or messages.

    * Your page should provide useful feedback when things go wrong, such as when a required field is missing, or when a field value fails validation. The standard controller actually handles all of that for you. All you need to do is tell it where to put the messages on the page.

  2. As you can see, <apex:inputField> displays errors for its own field, but for a longer form it’s a nice touch to list all of the page’s errors in one place at the top of the page.

  3. The standard controller already collects all of the page’s messages when the form is processed. The <apex:pageMessages> component enables you to display those messages wherever you see fit.

# Edit Related Records

  1. So far our forms have only edited one record at a time. More specifically, because they use the standard controller for the account object, the form can only make changes to account records.

  2. That’s not always the most efficient workflow for users to use. While you can’t save changes to multiple object types in one request with the standard controller, you can make it easier to navigate to related records by offering links that perform actions such as edit or delete on those records.

  3. Below the existing closing </apex:pageBlock> tag, add the following markup.

    * <apex:pageBlock title="Contacts">
        <apex:pageBlockTable value="{!Account.contacts}" var="contact">
            <apex:column>
                <apex:outputLink
                    value="{! URLFOR($Action.Contact.Edit, contact.Id) }">
                    Edit
                </apex:outputLink>
                &nbsp;
                <apex:outputLink
                    value="{! URLFOR($Action.Contact.Delete, contact.Id) }">
                    Del
                </apex:outputLink>
            </apex:column>
            <apex:column value="{!contact.Name}"/>
            <apex:column value="{!contact.Title}"/>
            <apex:column value="{!contact.Phone}"/>
        </apex:pageBlockTable>
      </apex:pageBlock>

        - The <apex:pageBlockTable> component creates a table with a list of the account’s contacts. What’s new here is the column with the <apex:outputLink> components. 

        - These use an expression that references a global variable, $Action, and combines it with the contact’s ID inside the URLFOR() function.

        - The result is a link to the contact’s edit or delete page, depending on the action referenced. This can be a very useful shortcut for users of this form.

# More info 

  1. For starters, Visualforce offers a dozen or so input components, not just <apex:inputField>. <apex:inputField> works well with the standard controller and for directly editing record data. 
  
  2. For pages where you’re using your own custom controller code, or when form input doesn’t map directly to fields on a record, you’ll want to know about some of the others. 

  3.  Most of these components have names that begin with “apex:input”, and you can find them grouped together in the component reference. For select lists and radio button controls, look for the components with names that start with “apex:select” instead.

  4. For user interfaces intended to be used on mobile devices, you’ll want to check out <apex:input>, which is designed to be used in HTML5 pages, and allows you to use a variety of features that make the resulting input user elements mobile friendly.

  5. The code you wrote here made use of a number of actions provided by the standard controller for the page. We call these standard actions, and there are quite a few of them. There’s a core set that are available for all objects with standard controllers, but many of the built-in standard objects have additional actions you can use.

  6. Speaking of actions, you were able to add actions to edit and delete existing related contacts. How can you add the ability to create new related contacts? It’s not quite as easy as creating a link using the create action, the way you did with edit and delete.

    * This is because those actions worked on existing records, which already have a relationship to the associated account. But when you create a new record, you need to create that relationship yourself. That will require you to write some custom controller code of your own.