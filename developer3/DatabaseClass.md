# Database Class 

  1. Bulk DML operations will fail to enter any record if even one of them are bad 

  2. Database classes allows you to enter good records while still dealing with bad records 

  3. Database.insert(accountList, false);

    * Setting the second parameter false will allow DML operations to continue for good records even when bad records are present'

  4. The return type of Database.insert() or Database.update() is Database.save();

    * Database.SaveResult[] srList = Database.insert(accountlist, false);

      - Second parameter is the rollback value which usually is true which means if one record is bad, none get inserted 

      - if rollback parameter is false, then the good records will get inserted and bad records will be handled later instead of preventing the entire batch from being inserted

    * for (Database.SaveResult sresult : srList) {
        if (sresult.isSuccess()) {
          // success message if everything goes well
          System.debug('account successly created: ' + sresult.getId()); }
        else {  
          for(Database.Error err : sresult.getErrors()) {  
            // error message for failed data entries
            System.debug(err.getStatusCode() + ': ' + err.getMessage()); 
            System.debug('Fields that have errors ' + err.getFields()); 
          } 
        }
      }

    * getError() - returns a list of the DB error objects listing with error code and description 

    * getID() - returns Ids of all the records you were trying to create or update 

    * is success() - returns a boolean to indicate if the DML op was sucessful or not.

# Transaction Control 

  1. Allows for savepoint creation in the code so at least some of the code you wrote will go through 
 
  2. savepoint sp = Database.setSavepoint();

    * Basic syntax for setting up a save point after you have made a dml statement 

    * e.g Account jackExample = new Account(name='Jack Example');
          insert jackExample
          savepoint saveJack Database.setSavepoint();

          Account sameAcc = [SELECT Name FROM Account WHERE Name='Jack Example'];
          sameAcc.Name = 'Mary Sue';
          update sameAcc;
          database.rollback(saveJack);

      - Even though name has been updated to Mary Sue, the rollback will revert the code back to the savepoint where account name is still Jack Example. 

  3. The rollback function is when the savepoint can be triggered allowing code to be rollbacked to the current savepoint.

# Savepoint Use Cases
  
  1. Sometimes during the processing of records, your business rules require that partial work (already executed DML statements) be “rolled back” so that the processing can continue in another direction. 
  
  2. Each rollback counts against the governor limit for DML statements. You will receive a runtime error if you try to rollback the database additional times.

# DML Options 

  1. Allows you to set options and configurations for DML operations

    * Database.DMLOptions optionName = new Database.DMLOptions();
    optionName.allowFieldTruncation = True;
  
# Relationship Query 

  1. Salesforce alternative to joined queries 

  2. No such thing as joined queries in Salesforce 

  3. Background:Account & Contact are related to each other using relationship field & account is primary & contact is secondary.

    * [SELECT id,name,(SELECT name FROM Account.Contacts)FROM Account LIMIT 5]
     
      - There is a lookup relationship between Account and Contacts

      - Here we fetch Accounts that have a contact name. If Account does not have a Contact name, it returns Account record with Contact name as null.

   