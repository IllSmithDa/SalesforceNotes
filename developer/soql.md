# SOQL

  1. To read a record from Salesforce, you need to write a query.  

  2. Salesforce provides the Salesforce Object Query Language, or SOQL in short, that you can use to read saved records. SOQL is similar to the standard SQL language but is customized for the Lightning Platform. 

  3. Because Apex has direct access to Salesforce records that are stored in the database, you can embed SOQL queries in your Apex code and get results in a straightforward fashion.

  4. When SOQL is embedded in Apex, it is referred to as inline SOQL.

  5. To include SOQL queries within your Apex code, wrap the SOQL statement within square brackets and assign the return value to an array of sObjects 

    *  For example, the following retrieves all account records with two fields, Name and Phone, and returns an array of Account sObjects.

      - Account[] accts = [SELECT Name,Phone FROM Account];

# Using the Query Editor

  1. The Developer Console provides the Query Editor console, which enables you to run your SOQL queries and view results

  2. The Query Editor provides a quick way to inspect the database. It is a good way to test your SOQL queries before adding them to your Apex code. 

  3. When you use the Query Editor, you need to supply only the SOQL statement without the Apex code that surrounds it.

  4. Let’s try running the following SOQL example: 

    * In the Developer Console, click the Query Editor tab.

    * Copy and paste the following into the first box under Query Editor, and then click Execute.

      - SELECT Name,Phone FROM Account

      - All account records in your org appear in the Query Results section as rows with fields.

# Basic SOQL Syntax

  1. SELECT fields FROM ObjectName [WHERE Condition]

  2. The WHERE clause is optional.
    
    * For example, the following query retrieves accounts and gets two fields for each account: the ID and the Phone.

      - SELECT Name,Phone FROM Account

      - SELECT Name,Phone: This part lists the fields that you would like to retrieve. The fields are specified after the SELECT keyword in a comma-delimited list. Or you can specify only one field, in which case no comma is necessary (e.g. SELECT Phone).

      - FROM Account: This part specifies the standard or custom object that you want to retrieve. In this example, it’s Account. For a custom object called Invoice_Statement, it is Invoice_Statement__c.

  3. Unlike other SQL languages, you can’t specify * for all fields. 
    
    * You must specify every field you want to get explicitly. 
    
    * If you try to access a field you haven’t specified in the SELECT clause, you’ll get an error because the field hasn’t been retrieved. 

  4. You don’t need to specify the Id field in the query as it is always returned in Apex queries, whether it is specified in the query or not.

    * For example: SELECT Id,Phone FROM Account and SELECT Phone FROM Account are equivalent statements. 

    * The only time you may want to specify the Id field if it is the only field you’re retrieving because you have to list at least one field: SELECT Id FROM Account

  5. You may want to specify the Id field also when running a query in the Query Editor as the ID field won’t be displayed unless specified.

# Filtering Query Results with Conditions

  1. If you want to limit the accounts returned to accounts that fulfill a certain condition, you can add this condition inside the WHERE clause.

  2. The following example retrieves only the accounts whose names are SFDC Computing. Note that comparisons on strings are case-insensitive.

    * SELECT Name,Phone FROM Account WHERE Name='SFDC Computing'

  3. The WHERE clause can contain multiple conditions that are grouped by using logical operators (AND, OR) and parentheses. For example, this query returns all accounts whose name is SFDC Computing that have more than 25 employees:

    * SELECT Name,Phone FROM Account WHERE (Name='SFDC Computing' AND NumberOfEmployees>25)

  4. This is another example with a more complex condition. This query returns all SFDC Computing accounts, or all accounts with more than 25 employees whose billing city is Los Angeles.

    * SELECT Name,Phone FROM Account WHERE (Name = 'SFDC Computing' OR ( NumberOfEmployees > 25 AND BillingCity = 'Los Angeles'))

  5. Instead of using the equal operator (=) for comparison, you can perform fuzzy matches by using the LIKE operator. 

    *  For example, you can retrieve all accounts whose names start with SFDC by using this condition: WHERE Name LIKE 'SFDC%'

  6. The % wildcard character matches any or no character. 
  
  7. The _ character in contrast can be used to match just one character.

# Ordering Query Results

  1. When a query executes, it returns records from Salesforce in no particular order, so you can’t rely on the order of records in the returned array to be the same each time the query is run

  2. You can however choose to sort the returned record set by adding an ORDER BY clause and specifying the field by which the record set should be sorted. 

    * This example sorts all retrieved accounts based on the Name field. 

        - SELECT Name,Phone FROM Account ORDER BY Name

    * The default sort order is in alphabetical order, specified as ASC. The previous statement is equivalent to:

        - SELECT Name,Phone FROM Account ORDER BY Name ASC

    * To reverse the order, use the DESC keyword for descending order:

        - SELECT Name,Phone FROM Account ORDER BY Name DESC

  3. You can sort on most fields, including numeric and text fields. You can’t sort on fields like rich text and multi-select picklists

