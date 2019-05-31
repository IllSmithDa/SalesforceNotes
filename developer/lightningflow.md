# Automation 

  1. If a customer is interacting with a company, they expact a seamless, personalized experience.

    * e.g customer experience dealing with a lost credit card 

  2. Providing a seamless, automated customer experience has historically been challenging, time-consuming, and code-heavy. Depending on the precise nature of your business processes, you may have had to:

    * Integrate various systems.

    * Configure process logic.

    * Design and build an end-user experience.

    * Make the experience available from anywhere: desktop or mobile devices, internal apps, or external portals.

  3. A flow interview is a running instance of a flow. When you distribute a flow, users interact with individual interviews of that flow.
  
  4. You can also build autolaunched flows, which run in the background like a process. The main difference is that autolaunched flows can’t have screens, which require user interaction. Because they have no screens, you can call autolaunched flows from backend things like processes and Apex classes.


# Lightning Flow 

  1. Lightning Flow provides declarative process automation for every Salesforce app, experience, and portal. 

  2. Included in Lightning Flow are two point-and-click automation tools: Process Builder, which lets you build processes, and Flow Builder, which lets you build flows. 

    * Lightning Flow is the name of the product.
   
    * Process Builder and Flow Builder are the names of the tools.

    * Use Process Builder to make processes; use Flow Builder to make flow

# Lightning Flow makes it easy for you to do the following. 

  1. Create a guided tutorial or wizard with screens. 

    * Flow Builder includes several out-of-the-box screen components, like text boxes, radio buttons, and file-uploads. If you need more than what’s offered, add custom Aura components to your screens.

  2. Set up automated tasks and processes.

    * Declaratively configure logic and actions for your business process with either Process Builder or Flow Builder. If needed, you can build custom Apex code to fill any functional gaps. 

  3. Connect to external systems.

    * Communicate changes between your Salesforce org and your external systems with platform events.

    * Process Builder and Flow Builder let you respond to and send platform event messages. In addition, Flow Builder can retrieve data from third-party systems with External Services.

  4. Add automation to your pages and apps.

    * Make sure your behind-the-scenes processes start when the right action happens, whether that’s when records change or when users click a particular button. 

    * Once you build guided visual experiences, add them to Lightning pages, Community pages, the utility bar in your Lightning apps, and more. 

  5. Reuse what you build.

    * In Flow Builder, any flow can be used as a subflow. 

    * In Process Builder, create an invocable process to reuse that process’s logic or actions in other business processes.

# Which Automation Tool Is Right for My Use Case? 

  1. Guided visual experience

    * experience 	Business processes that need input from users, whether they’re employees or customers

  2. Behind-the-scenes automation

    * Business processes that get all the necessary data from your Salesforce org or a connected system. In other words, user input isn’t needed.

  3. Approval automation 

    * Business processes that determine how a record, like a time-off request, gets approved by the right stakeholders. 

# From Processes to Flows to Apex

  1.  Use Process Builder when you need to start a behind-the-scenes business process automatically. Processes can start when

    * A record is created

    * A record is updated

    * A platform event occurs

  2. Use Flow Builder to:

    * Automate a guided visual experience.

    * Add more functionality for a behind-the-scenes process than is available in Process Builder. Use Flow Builder to build the more complex functionality. Then call the resulting flow from the process.

    * Start a behind-the-scenes business process when a user clicks something, like a button.

      - For example, when an opportunity is won, your company wants a renewal opportunity to be created automatically. As you see later in this module, you can build parts of that use case as a process, but the rest has to be built in a flow.

  3. Apex 

    * Use Apex when you need more functionality than is available in Process Builder or Flow Builder. Build the more complex functionality as invocable Apex methods. Then call the resulting Apex as an Apex action in the process or as an Apex action element in the flow.

# Flow variables comes in 4 types

  1. Variable - A single value 

    * "Hello World", true, 6

  2. Collection Variable - Multiple values of the same data type

    *  [1, 2, 3, 5, 8, 13]

  3. Record Variable - A set of field values for a single record

    *	Rating, ID, and Name for an account

  4. Record Collection Variable - Variable 	A set of field values for multiple records of the same object type

    * Rating, ID, and Name for multiple accounts

# Working with a data collection ( for loops )

  1. The only way to update items in a collection is to iterate over the collection with a loop.

  2. A loop tells the flow to process each item in the collection one at a time, executing the same logic on each item until the entire collection has been processed.

  3. Each time the loop iterates, the loop variable represents an item in the collection. When a loop starts, the first item in the collection variable is copied into the loop variable. After the iteration is over, the loop variable is overwritten with the next item’s values. And so on, until there are no items left in the collection.

  4. To update an item’s field values inside a loop, update the loop variable. Then, before the iteration for that item finishes, add the loop variable as an item in another collection variable. If you don’t do that, the changes are overwritten when the next item is loaded into the loop variable.

  5. Avoid adding actions, like creating or updating records, inside a loop. That’s a surefire way to hit limits.

