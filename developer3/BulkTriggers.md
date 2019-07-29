# Bulkified Triggers 

  1. Trigger Helper Class 

    * Best Practice Suggested Salesforce 

    * Whenever salesforce records changes, trigger will call out to one or multiple classes and the classes performs the logic. 

    * Logic never should be in the trigger itself

  2. All triggers are bulkified triggers and can handle thousands of records

  3. They use bulk idioms 

  4. Its all about iterating over the entire dataset

  5. Never desgin triggers for individual record but for bulk records because triggers need to handle multiple scenarios especially scenarios that involve bulk records 

    * trigger myTrigger on myObject__c (before insert) {

        Position[] positions = [SELECT Id FROM Position__c];

        for (myObject__c myobject: positions) {
            // run operation here
            MyClass.classFunc(positions)
        }
    }
      * For loop every object, get all positions and run the class methods

      * Note, never use SOQL queries or DML statements in the for loop as it will count against you in the governor limits and cause major problems for bulk data

  6. Number of SOQL queries per transactions is 100 

  7. Number of DML stataesments is 150 operations for one transaction

  8. Write update and insert triggers separately. 
  
  9. Never write more than one trigger per object as you won't know which will operate first and can cause recursion

  

# Recursion in Triggers

  1. A recursion calls either itself or another trigger which will callback the original trigger 

  2. Code is called repeatedly resulting in a infinite loop

  3. Trigger A caused by Object A updates Object B which activates Trigger B. Trigger B cause an update to Object A which activates Trigger A again. 

  4. Counter recursion using a trigger handler and static variables 

# Trigger Handler
  // helper class with a variable set to true by default
  1. public class rescursiveTriggerHandler {
      public static Boolean isFistRun = true;
  }

  2. trigger myTrigger on myObject__c (before insert) {

        // This condition will only ever be met once using a helper class
        if (rescursiveTriggerHandler.isFIrstRun) {
            rescursiveTriggerHandler.isFIrstRun = false;
            
            Position[] positions = [SELECT Id FROM Position__c];

            for (myObject__c myobject: positions) {
                // run operation here
                MyClass.classFunc(positions)
            }
        }
     }

# Add Error method

  1. Used for programming custom error messages and stop execution of a trigger 

  2. for (myObject__c myobject: positions) {
        // run operation here
        MyClass.classFunc(positions)
        if(positions.Salary__c == null) {
            positions.Salary__c.addError('Salary field must not be empty or null');
        }
     }

    