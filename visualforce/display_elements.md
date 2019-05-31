# Display Records, Fields, and Tables 

  1. Visualforce includes nearly 150 built-in components that you can use on your pages. Components are rendered into HTML, CSS, and JavaScript when a page is requested. 

  2. Coarse-grained components provide a significant amount of functionality in a single component, and might add a lot of information and user interface to the page it’s used on. 

  3.  Fine-grained components provide more focused functionality, and enable you to design the page to look and behave the way you want.

  4. Here we’ll focus on output components, that is, components that output data from a record and enable you to design a view-only user interface. 

# Display Record Details

  1. Use <apex:detail> to quickly add record details to a page that uses a standard controller.

  2. Some output components bring a lot to the party. These “coarse grained” components offer a lot of functionality, displaying many fields, labels, and other user interface elements.

  3. They let you quickly build pages that are variations on the built-in Salesforce user interface.

# Display Record Example

  1. Replace the line with {! Account.Name } with the following markup, and save your changes.

    * <apex:detail />

      - <apex:detail> is a coarse-grained output component that adds many fields, sections, buttons, and other user interface elements to the page in just one line of markup.

      - Notice also that everything it adds to the page uses the Salesforce Classic styling. There are quite a few attributes for customizing the appearance of <apex:detail>

      -  Spend a few minutes now and try changing a few to see what they do. To create pages that are more aligned with the styling of Lightning Experience, see Understand Important Visual Design Considerations in the Visualforce & Lightning Experience module.

# Display Related Lists

  1. Use <apex:relatedList> to display lists of records related to the current record.

  2. The <apex:detail> component displays the details of a particular record, as well as lists of related records, such as contacts, cases, opportunities, and so on. This might be too much, so you can remove those related lists, and then add back just a few, using a different coarse-grained component.

  3. Revise the markup to omit related lists by adding relatedList="false" to the <apex:detail> component.

    * <apex:detail relatedList="false"/>

      - The account record’s details are still displayed, but the related lists are gone.

    * elow the <apex:detail/> line, add the following markup.

      - <apex:relatedList list="Contacts"/>
        <apex:relatedList list="Opportunities" pageSize="5"/>
      
      - Your page should now display two related lists, for contacts and opportunities. Also notice that you can configure each related list independently, by changing attributes on just that component.

  4. The <apex:relatedList> component is another coarse-grained component, but it’s lower level than <apex:detail>. That is, <apex:detail> shows many related lists at once (or none), while <apex:relatedList> lets you go one by one. This lets you show only the related lists that you’re interested in, and you can customize the display of each related list individually.

# Display Individual Fields

  1. When you need even more control over your page layout, you can add fields individually. The <apex:outputField> component is designed for doing exactly that.

  2. Replace the <apex:detail/> line with the following markup.

    * <apex:outputField value="{! Account.Name }"/>
      <apex:outputField value="{! Account.Phone }"/>
      <apex:outputField value="{! Account.Industry }"/>
      <apex:outputField value="{! Account.AnnualRevenue }"/>

    * The four fields are added to the page. But the formatting perhaps isn’t what you expected. The field values are displayed all on one line, without labels, and without other formatting. 
    
    * That’s not what we want, and it’s quite a contrast to the <apex:detail> and <apex:relatedList> components, which automatically use the platform styling.

    * By itself, the <apex:outputField> only outputs the field’s value. But when you wrap it in <apex:pageBlock> and <apex:pageBlockSection> components, its behavior changes quite a bit.

  3. Wrap the <apex:outputField> lines with <apex:pageBlock> and <apex:pageBlockSection> components, so that your markup looks like this.

  4. Although <apex:outputField> seems like a fine-grained component because it only outputs one field, it’s actually doing quite a lot. It knows if it’s being used inside certain other components, and changes its output and styling appropriately.

  5. It’s also smart about formatting and display. Notice that the Annual Revenue field is formatted as currency. <apex:outputField> automatically adapts to the data type of the field being displayed. Try adding a date, checklist, or picklist field to the page, and see what happens.

# Display A Table

  1. What exactly is a related list? What does <apex:relatedList> do when you add it to a page?

    * It grabs a list of similar data elements. For example, a list of contacts for the account.

    * It sets up a table with columns for each field, headers atop each column, and so on.

    * For each item in the list—for each related contact—it adds a row to the table, and fills in each column with the appropriate field from that record.

  2. You can do the same thing in your own Visualforce markup using iteration components. An iteration component works with a collection of similar items, instead of on a single value.

    * For example, {!Account.contacts} is an expression that evaluates to a list of contacts for an account. 
    
    * You can use this expression with an iteration component to create a list or table with details of these related contacts.
    
  3. Replace the two <apex:relatedList/> lines with the following markup.

    * <apex:pageBlock title="Contacts">
        <apex:pageBlockTable value="{!Account.contacts}"      var="contact">
           <apex:column value="{!contact.Name}"/>
           <apex:column value="{!contact.Title}"/>
           <apex:column value="{!contact.Phone}"/>
        </apex:pageBlockTable>
      </apex:pageBlock>
  
  4. <apex:pageBlockTable> is an iteration component that generates a table of data, complete with platform styling. Here’s what’s going on in your markup.

    * The value attribute of <apex:pageBlockTable> is set to the expression mentioned previously, {!Account.contacts}. This is the list of records that <apex:pageBlockTable> will work with.

    * For each record in that list, one record at a time, <apex:pageBlockTable> assigns that record to the variable named in the <apex:pageBlockTable>’s var attribute. In this case, that variable is named contact.

    * For each record, <apex:pageBlockTable> constructs a new row in the table, using the row defined by the set of <apex:column>components within the body of <apex:pageBlockTable>.
      
      - The <apex:column> components, in turn, use the contact variable that represents the current record to pull out the field values for that record.

    * Outside of the loop, <apex:pageBlockTable> uses the fields in the <apex:column> components to create column headers, by looking up the label for each field.
  
    * That’s a lot to take in, and iteration components are tricky to understand the first time. The best thing you can do right now is to try creating your own. Add a list of opportunity related records to the page using <apex:pageBlockTable>. 
    
    * Choose the fields you want displayed in the table. Look up the different attributes for <apex:pageBlockTable> and <apex:column>, and experiment until you feel comfortable.

    * You may have noticed that your manually created related lists are missing some things that were added to the table created by <apex:relatedList>. 

      - For example, the Edit and Del links to edit and delete individual records is missing, and so is the New Contact button. To create these user interface elements you need to know a little more Visualforce, specifically about forms and actions. You’ll learn about that elsewhere.

      