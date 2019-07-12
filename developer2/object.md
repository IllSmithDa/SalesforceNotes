# Objects 

  1. Classes have no memory or instantiation on their own 

  2. Object is a real instance of the class

  3. contains varaibles, functions, memory

  4. Object = class + memory 

    * e.g myClass newObject = new MyClass(parameterName = '');

  6. You can now call methods that belong to the newly created object 

    * newObject.myMethod(345);

  7. You cannot call static methods using the object name. 
  
    * You can only call a static method it using the class name

      - wrong = newObject.staticMethod();

      - right = myClass.staticMethod();

  8. Static functions instead allow you to generate function as it will allocate memory 

    * While you can still access static functions using object, it is considered bad practice

  