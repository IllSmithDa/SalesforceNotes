# Write SOSL Queries

  1. Salesforce Object Search Language (SOSL) is a Salesforce search language that is used to perform text searches in records. Use SOSL to search fields across multiple standard and custom object records in Salesforce.

  2. SOSL is similar to Apache Lucene.

  3. Adding SOSL queries to Apex is simple—you can embed SOSL queries directly in your Apex code. When SOSL is embedded in Apex, it is referred to as inline SOS

  4. This is an example of a SOSL query that searches for accounts and contacts that have any fields with the word 'SFDC'.

    * List<List<SObject>> searchList = [FIND 'SFDC' IN ALL FIELDS 
                                       RETURNING Account(Name), Contact(FirstName,LastName)];
    
# Differences and Similarities Between SOQL and SOSL

  1. Like SOQL, SOSL allows you to search your organization’s records for specific information. 
  
  2. Unlike SOQL, which can only query one standard or custom object at a time, a single SOSL query can search all objects.

  3. Another difference is that SOSL matches fields based on a word match while SOQL performs an exact match by default (when not using wildcards).

    * For example, searching for 'Digital' in SOSL returns records whose field values are 'Digital' or 'The Digital Company', but SOQL returns only records with field values of 'Digital'.

  4. SOQL and SOSL are two separate languages with different syntax. Each language has a distinct use case:

    * Use SOQL to retrieve records for a single object.

    * Use SOSL to search fields across multiple objects. SOSL queries can search most text fields on an object.

# Using the Query Editor

  1. The Developer Console provides the Query Editor console, which enables you to run SOSL queries and view results.

  2. The Query Editor provides a quick way to inspect the database.

  3. It is a good way to test your SOSL queries before adding them to your Apex code. 

  4. When you use the Query Editor, you need to supply only the SOSL statement without the Apex code that surrounds it.

  5. Let’s try running the following SOSL example: 

    * In the Developer Console, click the Query Editor tab.

    * Copy and paste the following into the first box under Query Editor, and then click Execute.

    * FIND {Wingo} IN ALL FIELDS RETURNING Account(Name), Contact(FirstName,LastName,Department)

      - Find field that has value 'Wingo'. If fonud in Account, return Name. If found in Contact, return first name, last name, and department.

      - All account and contact records in your org that satisfy the criteria will display in the Query Results section as rows with fields.

      - The results are grouped in tabs for each object (account or contact). The SOSL query returns records that have fields whose values match Wingo. Based on our sample data, only one contact has a field with the value Wingo, so this contact is returned.

# Basic SOSL Syntax

  1. SOSL allows you to specify the following search criteria:

    * Text expression (single word or a phrase) to search for

    * Scope of fields to search

    * List of objects and fields to retrieve

    * Conditions for selecting rows in the source objects

# This is the syntax of a basic SOSL query:

  1. FIND 'SearchQuery' [IN SearchGroup] [RETURNING ObjectsAndFields]

    * SearchQuery is the text to search for (a single word or a phrase)

    * Search terms can be grouped with logical operators (AND, OR) and parentheses

    * Search terms can include wildcard characters (*, ?).

    * The * wildcard matches zero or more characters at the middle or end of the search term.

    * The ? wildcard matches only one character at the middle or end of the search term.

    * SearchGroup is optional and can take one of the following values: 

      - ALL FIELDS

      - NAME FIELDS

      - EMAIL FIELDS

      - PHONE FIELDS

      - SIDEBAR FIELDS
    
    * ObjectsAndFields is optional.
      
      - It is the information to return in the search result—a list of one or more sObjects and, within each sObject, list of one or more fields, with optional values to filter against.

      - If not specified, the search results contain the IDs of all objects found. 

    * Text searches are case-insensitive. For example, searching for Customer, customer, or CUSTOMER all return the same results.

# Single Words and Phrases

  1. A SearchQuery contains two types of text:

    * Single Word — single word, such as test or hello. Words in the SearchQuery are delimited by spaces, punctuation, and changes from letters to digits (and vice-versa). Words are always case insensitive. 

    * Phrase — collection of words and spaces surrounded by double quotes such as "john smith". Multiple words can be combined together with logic and grouping operators to form a more complex query.

# SOSL Apex Example

  1. This example shows how to run a SOSL query in Apex. 
  
  2. This SOSL query combines two search terms by using the OR logical operator—it searches for Wingo or SFDC in any field. 

  3. This example returns all the sample accounts because they each have a field containing one of the words.

  4. The SOSL search results are returned in a list of lists. Each list contains an array of the returned records. 

    * List<List<sObject>> searchList = [FIND 'Wingo OR SFDC' IN ALL FIELDS 
                   RETURNING Account(Name),Contact(FirstName,LastName,Department)];

      Account[] searchAccounts = (Account[])searchList[0];
      Contact[] searchContacts = (Contact[])searchList[1];

      System.debug('Found the following accounts.');

      for (Account a : searchAccounts) {
          System.debug(a.Name);
      }

      System.debug('Found the following contacts.');

      for (Contact c : searchContacts) {
          System.debug(c.LastName + ', ' + c.FirstName);
      }
  
# More on SOSL Queries

  1. You can filter, reorder, and limit the returned results of a SOSL query. Because SOSL queries can return multiple sObjects, those filters are applied within each sObject inside the RETURNING clause.

  2. You can filter SOSL results by adding conditions in the WHERE clause for an object. For example, this results in only accounts whose industry is Apparel to be returned: RETURNING Account(Name, Industry WHERE Industry='Apparel')

  3. Likewise, ordering results for one sObject is supported by adding ORDER BY for an object. For example this causes the returned accounts to be ordered by the Name field: RETURNING Account(Name, Industry ORDER BY Name).

  4. The number of returned records can be limited to a subset of records. This example limits the returned accounts to 10 only: RETURNING Account(Name, Industry LIMIT 10)

  