# Sample Scenarios 

  1. Guide a community member through requesting a new credit card with a step-by-step wizard. - Flow Builder

  2. A sales rep clicks a button on an opportunity, which launches a discount calculator. - Flow Builder 

  3. When an account is updated, update all of the contacts related to that account. - Process Builder

  4. When an opportunity stage is updated, also update a custom checkbox field. - Process Builder

  5. Create a task when a platform event occurs. - Process Builder

  6. Update a lead record in Salesforce after a certain amount of time passes, or when a specified time is reached. - Process Builder

  7. When an opportunity closes, automatically create a renewal opportunity. - Process Builder and Flow Builder

  8. Route an employee’s time-off request to a manager for approval. - Approvals 

    * Approvals isn’t included in Lightning Flow, but it offers a declarative way to automate something that Lightning Flow doesn’t cover. That said, Lightning Flow does support automating how a record gets submitted for approval.

# Add a Screen to Collect User Input

  1. From the toolbox, drag a Screen element onto the canvas

  2. Name it New Account in the Label field

  3. In Screen Components, click Text and then click Text again

  4. Select the first Text screen component and enter Account Name in the Label field

  5. Select the second Text screen component and enter Phone Number in the Label field

  6. Select the footer and on the right and under Control Navigation, deselect Previous and Pause

  7. Click Done

# Add a Create Records Element to Create Records

  1. From the Toolbox, drag a Create Records element onto the canvas. Name it Create Account

  2. For How to Set the Record Fields, select Use separate variables, resources, and literal values

  3. In Create a Record of This Object, in Object, select Account

  4. In Field, select Name

  5. In Value, select SCREEN COMPONENTS | Account_Name

  6. Click Add Field

  7. In Field, select Phone

  8. In Value, select SCREEN COMPONENTS | Phone_Number

  9. In Store Account ID in Variable, select New Resource from the Variable dropdown. The New Resource window appears.

    * In Resource Type, select Variable

    * Name the API Account_Id

    * In Data Type, select Text

    * Click Done

  10. In Store Account ID in Variable, select VARIABLES | Account_Id from the Variable dropdown.
  Make sure that your Create Records element looks like this

  11. Click Done

# Create the Screen That Enables File Uploads

  1. Drag another Screen element onto the canvas

  2. In Screen Properties, configure these settings

    * Name the screen Upload Files in the Label field

    * Under Control Navigation, deselect Previous and Pause. 

        - If you don't make that selection users will be able to navigate back to the first screen, and multiple accounts could accidentally be created
  
  3. On the left in Screen Components, click File Upload

    * For API Name, enter accountFiles

    * For File Upload Label, enter Upload Related Files

    * For Related Record ID, select VARIABLES | Account_Id

    * For Allow Multiple Files, select $GlobalConstant.True

  4. Click Done

# Connect the Elements to Finish the Flow 

  1. Click the node at the bottom of Start and drag it to New Account

  2. Click the node at the bottom of New Account and drag it to Create Account

  3. Click the node at the bottom of Create Account and drag it to Upload Files.

  4. Save the flow, name it Quick Account in Flow Label, and set the type to Screen Flow

  5. Click Save

    * Skip the warning you see about Lightning runtime. We talk about that next

  
# Salesforce offers two runtime experiences that determine the look and feel when someone runs a flow. To make your flows blend in with Lightning Experience, make sure that Lightning runtime is enabled in your org.

  1. From Setup, enter Automation in the Quick Find box, and then select Process Automation Settings.

  2. Verify that Enable Lightning runtime for flows is selected. 

  3. Save your changes. 

# Activate Your Flow

  1. From Setup, enter Flows in the Quick Find box, then select Flows.

  2. Click Quick Account.

  3. Find the appropriate version of the flow, and select Activate in the Action column.

# Add Your Flow to the Home Page

  1. Create a home page. 

    * From Setup, enter Builder in the Quick Find checkbox, and then select Lightning App Builder.

    * Click New.

    * Select Home Page and click Next

    * Give the page a name and click Next.

    * Click CLONE SALESFORCE DEFAULT PAGE, select Home Page Default, and click Finish.

  2. Drag a Flow component to the top of the right column.  

  3. For Flow, select Quick Account

  4. Save your changes and activate the page. Mark this page as the default home page and click Save.

  5. To see your flow in action, go to your Home page. 

    * Click Back to return to Setup.

    * Click App Launcher icon, and under All Items, click Home.


