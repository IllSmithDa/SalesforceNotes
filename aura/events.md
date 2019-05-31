# Connect Components with Events

  1. There are two principal ways to interact with or affect another component. 
  
    * The first way is one we’ve seen and done quite a bit of already: setting attributes on the component’s tag.

    * The second way to interact with a component is through events.

  2. Like attributes, components declare the events they send out, and the events they can handle. 

  3.  Like attributes, these public events constitute a part of the component’s public API.

  4. When you set the onclick attribute on a <lightning:button> to an action handler in a component’s controller, you create a direct relationship between those two components. 
    
    * They are linked, and while they’re using public APIs to remain independent of each other, they’re still coupled.

    * Events are different. Components don’t send events to another component. That’s not how events work. Components broadcast events of a particular type. If there’s a component that responds to that type of event, and if that component “hears” your event, then it will act on it.

    * You can think of the difference between attributes and events as the difference between wired circuits and wireless circuits. And we’re not talking wireless phones here. One component doesn’t get the “number” for another component and call it up. That would be an attribute. No, events are like wireless broadcasts. 

    * Your component gets on the radio, and sends out a message. Is there anyone out there with their radio set turned on, and tuned to the right frequency? Your component has no way of knowing—so you should write your components in such a way that it’s OK if no one hears the events they broadcast.

# Sending an Event from a Compnoent 

  1. <lightning:input type="toggle" 
              label="Reimbursed?"
              name="reimbursed"
              class="slds-p-around--small"
              checked="{!v.expense.Reimbursed__c}"
              messageToggleActive="Yes"
              messageToggleInactive="No"
              onchange="{!c.clickReimbursed}"/>
  
    * type="toggle" is really a checkbox with a toggle switch design.
  
    * class enables you to apply custom CSS styling or use SLDS utilities. 
  
    * messageToggleActive and messageToggleInactive provides a custom label for the checked and unchecked positions.  
  
    * Finally, the onchange attribute of <lightning:input> gives us an easy way to wire the toggle switch to an action handler that updates the record when you slide right (checked) or slide left   (unchecked).
  
    * Components do not reach into other components and set values on them. There’s no way to say “Hey grandparent, I’m gonna update expenses.” Components keep their hands to themselves.
  
      - When a component wants an ancestor component to make a change to something, it asks. Nicely. By sending an event.
  
  2. Sending an event looks almost the same as handling the update directly. Here’s the code for the clickReimbursed handler. 

    * ({
          clickReimbursed: function(component, event, helper) {
              var expense = component.get("v.expense");
              var updateEvent = component.getEvent("updateExpense");
              updateEvent.setParams({ "expense": expense });
              updateEvent.fire();
          }
      })

    * The preceding code for clickReimbursed does the following:

      - Gets the expense that changed.

      - Creates an event named updateExpense.

      - Packages expense into the event.

      - Fires the event.

    * updateExpense is a custom event, that is, an event we write ourselves. 

    * You can tell because, unlike getting a server action, we use component.getEvent() instead of component.get(). Also, what we are getting doesn’t have a value provider, just a name. We’ll define this event in just a moment.

# Defining an Event

  1. In the Developer Console, select File | New | Lightning Event, and name the event “expensesItemUpdate”. 

  2. <aura:event type="COMPONENT">
       <aura:attribute name="expense" type="Expense__c"/>
     </aura:event>

  3. There are two types of events, component and application.

  4. Here we’re using a component event, because we want an ancestor component to catch and handle the event. An ancestor is a component “above” this one in the component hierarchy.

  5. If we wanted a “general broadcast” kind of event, where any component could receive it, we’d use an application event instead.

  6. The other thing to notice about the event is how compact the definition is. 

    * We named the event when it was created, expensesItemUpdate, and its markup is a beginning and ending <aura:event> tag, and one <aura:attribute> tag. An event’s attributes describe the payload it can carry.

    * In the clickReimbursed action handler, we set the payload with a call to setParams().

    * Here in the event definition, we see how the event parameter is defined, and that there are no other valid parameters.

