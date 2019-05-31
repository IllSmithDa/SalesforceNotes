# Lightning App 
  
  * An app is a collection of items that work together to serve a particular function. 

  * In Lightning Experience, Lightning apps give your users access to sets of objects, tabs, and other items all in one convenient bundle in the navigation bar.

  * Lightning apps let you brand your apps with a custom color and logo. You can even include a utility bar and Lightning page tabs in your Lightning app. 

  * To switch between apps, users can use the App Launcher. This makes it easy for users to switch contexts and still have access to the items, objects, and pages they need most.

  * Each Lightning app has a navigation bar at the top of the page, letting your users:

    - Find what they need using item names for easy recognition

    - Complete actions and access recent records and lists with a single click

    - Personalize the navigation bar to suit the unique way they work
  
    - Think of the navigation bar as a container for a set of items and functionality. It’s always there, but the items within it change based on the app you’re using.

  * What can you put in a Lightning App?

    - Most standard objects, including Home, the main Chatter feed, Groups, and People
    
    - Your org’s custom objects
    
    - Visualforce tabs
    
    - Lightning component tabs
    
    - Canvas apps via Visualforce tabs
    
    - Web tabs

    - You can even include Lightning page tabs and utilities like Lightning Voice.

# What Makes Lightning Experience So Special

  1. Efficient navigation and the ability to switch between custom-branded apps

  2. Quick access to productivity tools like Notes and Recent Items in the utility bar

  3. New record layouts that focus on what you can do instead of what you can view

  4. Turbocharged list views that let you easily filter and visualize your data

  5. Beautiful dashboards with components that span both columns and rows

  6. Sleek report views that you can filter quickly to see the data that's most important to you\

  7. Opportunity Workspace

    * Showcase key record details in the new highlights panel at the top of the page.

    * Use the handy composer to quickly log calls, create tasks, send emails, and more.

    * Get key coaching details with a customizable Path to support your sales process.

    * See a wealth of related information on hover using quick view, without ever leaving the opportunity page.

    * Add related records—like contacts—in context with minimal clicks.

    * View relevant, timely news about the account the opportunity’s associated with.

  8. Accounts and Contacts

    * Locate important data efficiently with the redesigned Lightning Experience page layout.

    * Get key coaching details on account records with a customizable Path to support your sales process.

    * Get the latest news for your customers with News.

    * Work smarter and keep your data clean with field-level duplicate matching.

    * Review past and upcoming activities at a glance.

  9. Reports and Dashboards

    * Create filters while viewing a report.

    * Make visually awesome dashboards with more than three columns.

    * Transition easily from Salesforce Classic to Lightning Experience with reports and dashboards that are automatically viewable in the new interface. And they inherit all permissions and sharing settings that were defined in Salesforce Classic.

# Lightning Experience App Manager

  1. Use the Lightning Experience App Manager to:

    * View all your Salesforce apps

    * Create Lightning apps or connected apps.

    * See which apps are visible in Lightning Experience.

    * Easily manage apps.
  
  2. A checkmark in the Visible in Lightning Experience column means that the app is accessible in Lightning Experience via the App Launcher and is fully functional.

  3. Classic apps that don’t have a check mark in the Visible in Lightning column are enabled only for our Salesforce Classic UI. 

  4. Classic apps marked as visible in Lightning Experience are fully usable in Lightning Experience, but they don’t take advantage of the app enhancements that Lightning Experience offers.

# Lightning App Tips

  1. Talk to your users. Ask them what their priorities are. Customizing tabs in apps gives you a unique opportunity to engage with your users.

  2. Ask users to post feedback to a Chatter group.

  3. Publish polls.

  4. Schedule lunch sessions. Everyone likes a free lunch, and nearly everybody is happy to express their opinion.

  5. Create a master list of objects that everyone in your org wants. Then trim down the list for each group—sales reps, sales managers, execs, and so on. 

  6. Put low-priority items at the bottom, or remove them altogether. 

# What do Compact Layouts do?

  1. Compact layouts control which fields your users see in the highlights panel at the top of a record. 

  2.  They also control the fields that appear in the expanded lookup card you see when you hover over a link in record details, and in the details section when you expand an activity in the activity timeline.

  3. Compact layouts help make your team more productive by presenting them with the key record information so they can easily manage their work. 

    * For example, show phone numbers and regions on an account. Or, show stages, amounts, and ownership fields on an opportunity. With compact layouts, you can highlight whatever your users need to see at a glance when they look at a record.
  
# Create a Compact Layout
  * When you create a custom object, it’s automatically assigned to a system default compact layout, which has only one field on it: the object name. Maria   wants to call attention to the most important fields on the object when her users view the audit records. Let’s make that happen by creating a custom compact   layout for the Energy Audit custom object.

    1. First, find and open the compact layouts node in Setup for Energy Audit.

      * From Setup, click Object Manager.

      * Click Energy Audit to open the object and then click Compact Layouts. 
      You can see that the System Default compact layout is assigned as the primary compact layout right now. We’re going to change that.

    2. Click New.

    3. Give the compact layout a label: Energy Audit Compact Layout.

    4. Add these fields to the compact layout, in this order:

      * Energy Audit Name

      * Account

      * Annual Energy Usage (kWh)

      * Average Annual Electric Cost

      * Type of Installation

    5. Click Save.

      * Now let’s set the compact layout that you created as the primary compact layout for the object. This step makes the compact layout the new default for the Energy Audit custom object.
    
    6. Click Compact Layout Assignment and then Edit Assignment.

    7. Select Energy Audit Compact Layout and click Save.

