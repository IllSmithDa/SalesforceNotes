# Classes
  
  1. A class is a template or blueprint from which objects are created. An object is an instance of a class.

    * A skeleton with no memory

  2. All objects have state and behavior, that is, things that an object knows about itself, and things that an object can do.

    * A class can contain variables and methods. 

  3. An interface is like a class in which none of the methods have been implemented—the method signatures are there, but the body of each method is empty.

  4. Apex classes cannot be static only methods can be static

# Class Definition

  1. In Apex, you can define top-level classes (also called outer classes) as well as inner classes, that is, a class defined within another class. You can only have inner classes one level deep.

    * public class myOuterClass {

        // Additional myOuterClass code here
        class myInnerClass {
          // myInnerClass code here
        }

      }

  2. private class - access modifier declares that this class is only known locally, that is, only by this section of code. 

    * This is the default access for inner classes

      - If you do not specify an access modifier, the method or variable is private.

    * !This is the default, and means that the method or variable is accessible only within the Apex class in which it is defined.

  3. protected - This means that the method or variable is visible to any inner classes in the defining Apex class and to the classes that extend the defining Apex class.

    * You can only use this access modifier for instance methods and member variables.  

    * Note that it is strictly more permissive than the default (private) setting, just like Java.

  4. The public access modifier declares that this class is visible in your application or namespace.

    * This means the method or variable can be used by any Apex in this application or namespace.

    * The outer most class in Apex classes must either be public or global 

    * !In Apex, the public access modifier is not the same as it is in Java. This was done to discourage joining applications, to keep the code for each application separate.

    * In Apex, if you want to make something public like it is in Java, you need to use the global access modifier.

  5. Global access modifier means the method or variable can be used by any Apex code that has access to the class, not just the Apex code in the same application. 

    * This access modifier should be used for any method that needs to be referenced outside of the application, either in the SOAP API or by other Apex code.

    * If you declare a method or variable as global, you must also declare the class that contains it as global.

    * We recommend using the global access modifier rarely, if at all. Cross-application dependencies are difficult to maintain.

  6. The virtual definition modifier declares that this class allows extension and overrides. 

    *  You cannot override a method with the override keyword unless the class has been defined as virtual.
    
  7. The abstract definition modifier declares that this class contains abstract methods, that is, methods that only have their signature declared and no body defined.

    * You cannot add an abstract method to a global class after the class has been uploaded in a Managed - Released package version.

    * If the class in the Managed - Released package is virtual, the method that you can add to it must also be virtual and must have an implementation.

    * You cannot override a public or protected virtual method of a global class of an installed managed package.

# Constructors

  1. Not required as it will auto define an empty one if it is not user defined

  2. Constructor is code that is invoked when objected is generated from a class

    * Up to the user to determine which functions and variables are needed to be invoked right away or right when object is created

  3. Constructor with no arguments
    
    * public TestObject2() {
      this(DEFAULT_SIZE); // Using this(...) calls the one argument constructor   
     }
  
  4. Constructor with one argument
    * public TestObject2(Integer ObjectSize) {
        size = ObjectSize; 
      }

  5. public class Leads {
       
       // First a no-argument constructor
       public Leads () {}
       
       // A constructor with one argument
       public Leads (Boolean call) {}

       // A constructor with two arguments
       public Leads (String email, Boolean call) {}

       // Though this constructor has the same arguments as the
       // one above, they are in a different order, so this is legal
       public Leads (Boolean call, String email) {}

     }
