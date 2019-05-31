# What is Visual Force?

  1. Visualforce is a web development framework that enables developers to build sophisticated, custom user interfaces for mobile and desktop apps that can be hosted on the Lightning Platform

  2. You can use Visualforce to build apps that align with the styling of Lightning Experience, as well as your own completely custom interface.

  3. You can build functionality for your own organization, or create apps for sale in the AppExchange.

  4. Visualforce app development is familiar to anyone who has built web apps. Developers create Visualforce pages by composing components, HTML, and optional styling elements. Visualforce can integrate with any standard web technology or JavaScript framework to allow for a more animated and rich user interface.

  5.  Each page is accessible by a unique URL. When someone accesses a page the server performs any data processing required by the page, renders the page into HTML, and returns the results to the browser for display.

# Here’s a short example of a working Visualforce page. 

  1. <apex:page standardController="Contact" >
         <apex:form >
             
             <apex:pageBlock title="Edit Contact">
                 <apex:pageBlockSection columns="1">
                     <apex:inputField value="{!Contact.FirstName}"/>
                     <apex:inputField value="{!Contact.LastName}"/>
                     <apex:inputField value="{!Contact.Email}"/>
                     <apex:inputField value="{!Contact.Birthdate}"/>
                 </apex:pageBlockSection>
                 <apex:pageBlockButtons >
                     <apex:commandButton action="{!save}" value="Save"/>
                 </apex:pageBlockButtons>
             </apex:pageBlock>
             
         </apex:form>
     </apex:page>
  
  2. In just over a dozen lines of markup, this page does a lot.

    * It connects to the Visualforce standard controller, a part of the Visualforce framework that provides automatic data access and modification, standard actions, and more.

    * When accessed without a record ID, the page displays a blank data entry form. When you click Save, a new record is created from the form data.

    * When accessed with a record ID, the page looks up the data for that contact record and displays it in an editable form. When you click Save, your changes for the contact are saved back to the database.

    * Each input field is smart about how it presents its value.

      - The email field knows what a valid email address looks like, and displays an error if an invalid email is entered.

      - The date field displays a date widget when you click into the field to make entering a date easier.

    * The Save button calls the save action method, one of a number of standard actions provided by the standard controller.

# Open a Visualforce Page from the App Launcher

  1. Your Visualforce apps and custom tabs are all available from the App Launcher, which you reach by clicking App Launcher icon in the header. 

  2. Click a custom app (1) to activate it. Items in the app display in the navigation bar, including any Visualforce tabs you’ve added to the app. Note that you need to add your Visualforce pages to tabs for them to be accessible in the App Launcher. Visualforce tabs that aren’t in apps can be found in All Items (2).

# Add a Visualforce Page to the Navigation Bar

  1. As described in the preceding example, you can add Visualforce tabs to an app and they display as items in the app’s navigation bar. 

# Display a Visualforce Page within a Standard Page Layout

  1. Extend your page layouts by embedding Visualforce pages on them to display completely custom content on a standard page. The behavior here is identical to Salesforce Classic, except you need to view the record’s Details to see the page layout.

# Add a Visualforce Page as a Component in the Lightning App Builder

  1. When you create a custom app page in the Lightning App Builder, you can add a Visualforce page to the page by using the Visualforce component. 

# Launch a Visualforce Page as a Quick Action

  1. Although their placement in the Lightning Experience user interface is quite different from Salesforce Classic, the process of adding quick actions is much the same. Add them to the appropriate publisher area on the object’s page layout.

# Display a Visualforce Page by Overriding Standard Buttons or Links

  1. You can override the actions available on an object with a Visualforce page. When the user clicks a button or link that has been overridden, your page displays instead of the standard page. Setting this up is pretty much identical to Salesforce Classic. 

# Display a Visualforce Page Using Custom Buttons or Links

  1. You can create new actions for your objects, in the form of buttons and links, by defining them on an object. JavaScript buttons and links aren’t supported in Lightning Experience, but Visualforce (and URL) items are. 

  2. The process of defining Visualforce buttons and links is identical to that in Salesforce Classic, so we won’t bother to show it here

# Creating and Editing Visualforce pages 

  1. Visualforce pages are basic building blocks for application developers. A Visualforce page is similar to a standard Web page, but includes powerful features to access, display, and update your organization’s data.

  2. Pages can be referenced and invoked via a unique URL, just as they would be on a traditional web server.

  3. Visualforce uses a tag-based markup language that’s similar to HTML. Each Visualforce tag corresponds to a coarse or fine-grained user interface component, such as a section of a page, a list view, or an individual field. Visualforce boasts nearly 150 built-in components, and provides a way for developers to create their own components. 

  4. You can view, create, and edit Visualforce pages several different ways in Salesforce. Visualforce pages can also be created and modified using Salesforce APIs, enabling a variety of external tools.

