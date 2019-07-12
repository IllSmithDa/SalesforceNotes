# Trigger Context Variables
  
  1. Changes to a simple or multiple records of a particular object that might invoke a trigger are recognized and controlled via Trigger context variables

  2. Variables include 

    * isExecuting - returns true if the current context for Apex code is a trigger

    * isInsert - Returns true if Trigger was fired due to an insert operation 

    * isUpdate - Returns true if trigger was fired due to a update operation 

    * isDelete - return true if trigger was fired due to a delete operations

    * Trigger.new - returns the list of new version of sObject records 

    * newMap - a maps of IDs to the new versions of sObject records 

# Trigger Helper Class Pattern 

  1. Salesforce record changes 

  2. Trigger calls out to one or multiple classes 

    * Best practice is to have one class 

    * Class performs the logic 
  
    * Trigger should never perform the actual logic only determin when and which scenario logic in the class should run

    * Only one trigger should be active per object  

# Bulkified Triggers 

  1. Used for triggers designed to handle thousands of records 

  2. extensively uses sets, arrays, lists and maps 

# Recursion in Triggers 

  1. When multiple triggers accross multiple object are involved, you can sometimes end up with infinite loop where triggers will fire infinitely

# Validations 

  1. Triggers can be used to create validation rules and display error when validation rule failed to be met 

# Triggers and order of execution 

  1. Record is process of being saved to the database 

  2. First validation rules will be fired 

  3. Then trigger before the event 

  4. after the record id is gernerated, the standard fields are available so that you can use these values and relate this record to another parent or child record 

  5. Roll up summary executed the amount save is hit but later the record does not get saved due to same validation error. Roll up summary will always execute last after all data has been commited 

  6. Multiple workflow rules or triggers can cause chaos because there is no guarantee which one will fire first and in worse case scenario, a recursion which can be worked around using static variables