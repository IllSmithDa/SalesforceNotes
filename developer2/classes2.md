# Enum

  1. An enum is an abstract data type with values that each take on exactly one of a finite set of identifiers that you specify. 

  2. Enums are typically used to define a set of possible values that don’t otherwise have a numerical order, such as the suit of a card, or a particular season of the year.

  3. Although each value corresponds to a distinct integer value, the enum hides this implementation so that you don’t inadvertently misuse the values, such as using them to perform arithmetic. 

  4. After you create an enum, variables, method arguments, and return types can be declared of that type.

  5. To define an enum, use the enum keyword in your declaration and use curly braces to demarcate the list of possible values.

    * public enum Season {WINTER, SPRING, SUMMER, FALL}

  6. By creating the enum Season, you have also created a new data type called Season. You can use this new data type as you might any other data type. 
    
    * Season e = Season.WINTER;
      Season m(Integer x, Season e) {
      
          if (e == Season.SUMMER) return e;
           //...
      } 

  7. You can also define a class as an enum. Note that when you create an enum class you do not use the class keyword in the definition.

    * public enum MyEnumClass { X, Y }

  8. You can use an enum in any place you can use another data type name. If you define a variable whose type is an enum, any object you assign to it must be an instance of that enum class.

  9. Any webservice method can use enum types as part of their signature. When this occurs, the associated WSDL file includes definitions for the enum and its values, which can then be used by the API client.

    * System.StatusCode
  
      - This enum corresponds to the API error code that is exposed in the WSDL document for all API operations. 

      - StatusCode.CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY
        StatusCode.INSUFFICIENT_ACCESS_ON_CROSS_REFERENCE_ENTITY

# Apex Properties 

  1. An Apex property is similar to a variable; however, you can do additional things in your code to a property value before it is accessed or returned.

  2. Properties can be used to validate data before a change is made, to prompt an action when data is changed (such as altering the value of other member variables), or to expose data that is retrieved from some other source (such as another class).

  3. Property definitions include one or two code blocks, representing a get accessor and a set accessor:

    * The code in a get accessor executes when the property is read.

    * The code in a set accessor executes when the property is assigned a new value.

  4. If a property has only a get accessor, it is considered read only.

  5.  If a property has only a set accessor, it is considered write only.

  6. A property with both accessors is considered read-write.

  7. To declare a property, use the following syntax in the body of a class:

    * Public class BasicClass {

        // Property declaration
        access_modifier return_type property_name {

           get {
              //Get accessor code block
           }
           set {
              //Set accessor code block
           }
        } 
      }
  8. For example, the following class defines a property named prop. The property is public. The property returns an integer data type.

    * public class BasicProperty {
         public integer prop {
            get { return prop; }
            set { prop = value; }
         }
      }
    
  9. The following code segment calls the BasicProperty class, exercising the get and set accessors:

    * BasicProperty bp = new BasicProperty();
      bp.prop = 5;                   // Calls set accessor
      System.assertEquals(5, bp.prop);   // Calls get accessor

    * The body of the get accessor is similar to that of a method. It must return a value of the property type. Executing the get accessor is the same as reading the value of the variable.

    * The get accessor must end in a return statement.

    * We recommend that your get accessor not change the state of the object that it is defined on.

    * The set accessor is similar to a method whose return type is void.

    * When you assign a value to the property, the set accessor is invoked with an argument that provides the new value.

    * When the set accessor is invoked, the system passes an implicit argument to the setter called value of the same data type as the property.

    * Properties cannot be defined on interface.

# Automatic Properties

  1. Properties do not require additional code in their get or set accessor code blocks. Instead, you can leave get and set accessor code blocks empty to define an automatic property.

  2. Automatic properties allow you to write more compact code that is easier to debug and maintain.

  3. They can be declared as read-only, read-write, or write-only. 

  4. The following example creates three automatic properties:

    * public class AutomaticProperty {
         public integer MyReadOnlyProp { get; }
         public double MyReadWriteProp { get; set; }
         public string MyWriteOnlyProp { set; }
      }
 
  5. The following code segment exercises these properties:

    * AutomaticProperty ap = new AutomaticProperty();
      ap.MyReadOnlyProp = 5;                 // This produces a compile error: not writable
      ap.MyReadWriteProp = 5;                // No error
      System.assertEquals(5, ap.MyWriteOnlyProp);   // This produces a compile error: not readable

# Using Static Properties
 
  1. When a property is declared as static, the property's accessor methods execute in a static context. 

  2. Therefore, accessors do not have access to non-static member variables defined in the class.

  3. The following example creates a class with both static and instance properties:

    * public class StaticProperty {
         private static integer StaticMember;
         private integer NonStaticMember;
      
         // The following produces a system error
         // public static integer MyBadStaticProp { return NonStaticMember; }
      
         public static integer MyGoodStaticProp { 
           get {return StaticMember;} 
           set { StaticMember = value; } 
         }  
         public integer MyGoodNonStaticProp { 
           get {return NonStaticMember;} 
           set { NonStaticMember = value; } 
         } 
      }
    
  4. The following code segment calls the static and instance properties:

    * StaticProperty sp = new StaticProperty();
      // The following produces a system error: a static variable cannot be
      // accessed through an object instance
      // sp.MyGoodStaticProp = 5;
      
      // The following does not produce an error
      StaticProperty.MyGoodStaticProp = 5;

# Using Access Modifiers on Property Accessors

  1. Property accessors can be defined with their own access modifiers.

  2. If an accessor includes its own access modifier, this modifier overrides the access modifier of the property.

  3. The access modifier of an individual accessor must be more restrictive than the access modifier on the property itself.  

  4. For example, if the property has been defined as public, the individual accessor cannot be defined as global.

    * global virtual class PropertyVisibility {
      
        // X is private for read and public for write
        public integer X { private get; set; }

        // Y can be globally read but only written within a class
        global integer Y { get; public set; }
        
        // Z can be read within the class but only subclasses can set it
        public integer Z { get; protected set; }
      }