# Manipulate Records with DML

  1. Create and modify records in Salesforce by using the Data Manipulation Language, abbreviated as DML

  2. DML provides a straightforward way to manage records by providing simple statements to insert, update, merge, delete, and restore records.

  3. Because Apex is a data-focused language and is saved on the Lightning Platform, it has direct access to your data in Salesforce.
  
  4. By calling DML statements, you can quickly perform operations on your Salesforce records 

  5. An account sObject is created first and then passed as an argument to the insert statement, which persists the record in Salesforce

    * Create the account sObject 

      -  Account acct = new Account(Name='Acme', Phone='(415)555-1212', NumberOfEmployees=100);
    
    * Insert the account by using DML
      
      - insert acct;

  6. The following DML statements are available.

    * insert
    
    * update
    
    * upsert
    
    * delete
    
    * undelete
    
    * merge

  7. Each DML statement accepts either a single sObject or a list (or array) of sObjects. Operating on a list of sObjects is a more efficient way for processing records.

  8. The upsert DML operation creates new records and updates sObject records within a single statement, using a specified field to determine the presence of existing objects, or the ID field if no field is specified.

  9. The merge statement merges up to three records of the same sObject type into one of the records, deleting the others, and re-parenting any related records.

# ID Field Auto-Assigned to New Records

  1. When inserting records, the system assigns an ID for each record. 

  2.  In addition to persisting the ID value in the database, the ID value is also autopopulated on the sObject variable that you used as an argument in the DML call.

  3. This example shows how to get the ID on the sObject that corresponds to the inserted account.

    * Create the account sObject 
      
      - Account acct = new Account(Name='Acme', Phone='(415)555-1212', NumberOfEmployees=100);
    
    * Insert the account by using DML
      
      - insert acct;

    * Get the new ID on the inserted sObject argument
      
      - ID acctID = acct.Id;
    
    * Display this ID in the debug log
      
      - System.debug('ID = ' + acctID);

      - Debug log result (the ID will be different in your case)
    
      - DEBUG|ID = 001D000000JmKkeIAF

    * Because the sObject variable in the example contains the ID after the DML call, you can reuse this sObject variable to perform further DML operations, such as updates, as the system will be able to map the sObject variable to its corresponding record by matching the ID.

    * You can retrieve a record from the database to obtain its fields, including the ID field, but this can’t be done with DML. You’ll need to write a query by using SOQL. You’ll learn about SOQL in another unit.

# Bulk DML

  1. You can perform DML operations either on a single sObject, or in bulk on a list of sObjects. Performing bulk DML operations is the recommended way because it helps avoid hitting governor limits, such as the DML limit of 150 statements per Apex transaction

  2. This limit is in place to ensure fair access to shared resources in the Lightning Platform. Performing a DML operation on a list of sObjects counts as one DML statement, not as one statement for each sObject

  4. // Create a list of contacts
     List<Contact> conList = new List<Contact> {
         new Contact(FirstName='Joe',LastName='Smith',Department='Finance'),
             new Contact(FirstName='Kathy',LastName='Smith',Department='Technology'),
             new Contact(FirstName='Caroline',LastName='Roth',Department='Finance'),
             new Contact(FirstName='Kim',LastName='Shain',Department='Education')};
                 
     // Bulk insert all contacts with one DML call
     insert conList;

     // List to hold the new contacts to update
     List<Contact> listToUpdate = new List<Contact>();
     // Iterate through the list and add a title only
     //   if the department is Finance
     for(Contact con : conList) {
         if (con.Department == 'Finance') {
             con.Title = 'Financial analyst';
             // Add updated contact sObject to the list.
             listToUpdate.add(con);
         }
     }
     // Bulk update all contacts with one DML call
     update listToUpdate;

