# Handling Actions with Controllers 

  1. Basic Example of a Controller

    * <aura:component>
       
          <aura:attribute name="message" type="String"/>
       
          <p>Message of the day: {!v.message}</p>
       
          <div>
           <lightning:button label="You look nice today."
               onclick="{!c.handleClick}"/>

           <lightning:button label="Today is going to be a great day!"
               onclick="{!c.handleClick}"/>
          </div>
       
      </aura:component>

      - Just like the v.message expression, c.handleClick is a value provider, c, with a property, handleClick. c is the value provider for the component’s client-side controller, and handleClick is a function defined in that controller.

      -  So, {!c.handleClick} is a reference to an action handler in the component’s controller.

# What is a controller?

  1. A controller is basically a collection of code that defines your app’s behavior when “things happen,” whereby “things” we mean user input, timer and other events, data updates, and so on. 

  2. For Lightning Components, a controller is a resource in a component bundle that holds the action handlers for that component. 

    *  Action handlers are just JavaScript functions with a particular function signature.
  
  3. Is Lightning Components built on the MVC pattern?

    * In a word, no. There are similarities, to be sure, but it would be more correct to say that Lightning Components is View-Controller-Controller-Model, or perhaps View-Controller-Controller-Database.

  3. Why is “controller” doubled up in that pattern name?

    * ecause when interacting with Salesforce, your components will have a server-side controller in addition to the client-side controller we’ve worked with in this unit. 

    * This dual controller design is the key difference between Lightning Components and MVC.

  4. What’s the distinction between “model” and “database”? 

    * In traditional MVC, the model is a programmatic abstraction (usually a class) between the underlying data storage (usually a relational database) and the rest of the application

    * In Lightning Components, there’s no Apex class that directly stands in between @AuraEnabled controller methods and DML operations.

    * sObjects are already an abstraction between your Apex code and the underlying storage layer. 

    * You can add calculation fields, validation logic, and even add fully programmatic behavior in the form of triggers

# Controller example 

  1. ({
         handleClick: function(component, event, helper) {
             var btnClicked = event.getSource();         // the button
             var btnMessage = btnClicked.get("v.label"); // the button's label
             component.set("v.message", btnMessage);     // update our message
         }
     })

     * Controller resources have an interesting format. They are JavaScript objects that contain a map of name-value pairs, where the name is the name of the action handler and the value is a function definition.

      *  In the action handler, the controller gets the button that was clicked, pulls the label text out of it, and then sets the component’s message attribute to that text (2). And the message of the day is updated (3). You look nice today!

# Action Handlers

  1. The combination of name-value pair and specific function signature is an action handler.

    *  You’ll hear or see the terms action handler, controller action, and controller function used interchangeably, and for the most part that’s correct.

  2. When you click the CONTROLLER button in the Developer Console, you’ll get a controller resource with an example action handler already added. 

  3. The one trick is—and you will get syntax errors if you forget—you need to put commas between action handlers. 

  4. ({
         handleClick: function(component, event, helper) {
             var btnClicked = event.getSource();         // the button
             var btnMessage = btnClicked.get("v.label"); // the button's label
             component.set("v.message", btnMessage);     // update our message
         }
     })

  5. handleClick: function(component, event, helper) {

    * The action handler name, followed by an anonymous function declaration.

    *  you should always declare your controller functions to take these three parameters

      - component — the component. In this case, it’s helloMessageInteractive.

      - event — the event that caused the action handler to be called.

      - helper — the component’s helper, another JavaScript resource of reusable functions.

  6. var btnClicked = event.getSource();   

    * Remember that handleClick is connected to our <lightning:button> tag and its onclick attribute. 

    * The event, then, is someone clicking the button

    * Inside that event it has the notion of a source, the thing that generated the event, which is the button itself. 

      - So, calling event.getSource() gets us a reference to the specific <lightning:button> that was clicked.
  
  7. var btnMessage = btnClicked.get("v.label"); 

    * label is just another attribute, much like the message attribute we added to helloMessageInteractive

    * You can call get() on any component and provide the name of the attribute you want to retrieve, in the format v.attributeName. The result is the attribute value. 

    * Note that, as in component markup, v represents the view, the component itself—but in this case, it’s the <lightning:button> child component, not helloMessageInteractive

  8. component.set("v.message", btnMessage);

    * Changes our message attribute to the new message text.

    * We’re calling set() on component—the helloMessageInteractive component itself. This is a pattern you’ll repeat in virtually every component you create: get values from child components, maybe do some processing, and set values in the component itself.

# Function Chaining, Rewiring, and Simple Debugging

  1. Our first version of handleClick was three lines of code, because we broke each step in the get-process-set pattern into separate lines. 

  2. You can use something called function chaining to collapse those into fewer lines.

  3. ({
         handleClick: function(component, event, helper) {
             var btnClicked = event.getSource();         // the button
             var btnMessage = btnClicked.get("v.label"); // the button's label
             component.set("v.message", btnMessage);     // update our message
         }
     })

    * Done in three lines 

  4. handleClick2: function(component, event, helper) {
        var newMessage = event.getSource().get("v.label");
        component.set("v.message", newMessage);
     }

    * Done in 2 lines

  5. handleClick3: function(component, event, helper) {
       component.set("v.message", event.getSource().get("v.label"));
     }

    * Done in 1 line
  
  6. Often times its best to do it the long way first and then refactor into fewer lines to avoid mistakes and errors. 

  7. Also, the time honoring technique of console.log() or JSON.stringify(object) applies here as well

  