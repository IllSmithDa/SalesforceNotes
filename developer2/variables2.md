# Static Variables

  1. A static variable is static only within the scope of the Apex transaction. 

    * Static variables are initialized only once, at the start of the execution. 
    
    * These variables will be initialized first, before the initialization of any instance variables. 
    
    * A single copy to be shared by all instances of the class. 
    
    * A static variable can be accessed directly by the class name and doesn't need any object
  
      - Static variables are those which can be used without instantiating a class.

      - !!Instance variables are called by object while static are called by class. Static variables and methods are not included in view state for a vf page.

      - You can call a static variable directly by class name without requiring instance of class similar goes for static methods.

      - Static variable are global variable which are not related to particular object

    * It’s not static across the server or the entire organization. 

    * Before an object of a class is created, all static member variables in a class are initialized, and all static initialization code blocks are executed. 
    
      - These items are handled in the order in which they appear in the class.

  2. The value of a static variable persists within the context of a single transaction and is reset across transaction boundaries.

    * For example, if an Apex DML request causes a trigger to fire multiple times, the static variables persist across these trigger invocations.

  3. !To store information that is shared across instances of a class, use a static variable.

  4. All instances of the same class share a single copy of the static variable.
   
    * For example, all triggers that a single transaction spawns can communicate with each other by viewing and updating static variables in a related class. 

    * A recursive trigger can use the value of a class variable to determine when to exit the recursion.

  5. A static variable defined in a trigger doesn’t retain its value between different trigger contexts within the same transaction, such as between before insert and after insert invocations.

    * !Instead, define the static variables in a class so that the trigger can access these class member variables and check their static values.

  6. !A class static variable can’t be accessed through an instance of that class. 
   
    * If class MyClass has a static variable myStaticVariable, and myClassInstance is an instance of MyClass, myClassInstance.myStaticVariable is not a legal expression.

      - The same is true for instance methods. If myStaticMethod() is a static method, myClassInstance.myStaticMethod() is not legal. 

      - Instead, refer to those static identifiers using the class: MyClass.myStaticVariable and MyClass.myStaticMethod()
  
  7. Similar to other static code, a static initialization code block is only initialized once on the first use of the class.

  8. A class can have any number of either static or instance initialization code blocks. They can appear anywhere in the code body. 

  public class colorClass {

      static Map<String, RGB> colorMap = new Map<String, RGB>();

      static {
          colorMap.put('red', new RGB(255, 0, 0));
          colorMap.put('green', new RGB(0, 255, 0));
          colorMap.put('blue', newRGB(0, 0, 255))
      }
  }

# Instanced variables

  1. They’re associated with a particular object.

  2. They have no definition modifier. (no key words like static)

  3. They’re created with every object instantiated from the class in which they’re declared.

  4. Instance methods and member variables are used by an instance of a class, that is, by an object. 

  5. An instance member variable is declared inside a class, but not within a method.

  6. Instance methods usually use instance member variables to affect the behavior of the method.

# Constant Variables 

  1. Apex constants are variables whose values don’t change after being initialized once. 
  
  2. Constants can be defined using the final keyword.

  3. The final keyword means that the variable can be assigned at most once, either in the declaration itself, or with a static initializer method if the constant is defined in a class.
    
    * static final Integer PRIVATE_INT_CONST = 200;

    * static final Integer PRIVATE_INT_CONST2;
      public static Integer calculate() {
       return 2 + 7;
      }
      static {
        PRIVATE_INT_CONST2 = calculate();
      }