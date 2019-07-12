# What is Apex Trigger 

  1. It is a stored Apex procedure that is called whenever a record is inserted, updated or deleted or undeleted. 
  
    * If any change happens to a single or multiple records, the Apex trigger created on that object will be fired 

  2. Occurs after Process Builder, Apex triggers are preffered while implementing Business login in Salesforce

  4. Apex Triggers are specifically created for standard or custom objects

  5. Similar to Workflow rules but much more powerful


# Apex Triggers 

  2. In the Apex class you write your business logic and trigger determines when you execute your 
  business logic

  3. Apex can be invoked by using triggers. Apex triggers enable you to perform custom actions before or after changes to Salesforce records, such as insertions, updates, or deletions.

    * The act of firing SOQL query is what can activate a trigger

  4. Uses the .apxt

  5. You should only have 1 trigger for 1 object 

    * You can have more than 1 but no gaurantee that which will fire first 

    * Worse case scenario, trigger will fire other trigger back and forth creating a infinite loop of triggers

  6. You should only have 1 class for 1 trigger and that class is known as a trigger handler

  7. Triggers can handle up to 200 records at a time and process all the records one by one 

    * Workflow rule only works for 1 record at a time

    * They can handle bulk records 
 
    * More than 200, it will do it in batches with multiple executions

    * 500 records 

       - first execution: 200 records, second execution: 200 records, third execution: 100 records
  
# Two Types of Trigger

  1. Before triggers are used to update or validate record values before they’re saved to the database

    * Most of the time, triggers are occuring before they are saved to the database

  2. After triggers are used to access field values that are set by the system (such as a record's Id or LastModifiedDate field), and to affect changes in other records, such as logging into an audit table or firing asynchronous events with a queue. The records that fire the after trigger are read-only.

# Six types of trigger operations

  1. After determining trigger is before or after, there are four types of operations you can perform

    * insert

      - Trigger only occurs when you are inserting a new record not updating a old one

    * update

      - Trigger only occurs when you are updating an existing record

    * delete

      - Trigger only occurs when you are deleting an existing record

    * merge

      - merge triggers fire both before and after delete for the losing records, and both before and after update triggers for the winning record.

    * upsert 

      - upsert triggers fire both before and after insert or before and after update triggers as appropriate.

    * undelete

      - Triggers that execute after a record has been undeleted only work with specific objects. See Triggers and Recovered Records.

# Trigger syntax examples

  1. trigger discountTrigger on Pen__c (before insert) {
      PenClassDemonstration.applyDiscount(Trigger.new)
  }

    * Pen__c is the api name of the object in salesforce not class

    * PenClassDemonstration is the apex class

    * applyDiscount is the method belonging to the PenClassDemonstration

    * Trigger.new is a system variable where records will be saved

      - the lastest value represented here??

  2. trigger discountTrigger on Pen__c (before insert, before update) {
      PenClassDemonstration.applyDiscount(Trigger.new)
  }

  3. Trigger triggerName on ObjectName (triggerEvent) {
      // access class method here 
     }


# In real time, projects, we use context variables . Max possible times we will use 'Before' triggers and rarely 'After'

  1. trigger.new - for new records/ latest values

    * Returns a list of the new version of the sObject record 

    * Note it is only available in insert and update triggers and the record can only be modified in before triggers

  2. trigger.old - old records 

  3. trigger.isBefore - returns true if this trigger was fired before any record was saved 



# Trigger context variables 

  1. trigger.isExecuting


# Before trigger

  1. Can modify the record before it is saved to the database

  2. before triggers can be used to update and validate the same record that initiated the trigger before it is saved

  3. setting a discount trigger if amount is greater than 150 dollars

  4. All about saving and modifying the same objects 

# After Trigger

  1. Are executed after record is saved to the database

  2. After triggers can access field values that are set automatically the by the system (such as ID and LasModified fields)

    * IDs are created after the record is saved to the database so a after trigger is required to access them

  3. They are best if you want to effect changes in other object's records

  4. e.g insert a interviewer record and assign this interviewer a position as soon as position record is inserted

# Trigger and Order of Execution

  1. Load the orginal record or initialize on insert

  2. Overwrite the old record value with new values (if applicable)

  3. Execute All before triggers

  4. Re-run the system and user defined validation rules
  
  5. Save but do not commit the record to the database

    * Once commit, you cannot rollback

    * Only saved means, you can rollback

  6. Excute all the after triggers

  7. execute assignment rules

  8. auto response rules

  9. workflow rules

  10. workflow field updates 

  11. If record was updated using workflow rules, fire before and after trigger only one more time

  12. Execute flows and processes 

  13. Execute escalation rules

  14. Execute criteria based sharing rules

  15. Commit DML operation to the database

  16. Executes post-commit logic, such as sending email.