# Upserting Records

  1. If you have a list containing a mix of new and existing records, you can process insertions and updates to all records in the list by using the upsert statement

  2. Upsert helps avoid the creation of duplicate records and can save you time as you don’t have to determine which records exist first.

  3. The upsert statement matches the sObjects with existing records by comparing values of one field. If you don’t specify a field when calling this statement, the upsert statement uses the sObject’s ID to match the sObject with existing records in Salesforce

  4. Alternatively, you can specify a field to use for matching. For custom objects, specify a custom field marked as external ID

  5. Upsert Syntax

    * upsert sObject | sObject[]

    * upsert sObject | sObject[]​​ field

  6. The optional field is a field token 

    * upsert sObjectList Account.Fields.MyExternalId;

      - Upsert uses the sObject record's primary key (the ID), an idLookup field, or an external ID field to determine whether it should create a new record or update an existing one:

      - If the key is not matched, a new object record is created.
    
      - If the key is matched once, the existing object record is updated.
       
      - If the key is matched multiple times, an error is generated and the object record is neither inserted or updated.

  7. This example shows how upsert updates an existing contact record and inserts a new contact in one call. This upsert call updates the existing Josh contact and inserts a new contact, Kathy.

    * // Insert the Josh contact
      Contact josh = new Contact(FirstName='Josh',LastName='Kaplan',Department='Finance');       
      insert josh;

      // Josh's record has been inserted
      //   so the variable josh has now an ID
      //   which will be used to match the records by upsert
      josh.Description = 'Josh\'s record has been updated by the upsert operation.';

      // Create the Kathy contact, but don't persist it in the database
      Contact kathy = new Contact(FirstName='Kathy',LastName='Brown',Department='Technology');

      // List to hold the new contacts to upsert
      List<Contact> contacts = new List<Contact> { josh, kathy };

      // Call upsert
      upsert contacts;
      // Result: Josh is updated and Kathy is created.

  8. Alternatively, you can specify a field to be used for matching records. This example uses the Email field on Contact because it has idLookup property set.

    * Contact jane = new Contact(FirstName='Jane',
                         LastName='Smith',
                         Email='jane.smith@example.com',
                         Description='Contact of the day');
      insert jane;

      // 1. Upsert using an idLookup field
      // Create a second sObject variable.
      // This variable doesn’t have any ID set.
      Contact jane2 = new Contact(FirstName='Jane',
                               LastName='Smith',  
                               Email='jane.smith@example.com',
                               Description='Prefers to be contacted by email.');

      // Upsert the contact by using the idLookup field for matching.
      upsert jane2 Contact.fields.Email;

      // Verify that the contact has been updated
      System.assertEquals('Prefers to be contacted by email.',
                         [SELECT Description FROM Contact WHERE Id=:jane.Id].Description);

# Deleting Records

  1. You can delete persisted records using the delete statement. 
  
  2. Deleted records aren’t deleted permanently from Lightning Platform, but they’re placed in the Recycle Bin for 15 days from where they can be restored.

  3. This example shows how to delete all contacts whose last name is Smith.

    * Contact[] contactsDel = [SELECT Id FROM Contact WHERE LastName='Smith']; 
      delete contactsDel;

# DML Statement Exceptions

  1. If a DML operation fails, it returns an exception of type DmlException. You can catch exceptions in your code to handle error conditions.

  2. This example produces a DmlException because it attempts to insert an account without the required Name field. The exception is caught in the catch block.

    * try {\

      // This causes an exception because 
      // the required Name field is not provided.
      Account acct = new Account();

      // Insert the account 
      insert acct;

    } catch (DmlException e) {

        System.debug('A DML exception has occurred: ' +
                    e.getMessage());
    }

# Database Methods

  1. Apex contains the built-in Database class, which provides methods that perform DML operations and mirror the DML statement counterparts.

  2. These Database methods are static and are called on the class name.

    * Database.insert()

    * Database.update()

    * Database.upsert()

    * Database.delete()

    * Database.undelete()

    * Database.merge()

  3. Unlike DML statements, Database methods have an optional allOrNone parameter that allows you to specify whether the operation should partially succeed

  4.  When this parameter is set to false, if errors occur on a partial set of records, the successful records will be committed and errors will be returned for the failed records. Also, no exceptions are thrown with the partial success option.

    * This is how you call the insert method with the allOrNone set to false.
    
      - Database.insert(recordList, false);

    * The Database methods return result objects containing success or failure information for each record. For example, insert and update operations each return an array of Database.SaveResult objects.

      - Database.SaveResult[] results = Database.insert(recordList, false);

      - Upsert returns Database.UpsertResult objects, and delete returns Database.DeleteResult objects.

    * By default, the allOrNone parameter is true, which means that the Database method behaves like its DML statement counterpart and will throw an exception if a failure is encountered.

    * The following two statements are equivalent to the insert recordList; statement.

      - Database.insert(recordList);

      - Database.insert(recordList, true);

  5.  This example is based on the bulk DML example, but replaces the DML statement with a Database method. The Database.insert() method is called with the partial success option. One contact in the list doesn’t have any fields on purpose and will cause an error because the contact can’t be saved without the required LastName field. Three contacts are committed and the contact without any fields generates an error. The last part of this example iterates through the returned results and writes debug messages to the debug log.

    * // Create a list of contacts
      List<Contact> conList = new List<Contact> {
              new Contact(FirstName='Joe',LastName='Smith',Department='Finance'),
              new Contact(FirstName='Kathy',LastName='Smith',Department='Technology'),
              new Contact(FirstName='Caroline',LastName='Roth',Department='Finance'),
              new Contact()};
                  
      // Bulk insert all contacts with one DML call
      Database.SaveResult[] srList = Database.insert(conList, false);

      // Iterate through each returned result
      for (Database.SaveResult sr : srList) {
          if (sr.isSuccess()) {

              // Operation was successful, so get the ID of the record that was processed
              System.debug('Successfully inserted contact. Contact ID: ' + sr.getId());

          } else {

              // Operation failed, so get all errors
              for(Database.Error err : sr.getErrors()) {
                  System.debug('The following error has occurred.');
                  System.debug(err.getStatusCode() + ': ' + err.getMessage());
                  System.debug('Contact fields that affected this error: ' + err.getFields());
      	      }
          }
      }