# Page Layouts

  1. You can customize and personalize many things on a given object record page using page layouts.

  2. There are two ways to customize a page in Lightning Experience. You can customize a page’s layout, or customize its contents. These are done with separate tools.
  
  3. You can customize a page’s contents, such as the fields and buttons that appear on the page, by using a different tool called the page layout editor.
    
    * The page layout editor, also known as page layouts, helps you manage the content of pages in both our Classic UI and in Lightning Experience.

  4. The Page Editor lets you 

    * Control which fields, lists of related records, and custom links users see

    * Customize the order that the fields appear in the page details

    * Determine whether fields are visible, read only, or required
    
    * Control which standard and custom buttons appear on records and related lists

    * Control which quick actions appear on the page

  5. The Related tab (1) contains related lists, which are lists of other records that are associated with the record you’re viewing. For example, an account can have related products, contacts, opportunities, and other custom records. Related lists make it easy to find and manage related information.

  6. The Details tab (2) shows information about a record. For example, a contact record detail page shows the name, address, owner, account, and other fields that are used to store information about the contact and other related records. To change the content of the fields on a related or detail page, you can click Edit (3).

  7. The page layout editor has two basic parts: a palette on the upper portion of the screen (1) and the record’s page layout on the lower portion of the screen (2). The palette contains the basic elements—such as fields, actions, buttons, links, and related lists—that you can add and arrange on your page. You can think of the upper part as the buffet table and the lower part as the plate of food you’re assembling.

# Custom Buttons and Links 
  
  1. Custom links can link to an external URL, such as www.google.com, a Visualforce page, or your company’s intranet. 
  
  2. Custom buttons can connect users to external applications, such as web pages, and launch custom links.

  3. In Lightning Experience, custom buttons and links live on your page layouts and appear in different areas of a Lightning page.

    * List button — Appears on a related list on an object record page.
    
    * Detail page link - Appears in the Links section of the record details on an object record page.

    * Detail page button - Appears in the action menu in the highlights panel of a record page.
  
  4. A custom list button is a button that you can add to a related list. When you create a list button for an object, you can add that button to that object’s related list when the related list appears on other objects.

# Quick Actions

  1. Actions let your users quickly do tasks, such as create records, log calls, send emails, and more. 

  2.  With custom actions, you can make your users’ navigation and workflow as smooth as possible by giving them quick access to information that’s most important.

# Quick actions come in two different flavors:

  1.  Object-specific actions 
    
    * have automatic relationships to other records and let users quickly create or update records, log calls, send emails, and more, in the context of a particular object. 

    * For example, you add an object-specific action on the Account object that creates contacts. If a user creates a contact with that action on the detail page for the Acme account, that new contact is associated with Acme. Object-specific actions live on the page layout for the object.
  
    * There are several types of object-specific actions.

      - Object-specific create actions create records that are automatically associated with related records.

      - Object-specific Update a Record actions make it easy for users to edit records. You can define the fields that are available for update.

      - Object-specific Log a Call actions let users enter notes about calls, meetings, or other interactions that are related to a specific record.

      - Object-specific custom actions invoke Lightning components, flows, Visualforce pages, or canvas apps that let users interact with or create records that have a relationship to an object record.

      - Object-specific Send Email actions, available only on cases, give users access to a simplified version of the Case Feed Email action in the Salesforce mobile app. 

  2. Global actions 
  
    * You create global actions in a different place in Setup than you create object-specific actions.

    * They’re called global actions because they can be put anywhere actions are supported. Use global actions to let users log call details, create or update records, or send email, all without leaving the page they’re on.
    
    * Global actions live on a special layout of their own, known as the global publisher layout.

      - It isn’t associated with an object, and it populates the global actions menu in Lightning Experience. 
      
      - Users can access the global actions menu by clicking Global Actions menu icon in the Salesforce header.

      - If an object page layout isn’t customized with actions, then the actions on those object record pages are inherited from the global publisher layout.

# How to create a New Action 

  1. In Setup, click Object Manager, then click Account.

  2. Click Buttons, Links, and Actions, then click New Action.

  3. Maria wants this action to create audit records, so select the Create a Record action type.
  
  4. Select Energy Audit as the target object. This is the type of record that the action creates.
  
  5. Call the action New Energy Audit. This is the text users see for the action.
  
  6. Click Save.

# Add an Object-Specific Action to a Page Layout

  1. Click Page Layouts.

  2. Click Account Layout.

    * There are two actions sections on a page layout. The Quick Actions in the Salesforce Classic Publisher section controls which actions appear on record pages in the Salesforce Classic UI. The 

  3. In the Salesforce Mobile and Lightning Experience Actions section, click wrench icon to override global publisher layout to override the defaults.

  4. Select Mobile & Lightning Actions in the palette and then drag the New Energy Audit action to the Salesforce Mobile and Lightning Experience Actions section.

  5. Click save

# Create a Global Action

  1. From Setup, click the Home tab.

  2. Enter Global Actions in the Quick Find box and click Global Actions.
  
  3. Click New Action.

  4. Select Create a Record for the action type

  5. Select Campaign for the target object.

  6. Enter 'New Campaign' or whatever campaign name you wish to assign as the label for the action.

  7. click save

# Add a Global Action to the Global Actions Menu

  1. In Setup, so click Publisher Layouts.

  2. Click Edit next to Global Layout.

  3. If the Salesforce Mobile and Lightning Experience Actions section isn’t customized, click the wrench icon override global publisher layout to override it.

  4. Click the Mobile & Lightning Actions category in the palette.

  5. Drag New Campaign from the palette into the Salesforce Mobile and Lightning Experience Actions section and save the layout.

  6. Refresh the browser, then click global actions menu icon to check out the global actions menu.