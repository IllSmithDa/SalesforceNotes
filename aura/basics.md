# Aura Component 

  1. The Lightning Component framework is a UI framework for developing web apps for mobile and desktop devices. It’s a modern framework for building single-page applications with dynamic, responsive user interfaces for Lightning Platform apps.

    * To achieve these interactive user experiences, modern web apps are built as a tightly bound collection of code that loads from a single URL, and then runs continuously as you use it.

    * These single-page apps are built much like native apps are, with the plumbing being handled by a framework. A framework like the Lightning Component framework.

  2. It uses JavaScript on the client side and Apex on the server side.

  3. Lightning components were born out of and used to build the Salesforce platform for mobile apps. Mobile is baked into the core of the Lightning Component framework, and it makes developing apps that work on both mobile and desktop devices far simpler than many other frameworks.

# An Example Aura Component

  1. <aura:component>
         <aura:attribute name="expense" type="Expense__c"/>
         <aura:registerEvent name="updateExpense" type="c:expensesItemUpdate"/>
         <!-- Color the item green if the expense is reimbursed -->
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

    *  First of all, it’s XML markup, and mixes both static HTML tags with custom Aura component tags, such as the <aura:component> tag that leads off the sample.

    * <lightning:card> creates a container around a group of information.
    
    * <lightning:formattedDateTime> displays formatted date and time.
    
    * <lightning:relativeDateTime> displays the relative time difference between the current time and the provided time.

    * The lightning namespace provides many UI components that use Salesforce Lightning Design System, or SLDS, out-of-the-box.

    *  We recommend that you use components in the lightning namespace where possible

      -  For example, use <lightning:input> instead of <ui:inputText>, <ui:inputNumber>, and so on. Most of the input types, like text, number, email, and many more are available to you. 

  2. Client Side Controller function 

    * ({
          clickReimbursed: function(component, event, helper) {
              var expense = component.get("v.expense");
              var updateEvent = component.getEvent("updateExpense");
              updateEvent.setParams({ "expense": expense });
              updateEvent.fire();
          }
      })

      - This is the component’s client-side controller, written in JavaScript.

      - The clickReimbursed function in the component’s controller corresponds to the onchange="{!c.clickReimbursed}" attribute on the checkbox in the component’s markup.

  3. Visualforce was created before mobile apps on phones became a thing. While you can develop mobile apps with Visualforce, none of the built-in components are mobile-savvy. 

    * Which means you write more code. Lightning Components, on the other hand, is specifically optimized to perform well on mobile devices.

# Other ways to build 

  1. “How does the Lightning Component framework compare to MyFavoriteFramework?” where that favorite framework is another modern JavaScript web app framework such as AngularJS, React, or Ember.

    * You might be surprised to learn that we think these frameworks are a great way to build Lightning Platform apps!

    * We recommend using them with Visualforce, using what we call a container page, and packaging your chosen framework and app code into static resources. Using an empty container page has Visualforce get out of your way, and lets you use the full capabilities of your chosen framework.

  2. While it’s possible to use third-party JavaScript frameworks with Lightning components, it’s a bit cumbersome. The Lightning Component framework doesn’t have the notion of an empty page, and has some specific opinions about how, for example, data access is performed, and some rather specific security requirements.

    * And frankly, the features of the Lightning Component framework and most modern frameworks overlap quite a bit. While the style or specifics might be different, the features provided are conceptually similar enough that you’re effectively running duplicate code. That’s neither efficient nor easy to work with.

    * Another thing to consider: general-purpose frameworks such as AngularJS are designed to be agnostic about the platform they run on top of, in particular data services. The Lightning Component framework, on the other hand, is designed to connect natively with services provided by Salesforce and the Lightning Platform. 

# Where You Can Use Lightning Components

  1. Add Apps to the Lightning Experience App Launcher

  2. Add Apps to Lightning Experience and Salesforce App Navigation

  3. Create Drag-and-Drop Components for Lightning App Builder and Community Builder

  4. Add Lightning Components to Lightning Pages

  5. Add Lightning Components to Lightning Experience Record Pages

  6. Launch a Lightning Component as a Quick Action

  7. Override Standard Actions with Lightning Components

  8. Create Stand-Alone Apps

  9. Run Lightning Components Apps Inside Visualforce Pages

  10. Run Lightning Components Apps on Other Platforms with Lightning Out

  11. Customize Flow Screens

