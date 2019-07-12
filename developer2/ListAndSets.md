# Definitions

  1. Lists

    * A list is an ordered collection of elements that are distinguished by their indices. 
    
    * List elements can be of any data type—primitive types, collections, sObjects, user-defined types, and built-in Apex types.

    * Index of entry is its numeric location

    * You can set a particular value at a particular index using set funciton

      - myArray.set(0, 'candy')

      - changes the value of index 0 in myArray to candy;

  2. Sets 

    * A set is an unordered collection of elements that do not contain any duplicates.

      - No need to sort as it does get sorted automatically

    * Set elements can be of any data type—primitive types, collections, sObjects, user-defined types, and built-in Apex types.

    * No index format 

    * You can use assert function to check if a value is in the array

      - System.assert(mySet.contains(1));
      - check if the value 1 exists in the set
      
    * You can remove a value from the set using remove funciton

      - mySet.remove(1);

    * Creating a set from another set 

      - Set<Integer> mySet = new Set<Integer>();
        Set<Integer> mySet2 = new Set<Integer>(mySet);

  3. Maps

    * A map is a collection of key-value pairs where each unique key maps to a single value

    * Keys and values can be any data type—primitive types, collections, sObjects, user-defined types, and built-in Apex types.

    * !Keys must be unique but values do not

    * e.g Map<String, String> country_currencies = new Map<String, String>();
          Map<ID, Set<String>> m = new Map<ID, Set<String>>();

      - first String represents key and second String represents value

      - keys
    
    * Map<String, String> MyStrings = new Map<String, String>{'a' => 'b', 'c' => 'd'.toUpperCase()};

      - performs a function on MyStrings

    * put function enters a key value pair 

      - Map<Integer, String> m = new Map<Integer, String>(); // Define a new map
        m.put(1, 'First entry');                  // Insert a new key-value pair in the map
        m.put(2, 'Second entry');                  // Insert a new key-value pair in the map
        System.assert(m.containsKey(1));  // Assert that the map contains a key
        String value = m.get(2);               // Retrieve a value, given a particular key
        System.assertEquals('Second entry', value);
        Set<Integer> s = m.keySet();       // Return a set that contains all of the keys in the map

      - get() will return null if no value exists at a certain key

      - Map<Integer, Class__c > myMap = new Map<Integer, Class_c>();
        Class__c myObject = new Class__c(name='Joe', age=12);
        myMap.put(myObject);
        System.debug('This is my object ' + myObject);

  4. Apex, in general, is a statically-typed programming language, which means users must specify the data type for a variable before that variable can be used.

  5. You can sort the array or list using either a the sort function sort() or using a sorting algorithmn

# Initialzing a list

  1. List<String> colors = new List<String>();
        
# Initializing an array
        
  1. Integer[] cruiserSpeeds = new List<Integer>();
        
  2. Difference is in the left side of the operation

  3. You can go either List<String> or String[]
        
# Create a list of elements
        
  1. List<String> cars = new List<String>{'Toyota', 'Mazda', 'Ford', 'Mercedes'};

  2. works exactly the same for arrays
        
    * Long[] planetDistance = new List<Long>{1000000000390L, 4959000993200L, 129992390999L};
        
      - Long is a 64bit number that doesn't include decimal. 
    
      - This is used when we need a range of values wider than those provided by Integer.    
            
  3. You can add elements into array
    
    * cars.add('Dodge');
        
  4. get an element from the list which in this case is 0
        
    * String favBrand = cars.get(0);
       
  5. preferred way getting an element as it is similar to javascript method getting elements
    
    * String favBrand2 = cars[0];
        
    * System.debug(favBrand);
        
  6. iterate over the array
        
    * for (Integer i = 0; i < cars.size(); i++) {
        System.debug(cars[i]);
      }

# Salesforce iterating over list/set


  1. set<Integer> mySet = New set<Integer>{4, 3, 2};
     mySet.add(1)

    * Remember set has not index so iterate using salesforce iteration  

    * for (integer i : mySet) {
        System.debug(i)
      }
    
  2. Loop SOQL query

    * for (Object__c objectName: [SELECT Id from Object__c]) {
        System.debug(objectName)
      }

