# While loops 

  1. Will only execute if the condition is actually met
  
  Integer myCounter = 0;

  while (myCounter < 13 ) {
      myCounter++;
  }

# DO while loops 

  1. will always execute at least once then check the condition

  2. Use if you want to guarantee an execution of the code of at least once
    
    * do {
    
        runFunction1();
    
      } while(country = 'Canada');

# for loop 

  1. Iteration through an array usually 

    * for (Integer i = 0; i < array.size(); i++) {
        doSomething(array[i]);
      }

  2. Salesforce has its own for loop 

    * Integer[] myArray = new List<Integer> {1, 2, 4, 5, 6};

      for (Integer entryValue: myArray) {
          System.debug(entryValue);
      }