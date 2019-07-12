# SOQL Query

  1. Basic Example

    * [SELECT Name, Id FROM Account Where city='San Francisco']

    * [SELECT LastName, FistName FROM Bank_Account__c where amount__v >= '100000']

      - Note you can use greater or less than 

      - also can use >, < , = , <=, >=, !=

      - [SELECT Name from Contact WHERE number != null];

  2. String based queries are written in string form and passes as a parameter to DV query to be executed 

  3. Queries can return the following 3 types of data 

    * list of objects 

    * single object 

    * integer 

  4. Works for standard and custom objects in the database. 

  5. Queries defined as a set of keywords that we need to properly with help of few object names as well as conditional statements

# SOQL complex example

  1. SELECT Id, Name from Contact WHERE birthday=Today AND Height__c > 100 
    AND ((Phone=null  AND DoNotCall=False AND Phone like '0111%') OR email=null)
    ORDER BY Name 
    LIMIT 50
    OFFSET 10

    * When you use LIMIT, the 50 that will show by default are by the most recently modified records first 

    * OFFSET must come after LIMIT 

    * OFFSET skips the specified number of records initially returned

  

   