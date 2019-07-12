# final

  1. Final variables can only be assigned a value once, either when you declare a variable or inside a constructor. You must assign a value to it in one of these two places.

  2. To define a constant, mark a variable as both static and final.

  3. Static final variables can be changed in static initialization code or where defined.

  4. Methods and classes are final by default. You cannot use the final keyword in the declaration of a class or method

    * This means they cannot be overridden. Use the virtual keyword if you need to override a method or class.

# instanceof

  1. If you need to verify at run time whether an object is actually an instance of a particular class, use the instanceof keyword.

  2. The instanceof keyword can only be used to verify if the target type in the expression on the right of the keyword is a viable alternative for the declared type of the expression on the left.

    * Object o = null;
      Boolean result = o instanceof Account;
      System.assertEquals(false, result);

# super 

  1. The super keyword can be used by classes that are extended from virtual or abstract classes. By using super, you can override constructors and methods from the parent class.

  2. For example, if you have the following virtual class:

    * public virtual class SuperClass {
          public String mySalutation;
          public String myFirstName;
          public String myLastName;
      
          public SuperClass() {
      
              mySalutation = 'Mr.';
              myFirstName = 'Carl';
              myLastName = 'Vonderburg';
          }
      
          public SuperClass(String salutation, String firstName, String lastName) {
      
              mySalutation = salutation;
              myFirstName = firstName;
              myLastName = lastName;
          }
      
          public virtual void printName() {
      
              System.debug('My name is ' + mySalutation + myLastName);
          }
      
         public virtual String getFirstName() {
             return myFirstName;
         }
      } 
  3. You can create the following class that extends Superclass and overrides its printName method:

    * public class Subclass extends Superclass {
        public override void printName() {
              super.printName();
              System.debug('But you can call me ' + super.getFirstName());
          }
      }

      - The expected output when calling Subclass.printName is My name is Mr. Vonderburg. But you can call me Carl.
  
  4. You can also use super to call constructors. Add the following constructor to SubClass:

    * public Subclass() {
        super('Madam', 'Brenda', 'Clapentrap');
      }

      - Now, the expected output of Subclass.printName is My name is Madam Clapentrap. But you can call me Brenda.

  5. Only classes that are extending from virtual or abstract classes can use super.

  6. You can only use super in methods that are designated with the override keyword.

# this 

  1. You can use the this keyword in dot notation, without parenthesis, to represent the current instance of the class in which it appears. 

  2. Use this form of the this keyword to access instance variables and methods. For example:

    * public class myTestThis {
        string s;
          {
              this.s = 'TestString';
          }
      }
      
      - In the above example, the class myTestThis declares an instance variable s. The initialization code populates the variable using the this keyword.

  3. Or you can use the this keyword to do constructor chaining, that is, in one constructor, call another constructor. In this format, use the this keyword with parentheses. For example:

    * public class testThis {
      
         // First constructor for the class. It requires a string parameter.
         public testThis(string s2) {
         }
      
         // Second constructor for the class. It does not require a parameter.
         // This constructor calls the first constructor using the this keyword.
         public testThis() {
             this('None');
         }
      }
    
    * When you use the this keyword in a constructor to do constructor chaining, it must be the first statement in the constructor.

# transient

  1. Use the transient keyword to declare instance variables that can't be saved, and shouldn't be transmitted as part of the view state for a Visualforce page. For example:

    * Transient Integer currentTotal;

  2. You can also use the transient keyword in Apex classes that are serializable, namely in controllers, controller extensions, or classes that implement the Batchable or Schedulable interface.

  3. In addition, you can use transient in classes that define the types of fields declared in the serializable classes.

  4. Declaring variables as transient reduces view state size. 

  5. A common use case for the transient keyword is a field on a Visualforce page that is needed only for the duration of a page request, but should not be part of the page's view state and would use too many system resources to be recomputed many times during a request.

  6. Some Apex objects are automatically considered transient, that is, their value does not get saved as part of the page's view state. These objects include the following:

    * PageReferences

    * XmlStream classes

    * Collections automatically marked as transient only if the type of object that they hold is automatically marked as transient, such as a collection of Savepoints

    * Most of the objects generated by system methods, such as Schema.getGlobalDescribe.

    * JSONParser class instances.

  7. The following example contains both a Visualforce page and a custom controller. Clicking the refresh button on the page causes the transient date to be updated because it is being recreated each time the page is refreshed. The non-transient date continues to have its original value, which has been deserialized from the view state, so it remains

    * DateTime t1;
      transient DateTime t2;

# with sharing or without sharing 

  1. The with sharing keyword allows you to specify that the sharing rules for the current user are considered for the class. 

  2. You have to explicitly set this keyword for the class because Apex code runs in system context.

  3. In system context, Apex code has access to all objects and fields— object permissions, field-level security, sharing rules aren’t applied for the current user.

  4. This strategy ensures that code doesn’t fail to run because of hidden fields or objects for a user 

  5. The only exceptions to this rule are Apex code that is executed with the executeAnonymous call and Chatter in Apex. 

  6. executeAnonymous always executes using the full permissions of the current user. 

  7. Use the with sharing keywords when declaring a class to enforce the sharing rules that apply to the current user. For example:

    * public with sharing class sharingClass {
      
      // Code here
      
      }

  8. Use the without sharing keywords when declaring a class to ensure that the sharing rules for the current user are not enforced

  9. For example, you can explicitly turn off sharing rule enforcement when a class is called from another class that is declared using with sharing.

    * public without sharing class noSharing {
      
      // Code here
      
      }

  10. The sharing setting of the class where the method is defined is applied, not of the class where the method is called. 
  
    * For example, if a method is defined in a class declared with with sharing is called by a class declared with without sharing, the method executes with sharing rules enforced.

  11. If a class isn’t declared as either with or without sharing, the current sharing rules remain in effect. Therefore, the class doesn’t enforce sharing rules except when it acquires sharing rules from another class. 
  
    * For example, if the class is called by another class that has sharing enforced, then sharing is enforced for the called class.

  12. Both inner classes and outer classes can be declared as with sharing. The sharing setting applies to all code contained in the class, including initialization code, constructors, and methods.

  13. Inner classes do not inherit the sharing setting from their container class.

  14. Classes inherit this setting from a parent class when one class extends or implements another.