# APEX INTRO

  1. Based on Object oriented programming

  2. strongly typed 

  3. compiled 

  4. highly scalable 

  5. template based language similar to java 

  6. First language that runs completely on the web browser

# Debug log 

  1. Must be checked at the bottom right in order for log to appear after you execute the code

  2. You can select debug only or executable only

  3. It will list limits as well 

# Executing on Developer Console

  1. You can execute line of code you highlighted only by clicking execute highlight button

# DML Operation (Data manipulation)

  1. You have to declare a subject variable of the type record/object that you are going to insert 

    * e.g int varaible1, string stringName;

  2. Using SOQL Query which will make calls to the database

    * INSERT will insert data into the Salesforce database 

  3. Account accountInstance = new Account(Name='Bob the Builder');

    * instantiating an instance of an account and trying to create a new Account record 

  4. Insert accountInstance

    * inserts the actual account instance into Salesforce 

  5. SELECT methods 

    * Used to find a record using a SOQL qeury 

      - e.g Account myAccount = [SELECT Id, Name from Account WHERE Name like 'account name%']

    * e.g StudentMaster__c student = SELECT  Id, Name FROM StudenMaster__c WHERE mailID__c = 'bob@akidevcom'

      - ID and Name will be fetched from the database and will match by the the mail ID

# Database 

  1. Database.insert()

    * Unlike DML statements, Database methods have an optional allOrNone parameter that allows you to specify whether the operation should partially succeed. 
    
    * When this parameter is set to false, if errors occur on a partial set of records, the successful records will be committed and errors will be returned for the failed records. 
    
    * Also, no exceptions are thrown with the partial success option.
    
    * Database.insert(recordList, false);

    * DML statements like insert has a limit of 150 a day

      - also called Governor limits allows for multitenancy or multiple businesses to run on the same cloud
    
      - record ID which is unique to each entry is generated automatically when record is inserted into the database

      - look up field or any custom fields ending __c will automatically return the Id even if you don't specifically indicate you are looking for ID. 
    
# Apex and Visual Force use cases 

  1. Ajax can be used in Apex 

  2. For scenario where we need roll up summary but because we don't have a master detail relationship, we are not allowed to use roll up summary. ( e.g we only have look up relationship)

  3. workflow field update - it can only update the field of the record on which the rule is executing