# Create Basic Component

  1. So, let’s write something. Select File | New | Lightning Component to create an Aura component. 
  
    * In the New Lightning Bundle panel, enter helloWorld for the component name, and click Submit.

  2. This creates a new helloWorld component bundle, with two open tabs. Close the helloWorld tab, and keep the helloWorld.cmp tab open.

  3. helloWorld.cmp contains the opening and closing tags for an Aura component, <aura:component>. Between them, add the following markup, and save:

    * <p>Hello Lightning!</p>

  4.  You can’t run your component directly and see how it behaves. Instead, your component needs to run inside a container app, which we’ll call a container for short.

  5. Select File | New | Lightning Application to create a new Lightning app. In the New Lightning Bundle panel, enter “harnessApp” for the app name, and click Submit.

    * This creates a new harnessApp bundle, with two open tabs. Close the harnessApp tab, and keep the harnessApp.app tab open.

  6. harnessApp.app contains the opening and closing tags for a Lightning app, <aura:application>. Between them, add the following markup, and save:

    * <c:helloWorld/>

      - This adds the helloWorld component we created earlier to the harnessApp app.

  7.  Apps have a preview button, components don’t. Click it now, and another browser window should open and show you your app.

# Notes on Developer Console

  1. You have surely noticed the extra controls that appear in a palette on the right side of the editing window of any Lightning bundle

    *  Each of the different buttons with a Create label represents a different resource you can add to the bundle.

    * There’s also File | Open | Lightning Resources, which lets you open a bunch of Lightning resources all at once.

  2. The URL for our “preview” is actually the permanent home of our app (once it’s made available to our users). 
    
    * The format of the URL is the following: https://<yourDomain>.lightning.force.com/<yourNamespace>/<yourAppName>.app.

      - <yourAppName> represents the name of your app bundle, in this case, harnessApp.

# What is a Component?

  1. As a practical matter, a component is a bundle that includes a definition resource, written in markup, and may include additional, optional resources like a controller, stylesheet, and so on.

    * A bundle is sort of like a folder. It groups the related resources for a single component. Resources in a bundle are auto-wired together via a naming scheme for each resource type.

    * Auto-wiring just means that a component definition can reference its controller, helper, etc., and those resources can reference the component definition.

  2. A resource is sort of like a file, but stored in Salesforce rather than on a file system.

  3. Our helloWorld.cmp component definition resource is easy to understand.

    * <aura:component>
          <p>Hello Lightning!</p>
      </aura:component>

  4. Let’s see how this works. With helloWorld.cmp active, click the STYLE button in the component palette on the right. This opens a new tab for the style resource that was added to the helloWorld bundle. 

    * It starts with a single, empty selector, .THIS. To see how this works, add a simple style to the stylesheet, so that it looks like the following.

      - .THIS {
         }
         p.THIS {
             font-size: 24px;
         }

      - At runtime .THIS is replaced with a style scoping string named for your component.

      - It limits style rules to only this component, so that you can create styles that are specific to the component, without worrying about how those styles might affect other components.

  5. We can also have components be contained in other components. 

    * The arrangement, or composition, of these smaller components defines the differences between the three larger structures.

    * n the Developer Console, create an Aura component named helloHeading. For its markup, paste in the following code.
    
      - <aura:component>
            <h1>W E L C O M E</h1>
        </aura:component>

    * Now, click back to helloWorld.cmp, and add <c:helloHeading/> to it, above the “Hello Lightning” line. Your helloWorld component definition should now look like this

      - <aura:component>
	  
          <c:helloHeading/>
	          
          <p>Hello Lightning!</p>
	          
        </aura:component>

      - We say that helloHeading is a child component of helloWorld, or that helloHeading is nested inside helloWorld

# What Is an App? 

  1. An app is just a special kind of component

    * An app uses <aura:application> tags instead of <aura:component> tags.

    * Only an app has a Preview button in the Developer Console.

  2. What Are Apps For?

    * When writing markup, you can add a component to an app, but you can’t add an app to another app, or an app to a component.

    * An app has a standalone URL that you can access while testing, and which you can publish to your users. 
      
      - We often refer to these standalone apps as “my.app.”

    * You can’t add apps to Lightning Experience or the Salesforce app—you can only add components.

    * You publish functionality built with Lightning Components in containers. Lightning Components apps are one kind of container for our Lightning components. 

  3. what exactly do you add to the App Launcher, if not an app?

    * What you add to App Launcher is a Salesforce app, which wraps up an Aura component, something defined in a <aura:component>.

    * An Aura components app—that is, something defined in a <aura:application> —can’t be used to create Salesforce apps. 

