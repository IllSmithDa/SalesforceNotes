# Extending a class 

  1. A class that extends another class inherits all the methods and properties of the extended class. 

  2. In addition, the extending class can override the existing virtual methods by using the override keyword in the method definition.

  3. Overriding a virtual method allows you to provide a different implementation for an existing method.

  4. !This means that the behavior of a particular method is different based on the object you’re calling it on. This is referred to as polymorphism.

  5. A class extends another class using the extends keyword in the class definition.

  6. A class can only extend one other class, but it can implement more than one interface.

  7. This example shows how the YellowMarker class extends the Marker class. To run the inheritance examples in this section, first create the Marker class.

    * public virtual class Marker {
        public virtual void write() {
          System.debug('Writing some text.');
        }
    
        public virtual Double discount() {
          return .05;
        }
      }

  8. Then create the YellowMarker class, which extends the Marker class.

    * // Extension for the Marker class
      public class YellowMarker extends Marker {
          public override void write() {
              System.debug('Writing some text using the yellow marker.');
          } 
      }    

  9. This code segment shows polymorphism. The example declares two objects of the same type (Marker).\

    * Marker obj1, obj2;
      obj1 = new Marker();
      // This outputs 'Writing some text.'
      obj1.write();
      
      obj2 = new YellowMarker();
      // This outputs 'Writing some text using the yellow marker.'
      obj2.write();
      // We get the discount method for free even though it only exist on the marker class
      // and can call it from the YellowMarker instance.
      Double d = obj2.discount();