# Limiting the Number of Records Returned

  1. You can limit the number of records returned to an arbitrary number by adding the LIMIT n clause where n is the number of records you want returned

  2. For example, this query retrieves the first account that is returned. Notice that the returned value is one account and not an array when using LIMIT 1

    * SELECT Name,Phone FROM Account 
                  WHERE (Name = 'SFDC Computing' AND NumberOfEmployees>25)
                  ORDER BY Name
                  LIMIT 10

    * Execute the following SOQL query in Apex by using the Execute Anonymous window in the Developer Console. Then inspect the debug statements in the debug log. One sample account should be returned.

      - Account[] accts = [SELECT Name,Phone FROM Account 
                   WHERE (Name='SFDC Computing' AND NumberOfEmployees>25)
                   ORDER BY Name
                   LIMIT 10];

        System.debug(accts.size() + ' account(s) returned.');

        // Write all account array info
        System.debug(accts);

# Accessing Variables in SOQL Queries

  1. SOQL statements in Apex can reference Apex code variables and expressions if they are preceded by a colon (:). The use of a local variable within a SOQL statement is called a bind.

  2. This example shows how to use the targetDepartment variable in the WHERE clause.

    * String targetDepartment = 'Wingo';
      Contact[] techContacts = [SELECT FirstName,LastName 
                               FROM Contact WHERE Department=:targetDepartment];

# Querying Related Records

  1. Records in Salesforce can be linked to each other through relationships: lookup relationships or master-detail relationships.

    * For example, the Contact has a lookup relationship to Account. When you create or update a contact, you can associate it with an account. The contacts that are associated with the same account appear in a related list on the account’s page.

  2. In the same way you can view related records in the Salesforce user interface, you can query related records in SOQL.

  3. To get child records related to a parent record, add an inner query for the child records. The FROM clause of the inner query runs against the relationship name, rather than a Salesforce object name. 

  4. This example contains an inner query to get all contacts that are associated with each returned account. The FROM clause specifies the Contacts relationship, which is a default relationship on Account that links accounts and contacts.

    * SELECT Name, (SELECT LastName FROM Contacts) FROM Account WHERE Name = 'SFDC Computing'

  5. This next example embeds the example SOQL query in Apex and shows how to get the child records from the SOQL result by using the Contacts relationship name on the sObject.

    * Account[] acctsWithContacts = [SELECT Name, (SELECT FirstName,LastName FROM Contacts)
                               FROM Account 
                               WHERE Name = 'SFDC Computing'];

      // Get child records
      Contact[] cts = acctsWithContacts[0].Contacts;
      System.debug('Name of first associated contact: ' 
                   + cts[0].FirstName + ', ' + cts[0].LastName);

  6. You can traverse a relationship from a child object (contact) to a field on its parent (Account.Name) by using dot notation. 

    * For example, the following Apex snippet queries contact records whose first name is Carol and is able to retrieve the name of Carol’s associated account by traversing the relationship between accounts and contacts.

      - Contact[] cts = [SELECT Account.Name FROM Contact 
                 WHERE FirstName = 'Carol' AND LastName='Ruiz'];
        Contact carol = cts[0];
        String acctName = carol.Account.Name;
        System.debug('Carol\'s account name is ' + acctName);

# Querying Record in Batches By Using SOQL For Loops

  1. With a SOQL for loop, you can include a SOQL query within a for loop. 

  2. The results of a SOQL query can be iterated over within the loop. SOQL for loops use a different method for retrieving records—records are retrieved using efficient chunking with calls to the query and queryMore methods of the SOAP API. 
  
  3. By using SOQL for loops, you can avoid hitting the heap size limit.

  4. SOQL for loops iterate over all of the sObject records returned by a SOQL query. The syntax of a SOQL for loop is either:

    * for (variable : [soql_query]) {
        code_block
      }

    * for (variable_list : [soql_query]) {
        code_block
      }
    
      - Both variable and variable_list must be of the same type as the sObjects that are returned by the soql_query.

  5. It is preferable to use the sObject list format of the SOQL for loop as the loop executes once for each batch of 200 sObjects. Doing so enables you to work on batches of records and perform DML operations in batch, which helps avoid reaching governor limits.
  
    * insert new Account[]{new Account(Name = 'for loop 1'), 
                     new Account(Name = 'for loop 2'), 
                     new Account(Name = 'for loop 3')};

      // The sObject list format executes the for loop once per returned batch
      // of records
      Integer i=0;
      Integer j=0;

      for (Account[] tmp : [SELECT Id FROM Account WHERE Name LIKE 'for loop _']) {
          j = tmp.size();
          i++;
      }

      System.assertEquals(3, j); // The list should have contained the three accounts
                             // named 'yyy'
                             
      System.assertEquals(1, i); // Since a single batch can hold up to 200 records and,
                             // only three records should have been returned, the 
                             // loop should have executed only once      