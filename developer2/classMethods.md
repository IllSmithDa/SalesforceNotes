# Method Basics

  1. Method requires data types, parameters, and a body method 

    * A method can only have up to 32 parameters 

    * methods must return the type assigned to it 

      - string method must return a string 

    * void methods have no return type no, so no value can be returned

    * methods can be polymorphic 

      - two or more methods with the same name will have different number of parameters

      - when method is called, it will call the one with the parameters with the exact match
       
      - If match cannot be found, it will seek an approximate match using coercion rules

  2. Static methods, variables, and initialization code have these characteristics.

    * They’re associated with a class.

    * !A static method or variable doesn’t require an instance of the class in order to run.

    * !Before an object of a class is created, all static member variables in a class are initialized, and all static initialization code blocks are executed.
      
      - These items are handled in the order in which they appear in the class.
      
    * !They’re allowed only in outer classes. Methods in inner classes cannot be static

    * A static method is used as a utility method, and it never depends on the value of an instance member variable. 
    
      - Because a static method is only associated with a class, it can’t access the instance member variable values of its class.

    * They’re initialized only when a class is loaded.

    * They aren’t transmitted as part of the view state for a Visualforce page.

  3. Instance methods, member variables, and initialization code have these characteristics.

    * They’re associated with a particular object.

    * They have no definition modifier.

    * They’re created with every object instantiated from the class in which they’re declared.

  4. In Apex, you can have static methods, variables, and initialization code. However, Apex classes can’t be static. 