# Sending an Event

  1. We already looked at how to actually fire an event, in the clickReimbursed action handler. But for that to work, we need to do one last thing, and that’s register the event.

  2. Add this line of markup to the expenseItem component, right below its attribute definitions.

    * <aura:registerEvent name="updateExpense" type="c:expensesItemUpdate"/>

    * This markup says that our component fires an event, named “updateExpense”, of type “c:expensesItemUpdate”.
    
    * Here in expenseItem, we’re going to send an event named updateExpense

      - Later in expenseForm, we’re going to send an event named createExpense. 

      - Both of these events need to include an expense to be saved to the server

      - And so they both use the c:expensesItemUpdate event type, or package format, to send their events.

      - On the receiving end, our main expenses component is going to register to handle both of these events.

      - Though the server call ends up being the same, the user interface updates are slightly different.

      - So how does expenses know whether to create or update the expense in the c:expensesItemUpdate package? By the name of the event being sent.
  
  3. Before we move on to handling events, let’s summarize what it takes to send them. 

    * Define a custom event by creating a Lightning Event, giving it a name and attributes.

    * Register your component to send these events, by choosing a custom event type and giving this specific use of that type a name.

    * Fire the event in your controller (or helper) code by: 

      - Using component.getEvent() to create a specific event instance.

      - Sending the event with fire().

# Handling an Event - Enabling the expenseItem component to send an event required three steps. Enabling the expenses component to receive and handle these events requires three parallel steps.

  1. Define a custom event. We’ve already done this, because expenseItem is sending the same custom event that expenses is receiving.

  2. Register the component to handle the event. This maps the event to an action handler.

  3. Actually handle the event in an action handler.

    * Since we’ve already done step 1, let’s immediately turn to step 2, and register expenses to receive and handle the updateExpense event. Like registering to send an event, registering to handle one is a single line of markup, which you should add to the expenses component right after the init handler

    * <aura:handler name="updateExpense" event="c:expensesItemUpdate" action="{!c.handleUpdateExpense}"/>

      - Like the init handler, this uses the <aura:handler> tag, and has an action attribute that sets the controller action handler for the event. Like when you registered the event in expenseItem, here you set the name and type of the event—though note the use of the much more sensibly named event attribute for the type.

      - What’s new, and specific to handling custom events, is the combination of the attributes, and knowing how this receiver “socket” in expenses matches up with the sender “socket” in expenseItem. 

    * We’ll start with the handleUpdateExpense action handler. Here’s the code, and be sure to put it riiiiiight under the clickCreate action handler. 

      - handleUpdateExpense: function(component, event, helper) {
          var updatedExp = event.getParam("expense");
          helper.updateExpense(component, updatedExp);
        }

    * And now let’s add the updateExpense helper function. As we did with the action handler, make sure you put this code right below the createExpense helper function.

      - updateExpense: function(component, expense) {
          var action = component.get("c.saveExpense");
          action.setParams({
              "expense": expense
          });
          action.setCallback(this, function(response){
              var state = response.getState();
              if (state === "SUCCESS") {
                  // do nothing!
              }
          });
          $A.enqueueAction(action);
        },

      - Note that this code only handles the case where the server is successful at updating the expense record. We’d definitely have some work to do if there was an error. 

# Refactor the Helper Functions

  1. Let’s go back to that opportunity we saw to factor out some common code. The two helper functions are identical except for the callback. So, let’s make a new, more generalized function that takes the callback as a parameter. 

    * saveExpense: function(component, expense, callback) {
        var action = component.get("c.saveExpense");
        action.setParams({
            "expense": expense
        });
        if (callback) {
            action.setCallback(this, callback);
        }
        $A.enqueueAction(action);
      },
  
  2. The callback parameter is optional. If it’s there, we’ll pass it along to action. Simple. And now we can reduce our event-specific helper functions to the following code. 

    * createExpense: function(component, expense) {
          this.saveExpense(component, expense, function(response){
              var state = response.getState();
              if (state === "SUCCESS") {
                  var expenses = component.get("v.expenses");
                  expenses.push(response.getReturnValue());
                  component.set("v.expenses", expenses);
              }
          });
      },
      updateExpense: function(component, expense) {
          this.saveExpense(component, expense);
      },

      - createExpense is only a little shorter, but it’s exclusively focused on what to do when the response comes back (the callback). And wow, updateExpense is a one-liner!

  3. Refactor the Add Expense Form

    * This next task involves extracting the Add Expense form from the expenses component, and moving it to its own, new component. 