# Create Visualforce page 

  1. Open the Developer Console under Your Name or the quick access menu (Setup gear icon). The Developer Console opens in a new window.

  2. Click File | New | Visualforce Page.

  3. Enter HelloWorld for the name of the new page, and click OK.   A new, blank Visualforce page opens in the Developer Console.

  4. In the editor, enter the following markup for the page.

    * <apex:page> 
        <h1>Hello World</h1> 
      </apex:page>

  5. Click File | Save.
  
  6. To see your new page, click Preview. The rendered page opens in a new window. Note that this page preview shows your page without Salesforce styling. To see your page in the context of Lightnin. Experience, return to your main browser window. Open your browser’s JavaScript console and enter the following code. Don’t forget to replace pageName with your page’s name:

    * $A.get("e.force:navigateToURL").setParams(
      {"url": "/apex/pageName"}).fire();

      - This JavaScript fires the Lightning Experience navigateToURL event, and is the equivalent of entering in the classic /apex/PageName URL—you can even see that URL pattern in the code. 

      - Click File | Open to see a list of existing Visualforce pages. Double-click a page to open it. You can also open other Salesforce entities, such as Apex classes and triggers, Visualforce components, and so on.

# Add Attributes Using Auto-Suggest

  1. In your HelloWorld page, click inside the opening <apex:page> tag, right before the closing “>”. Type a space and then “s”.
     Auto-suggest presents a list of possible completions for what you type. As you type additional characters, the list of suggestions is reduced to only   matching values.

  2. Press the down arrow key until “sidebar” is selected. Press Return. The sidebar attribute is added to the <apex:page> tag in your markup, and auto-suggest presents possible values for it.

  3. Use the arrow keys or type “f” to select false, and press Return. Your code should look like this.

    * <apex:page sidebar="false"> 
        <h1>Hello World</h1> 
      </apex:page>

  4. Save your changes.

  5. Repeat the above steps to add showHeader="false" to the <apex:page> tag, and save your changes.

    * <apex:page sidebar="false" showHeader="false"> 
        <h1>Hello World</h1> 
      </apex:page>
    
      - Note that both the sidebar and showHeader attribute have no effect in Lightning Experience, and that there’s no way to suppress the Lightning Experience header. Although the default value of showHeader is true, it has no effect in Lightning Experience.

      - The page still includes some Salesforce style sheets, which let you match Salesforce choices for fonts, size, and so on. To suppress all Salesforce output, add standardStylesheets="false" to remove the styles as well.

# Add and Compose Components to Form a Page Structure - Add components to your Visualforce page and arrange them to build the page’s structure.

  1. In your HelloWorld page, add a <apex:pageBlock> component below the text “Hello World”. <apex:pageBlock> is a structured user interface element that groups related items on a page. Use auto-suggest to add it, and set the title attribute to “A Block Title”.

  2. Add a <apex:pageBlockSection> component inside the <apex:pageBlock> component. Set the title attribute to “A Section Title”. <apex:pageBlockSection> is another component that adds structure and hierarchy to a page. When rendered, <apex:pageBlockSection> elements can be collapsed by the user to hide all but the section title.

  3. Add some text inside <apex:pageBlockSection> component, such as “I’m three components deep!”.

    * <apex:page> 
       <h1>Hello World</h1> 

        <apex:pageBlock title="A Block Title">
          <apex:pageBlockSection title="A Section Title">
               I'm three components deep!
          </apex:pageBlockSection>
        </apex:pageBlock>
      </apex:page>

  5. Add another <apex:pageBlockSection> after the first, and set the title to “A New Section.” Add some text to the body of the component, like you did with the first <apex:pageBlockSection>. Your code should look like this.

    * <apex:page> 
        <h1>Hello World</h1> 
        <apex:pageBlock title="A Block Title">
          <apex:pageBlockSection title="A Section Title">
              I'm three components deep!
          </apex:pageBlockSection>
          
          <apex:pageBlockSection title="A New Section">
              This is another section.
          </apex:pageBlockSection>
        </apex:pageBlock>
      </apex:page>
    
      - Notice how the <apex:pageBlockSection> tags are nested within the <apex:pageBlock> tag. You can’t use a child <apex:pageBlockSection> tag without putting it inside a parent <apex:pageBlock> tag.

# Other ways to edit and create Visualforce pages

  1. The development mode “quick fix” and footer is a fast way to quickly create a new page, or make short edits to an existing page. It’s great for quick changes or when you want to create a short page to test out some new code on a blank slate, before incorporating it into your app pages.

  2. The Setup editor, available in Setup by entering Visualforce Pages in the Quick Find box, then selecting Visualforce Pages, is the most basic editor, but it provides access to page settings that aren’t available in the Developer Console or development mode footer.

  3. There are also a number of external tools available, such as the Lightning Platform IDE plug-in for Eclipse and MavensMate for SublimeText, which can connect to your Salesforce organization and be used for Visualforce development.
  
  4. The <apex:pageBlock> and <apex:pageBlockSection> components you added to your page render a user interface that matches that of Salesforce Classic interface elements. There are other components that also let you match the platform visual style, including <apex:pageBlockSectionItem> and <apex:pageBlockButtons>. 

  