# Developer Console -  integrated development environment (more typically called an IDE) where you can create, debug, and test apps in your org. 
  1. Navigate, open, create and edit Apex classes and triggers, Aura component and Visualforce pages and components

  2. Browse packages that you’ve created or installed in your org.

  3. Generate logs for debugging and analyze them using different perspectives.

  4. Test your Apex code to ensure that it’s error free.

  5. Identify and resolve errors by setting checkpoints in your Apex code.

  6. Write and execute SOQL and SOSL queries to find, create, and update the records in your org.

  7. As of the Spring ‘19 release (API version 45.0), you can build Lightning components using two programming models: the Lightning Web Components model and the original Aura Components model. Lightning web components and Aura components can coexist and interoperate on a page. This content covers Aura components. You can’t develop Lightning web components in the Developer Console.

  8. The Developer Console is connected to one org and is browser-based.

    * If you want your changes to be effective immediately and you don’t want to install anything on your computer, we recommend the Developer Console.

    * If you want to connect to multiple orgs, compare or synchronize files, or use version control, Force.com IDE is your best option.

    * The Developer Console doesn’t have version control or conflict resolution. To avoid overwriting other people’s code, be careful when you use the Developer Console in orgs that you share with your teammates. 

# Accessing the Developer Console

  1. The first thing you learn as a commander is how to access your console. After logging in to your org, click Developer Console under the quick access menu (Quick Access Menu) or your name.

# What Is a Workspace?

  1. After you’ve opened the Developer Console, the next step is to decide how to set up your workspace.

  2. Similarly, workspaces in the Developer Console help you organize information to show just what you need as you work on each of your development tasks. 

  3.  Although it sounds like a fancy term, a workspace is simply a collection of resources, represented by tabs, in the main panel of the Developer Console. You can create a workspace for any group of resources that you use together.

  4. If you’re working on two different projects, you can have the related code, tests, and logs open simultaneously in separate workspaces.

    * For instance, say you’re writing code to update some records for your engineering team, but you also want to check the system details for your navigation team

    * You can create two workspaces, each of which contains only the resources relevant to the project. Workspaces reduce clutter and make it easier to navigate between different resources.

# Set Up Your Own Workspace

  1. Select Workspace | New Workspace and give your workspace a name. In your new workspace, you can create Apex classes, Aura components, Visualforce pages, and more.

  2. You can switch between your workspaces by selecting Workspace | Workspace Manager Workspace | Switch Workspace (1). In this way, you can work with code and analyze logs for each project just by opening a different workspace.

# Navigate and Edit Source Code 

  1. Create and Execute Apex Code

  2. Apex is a Salesforce programming language that you can use to customize business processes in your org. 

# Create Aura Components

  1. What Are Lightning Components?

    * Lightning Components is a framework for developing mobile and desktop apps. You can use it to create responsive user interfaces for Lightning Platform apps. Lightning components also make it easier to build apps that work well across mobile and desktop devices.

  2. You can use the Developer Console to create Aura components. Using the Developer Console, you can create a component bundle. A component bundle acts like a folder in that it contains components and all other related resources, such as style sheets, controllers, and design.

# Create an Aura Component

  1. Select File | New | Lightning Component. The window that pops up prompts you for a name and description.

  2. Name your component meetGreet and click Submit. 

    * The window also has options to configure your app’s tab, page, record page, and communities page. You can ignore these options. For now, we’re only focusing on writing basic Aura component code.

  3. Two tabs are created. Click the one labeled meetGreet.cmp. This file contains the opening and closing tags for Aura components.

  4. Between the opening and closing <aura:component> and </aura:component> tags, copy and paste this line.

    * <p>Greetings, fellow humans! What’s your status?</p>

  5. To save the component, select File | Save.

# Here’s how you can open a saved Aura component or any of these resources.

  1. Select File | Open Lightning Resources.

  2. Type your component’s name in the search box to find your bundle, or select its folder from the list. 

  3. To see the bundle’s resources, click the arrow next to the folder.

  4. Select the resource you want to work on, and then click Open Selected.

  