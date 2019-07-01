# What is Apex? Other than the fact that its programming language

  1. Hosted—Apex is saved, compiled, and executed on the server—the Lightning Platform.

  2. Object oriented—Apex supports classes, interfaces, and inheritance.

  3. Strongly typed—Apex validates references to objects at compile time.

  4. Multitenant aware—Because Apex runs in a multitenant platform, it guards closely against runaway code by enforcing limits, which prevent code from monopolizing shared resources.

  5. Integrated with the database—It is straightforward to access and manipulate records. Apex provides direct access to records and their fields, and provides statements and query languages to manipulate those records.ntegrated with the database—It is straightforward to access and manipulate records. Apex provides direct access to records and their fields, and provides statements and query languages to manipulate those records.

  6. Data focused—Apex provides transactional access to the database, allowing you to roll back operations.

  7. Easy to use—Apex is based on familiar Java idioms.

  8. Easy to test—Apex provides built-in support for unit test creation, execution, and code coverage. Salesforce ensures that all custom Apex code works as expected by executing all unit tests prior to any platform upgrades

  9. Versioned—Custom Apex code can be saved against different versions of the API.

  10. Apex is the first language to be compiled over the internet and the cloud

  11. Strongly typed and runs through a compiler who will convert human language into machine language

# Apex Language Highlights

  1. Classes, interfaces, properties, and collections (including arrays).

  2. Object and array notation.

  3. Expressions, variables, and constants.

  4. Conditional statements (if-then-else) and control flow statements (for loops and while loops).

  5. Unlike other object-oriented programming languages, Apex supports:

    * Cloud development as Apex is stored, compiled, and executed in the cloud.

    * Triggers, which are similar to triggers in database systems.

    * Database statements that allow you to make direct database calls and query languages to query and search data.

    * Transactions and rollbacks.

    * The global access modifier, which is more permissive than the public modifier and allows access across namespaces and applications.

    * Versioning of custom code.

# Development Tools

  1. You can write Apex and access debugging information directly in the browser by using the Salesforce user interface. Open the Developer Console under Your Name or the quick access menu 

# Data Types Overview

  1. Apex supports the following data types.

    * A primitive, such as an Integer, Double, Long, Date, Datetime, String, ID, Boolean, among others.

    * An sObject, either as a generic sObject or as a specific sObject, such as an Account, Contact, or MyCustomObject__c (you’ll learn more about sObjects in a later unit.)

    * A collection, including:

      - A list (or array) of primitives, sObjects, user defined objects, objects created from Apex classes, or collections

      - A set of primitives

      - A map from a primitive to a primitive, sObject, or collection

    * A typed list of values, also known as an enum

    * User-defined Apex classes

    * System-supplied Apex classes

# Apex Collections: List

  1. Lists hold an ordered collection of objects. Lists in Apex are synonymous with arrays and the two can be used interchangeably.

  2. The following two declarations are equivalent. The colors variable is declared using the List syntax.

    * List<String> colors = new List<String>();  - List

    * String[] colors = new List<String>(); - Array

      - Generally, it’s easier to create a list rather than an array because lists don’t require you to determine ahead of time how many elements you need to allocate.

  3. You can add elements to a list when creating the list, or after creating the list by calling the add() method. This first example shows you both ways of adding elements to a list.

    * Create a list and add elements to it in one step
      
      - List<String> colors = new List<String> { 'red', 'green', 'blue' };
      
    * Add elements to a list after it has been created

      - List<String> moreColors = new List<String>();
        moreColors.add('orange');
        moreColors.add('purple');

  4. List elements can be read by specifying an index between square brackets, just like with array elements. Also, you can use the get() method to read a list element. 

    * Get elements from a list 

      - String color1 = moreColors.get(0);
        String color2 = moreColors[0];
        System.assertEquals(color1, color2);

    * Iterate over a list to read elements

      - for(Integer i=0; i<colors.size(); i++) {

          // Write value to the debug log
          System.debug(colors[i]);

        }

# Apex Classes

  1. One of the benefits of Apex classes is code reuse. Class methods can be called by triggers and other classes.

# Save an Apex Class example - Save the EmailManager class in your organization:

  1. Open the Developer Console under Your Name or the quick access menu 

  2. In the Developer Console, click File | New | Apex Class, and enter EmailManager for the class name, and then click OK.

  3. Replace the default class body with the EmailManager class example.

  4. The EmailManager class has a public method (sendMail()) that sends email and uses built-in Messaging methods of the Apex class library. Also, this class has a private helper method (inspectResults()), which can’t be called externally because it is private but is used only within the class. This helper method inspects the results of the email send call and is called by sendMail().

  5. Click Ctrl+S to save your class.

# Anonymous Apex 
  
  1. Anonymous Apex allows you to run lines of code on the fly and is a handy way to invoke Apex, especially to test out functionality

  2. Debug log results are generated, as with any other Apex execution

# How to Access Anonymous Apex

  1. In the Developer Console, click Debug | Open Execute Anonymous Window.

  2. In the window that opens, enter the following. Replace 'Your email address' with your email address.

    * EmailManager em = new EmailManager();
      em.sendMail('Your email address', 'Trailhead Tutorial', '123 body');

  3. Click Execute to test code. 

# Inspect Debug Logs

  1. Debug logs are useful for debugging your code. 

  2. When Apex methods execute, the calls are logged in the debug log.

  3. Also, you can write your own debug messages to the log, which helps in debugging your code in case there are errors.

  4. The inspectResults() helper method, which is called by sendMail(), writes messages to the log by using the System.debug() method to indicate whether the email send operation was successful or had errors. 

  5. You can look for these messages in the debug log that was generated when you executed the method.

# How to Access Logs 

  1. In the Developer Console, click the Logs tab and double-click the most recent log in the list.

  2. Select Debug Only to filter the log so that only log lines for System.debug() statements are shown.

    * You’ll see the following message in the filtered log view, assuming the email was sent without errors.

      - DEBUG|Email sent successfully

# Call a Static Method 

  1. Because the sendMail() method in our class doesn’t access class member variables, it doesn’t need to be an instance method.

  2. Static methods are easier to call than instance methods because they don’t need to be called on an instance of the class but are called directly on the class name.

  3. So in a class Car you might have a method double convertMpgToKpl(double mpg) which would be static, because one might want to know what 35mpg converts to, even if nobody has ever built a Car. But void setMileage(double mpg) (which sets the efficiency of one particular Car) can't be static since it's inconceivable to call the method before any Car has been constructed.

  4. Define static methods in the following scenarios only:

    * If you are writing utility classes and they are not supposed to be changed.
    
    * If the method is not using any instance variable.
    
    * If any operation is not dependent on instance creation.
    
    * If there is some code that can easily be shared by all the instance methods, extract that code into a static method.
    
    * If you are sure that the definition of the method will never be changed or overridden. As static methods can not be overridden.

# Changing to Static Method

  1. In the Developer Console, find the open tab for the EmailManager class and modify the first line of the sendMail() method definition to the following (the only change is the added static keyword.)

    * public static void sendMail(String address, String subject, String body) {
    }

  2. Save the class by pressing Ctrl+S.

  3. Modify the statements in your Execute Anonymous window to call the static method on the class name.

    * EmailManager.sendMail('Your email address', 'Trailhead Tutorial', '123 body');

  4. Click Execute.

    * Now that this method has executed, you can check your email, and optionally, the debug log as in the previous steps.