# Component Attributes

  1. How to enable a component to accept input when it’s created?

    * We need to set values on the component. We do this using attributes. 

  2. Attributes on components are like instance variables in objects. 
  
    * They’re a way to save values that change, and a way to name those value placeholders

    * For example, let’s say we wanted to write a helloMessage component that prints a custom message. We can envision adding a message attribute to this component to customize its output. And then we can set that message when we add the component to our app, like the following. 

      - <aura:component>
	  
          <c:helloMessage message="You look nice today."/>
	    
        </aura:component>

# How to Define attributes for a component 

  1. An attribute is defined using an <aura:attribute> tag, which requires values for the name and type attributes, and accepts these optional attributes: default, description, required.

  2. A component attribute is the place where you can store a value. In the preceding example, the helloMessage component has a component attribute named message. 

  3. You define a component attribute using the <aura:attribute> tag. 

  4. The <aura:attribute> tag itself takes attributes when you use it. 

    * That is, when you define a component attribute using the <aura:attribute> tag, you set attributes on <aura:attribute> that specify the “shape” of the component attribute you’re defining.

  5. Example using helloMessage component 

    * <aura:component>
          <aura:attribute name="message" type="String"/>
          <p>Hello! {!v.message}</p>
      </aura:component>

      - The helloMessage component has one component attribute, and that attribute is defined by setting the name and type of the attribute.

      - The name of the attribute is message and, once we learn about expressions, that’s how you’ll reference it.

      - The other attribute we’ve used here is type, and we’ve set it because it’s required in an attribute definition. 

      - It says that the message attribute contains a string, which makes sense. 

      - We’re outputting the contents of message using the expression {!v.message}. That is, this expression references the message attribute. The expression is evaluated, and resolves to the text string that’s currently stored in message. And that’s what the expression outputs into the body of the component.
    
  6. What is an expression? 

    * An expression is basically a formula, or a calculation, which you place within expression delimiters (“{!” and “}”). So, expressions look like the following:

      - {!<expression>}

    * Basically a formula, much like you’d write in a calculation field, filter criteria, or Visualforce.

    * <aura:component>
          <aura:attribute name="message" type="String"/>
          <p>{!'Hello! ' + v.message}</p>
      </aura:component>

      - All we’ve done is move the “Hello” part from static text outside the expression to literal text inside the expression.

      - Notice that we’ve used the “+” operator to concatenate the two strings together.

    * Moving the greeting text inside the expression lets you use labels, instead of literal text, which makes it easier to update (and translate) your components. For example:

      - {!$Label.c.Greeting + v.message}

      - Not that you can’t use JavaScript in expressions in Aura components markup.

    * You can pass expressions to another component to set the value on that component. 

      - <aura:component>
            <aura:attribute name="customMessage" type="String"/>
            <p> <c:helloMessage message="{!v.customMessage}"/> </p>
        </aura:component>
      
      -  Here’s a new component that passes in a custom value to the helloMessage component. Passing the value to the other component overrides the value on that component.

# Value Providers

  1. Attributes came with something like v.message. v is something called a value provider.

  2. Value providers are a way to group, encapsulate, and access related data. 

    * In simplest definition (as it is a complex topci), think of v as an automatic variable that’s made available for you to use.

  3. v gives you a “hook” to access the component’s message attribute, and it’s how you access all of a component’s attributes.

  4. Values in a value provider are accessed as named properties. 

    * To use a value, separate the value provider and the property name with a dot (period).

      - For example, v.message, as we’ve seen.

    * When an attribute of a component is an object or other structured data (that is, not a primitive value), access the values on that attribute using the same dot notation\\\

      - For example, {!v.account.Id} accesses the Id field of an account record.

      - For deeply nested objects and attributes, continue adding dots to traverse the structure and access the nested values.

# Attribute Data Types

  1. There are a number of different attribute types.

  2. Primitives data types, such as Boolean, Date, DateTime, Decimal, Double, Integer, Long, or String. The usual suspects in any programming language.

  3. Standard and custom Salesforce objects, such as Account or MyCustomObject__c.

  4. Collections, such as List, Map, and Set.

  5. Custom Apex classes.

  6. Framework-specific types, such as Aura.Component, or Aura.Component[]. 

  7. <aura:component>
         <aura:attribute name="expense" type="Expense__c"/>
         <p>Amount:
             <lightning:formattedNumber value="{!v.expense.Amount__c}" style="currency"/>
         </p>
         <p>
             Client: {!v.expense.Client__c}
         </p>
         <p>
             <lightning:input type="toggle"                            
                              label="Reimbursed?"                           
                              name="reimbursed"                         
                              checked="{!v.expense.Reimbursed__c}" />
          </p> 
         <!-- Other markup here -->
     </aura:component>

    * The component’s purpose is to display the details of an expense by referencing the field on the Expense__c record, using the {!v.expense.fieldName} expression. 

    * We’re using the <lightning:input> component of type="toggle", which is a checkbox in the form of a toggle, so that we can update the value in the UI later. 

# Other Aspects of Attribute Definitions

  1. The default attribute defines the default attribute value. It’s used when the attribute is referenced and you haven’t yet set the attribute’s value.

  2. The required attribute defines whether the attribute is required. The default is false.

  3. The description attribute defines a brief summary of the attribute and its usage. 

# Example

  1. <aura:component>
       <aura:attribute name="messages" type="List"
           default="['You look nice today.',
               'Great weather we\'re having.',
               'How are you?']"/>
       <h1>Hello Playground</h1>
       <p>Silly fun with attributes and expressions.</p>
   
       <h2>List Items</h2>
       <p><c:helloMessage message="{!v.messages[0]}"/></p>
       <p><c:helloMessage message="{!v.messages[1]}"/></p>
       <p><c:helloMessage message="{!v.messages[2]}"/></p>
   
       <h2>List Iteration</h2>
       <aura:iteration items="{!v.messages}" var="msg">
           <p><c:helloMessage message="{!msg}"/></p>
       </aura:iteration>
   
       <h2>Conditional Expressions and Global Value Providers</h2>
       <aura:if isTrue="{!$Browser.isIPhone}">
           <p><c:helloMessage message="{!v.messages[0]}"/></p>
       <aura:set attribute="else">
           <p><c:helloMessage message="{!v.messages[1]}"/></p>
           </aura:set>
       </aura:if>
     </aura:component>

    * First, helloPlayground has one attribute, messages, that’s a complex data type, List. 

    * And it has a default value for that list, an array of three single-quoted strings separated by commas. And, in the List Items section, you can see how to access each of the strings using an index. 

    * What happens if someone creates a <c:helloPlayground> with only two messages? Accessing the third item will fail, and while it won’t cause a crash here, with more complex components it might.

    * The <aura:iteration> component repeats its body once per item in its items attribute, so the list shrinks or grows as we have fewer or more messages. 

    * In the Conditional Expressions and Global Value Providers section, you can see a way to choose between two different possible outputs.

    * <aura:if> component lets you, for example, add an edit button to a page only if the user has edit privileges on the object

  2.  In object-oriented programming, there’s a difference between a class and an instance of that class. Components have a similar concept. When you create a .cmp resource, you are providing the definition (class) of that component

    * When you put a component tag in a .cmp, you are creating a reference to (instance of) that component.

    * We can add multiple instances of the same component with different attributes.

    * In the preceding example, when you use the default value for messages, you’ll end up with eight references to (instances of) our <c:helloMessage> component. If you pass in a longer list, you could end up with (many) more.