# Should You Use DML Statements or Database Methods?

  1. Use DML statements if you want any error that occurs during bulk DML processing to be thrown as an Apex exception that immediately interrupts control flow (by using try. . .catch blocks). This behavior is similar to the way exceptions are handled in most database procedural languages. 

  2. Use Database class methods if you want to allow partial success of a bulk DML operation—if a record fails, the remainder of the DML operation can still succeed. 

    * Your application can then inspect the rejected records and possibly retry the operation. 

    * When using this form, you can write code that never throws DML exception errors.

    * Instead, your code can use the appropriate results array to judge success or failure. Note that Database methods also include a syntax that supports thrown exceptions, similar to DML statements. 

# Working with Related Records

  1. Inserting Related Records

    * You can insert records related to existing records if a relationship has already been defined between the two objects, such as a lookup or master-detail relationship.

    * A record is associated with a related record through a foreign key ID. 

      - For example, if inserting a new contact, you can specify the contact's related account record by setting the value of the AccountId field.

  2. This example shows how to add a contact to an account (the related record) by setting the AccountId field on the contact.

    * Account acct = new Account(Name='SFDC Account');
      insert acct;
      
      // Once the account is inserted, the sObject will be 
      // populated with an ID.
      // Get this ID.
      ID acctID = acct.ID;
 
      // Add a contact to this account.
      Contact mario = new Contact(
          FirstName='Mario',
          LastName='Ruiz',
          Phone='415.555.1212',
          AccountId=acctID);
      insert mario; 

# Updating Related Records

  1. Fields on related records can't be updated with the same call to the DML operation and require a separate DML call. 

    * For example, if inserting a new contact, you can specify the contact's related account record by setting the value of the AccountId field.

    * However, you can't change the account's name without updating the account itself with a separate DML call.

    * Similarly, when updating a contact, if you also want to update the contact’s related account, you must make two DML calls. 

  2. The following example updates a contact and its related account using two update statements.

     * // Query for the contact, which has been associated with an account.
       Contact queriedContact = [SELECT Account.Name 
                                 FROM Contact 
                                 WHERE FirstName = 'Mario' AND LastName='Ruiz'
                                 LIMIT 1];

       // Update the contact's phone number
       queriedContact.Phone = '(415)555-1213';

       // Update the related account industry
       queriedContact.Account.Industry = 'Technology';
       
       // Make two separate calls 
       // 1. This call is to update the contact's phone.
       update queriedContact;
       
       // 2. This call is to update the related account's Industry field.
       update queriedContact.Account;       
      
# Deleting Related Records

  1. The delete operation supports cascading deletions. If you delete a parent object, you delete its children automatically, as long as each child record can be deleted. 

  2. For example, deleting the account you created earlier (SFDC Account) will delete its related contact too.

    * Account[] queriedAccounts = [SELECT Id FROM Account WHERE Name='SFDC Account'];
      delete queriedAccounts;

# About Transactions

  1. DML operations execute within a transaction.

  2. All DML operations in a transaction either complete successfully, or if an error occurs in one operation, the entire transaction is rolled back and no data is committed to the database.

  3. The boundary of a transaction can be a trigger, a class method, an anonymous block of code, an Apex page, or a custom Web service method.

    * For example, if a trigger or class creates two accounts and updates one contact, and the contact update fails because of a validation rule failure, the entire transaction rolls back and none of the accounts are persisted in Salesforce.