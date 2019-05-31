# Bulk Trigger Design Patterns

  1. Apex triggers are optimized to operate in bulk

  2. We recommend using bulk design patterns for processing records in triggers.

  3. When you use bulk design patterns, your triggers have better performance, consume less server resources, and are less likely to exceed platform limits.

  4. The benefit of bulkifying your code is that bulkified code can process large numbers of records efficiently and run within governor limits on the Lightning Platform. 

  5. These governor limits are in place to ensure that runaway code doesn’t monopolize resources on the multitenant platform.

# Operating on Record Sets

  1. Bulkified triggers operate on all sObjects in the trigger context.

  2. Typically, triggers operate on one record if the action that fired the trigger originates from the user interface.

  3. But if the origin of the action was bulk DML or the API, the trigger operates on a record set rather than one record. 

    * For example, when you import many records via the API, triggers operate on the full record set.

    * Therefore, a good programming practice is to always assume that the trigger operates on a collection of records so that it works in all circumstances

    * The following trigger assumes that only one record caused the trigger to fire.

      - trigger MyTriggerNotBulk on Account(before insert) {
          
          Account a = Trigger.New[0];
          a.Description = 'New description';
        
        }
        
    * This example is a modified version of MyTrigger. It uses a for loop to iterate over all available sObjects. This loop works if Trigger.New contains one sObject or many sObjects.

      - trigger MyTriggerBulk on Account(before insert) {

          for(Account a : Trigger.New) {
              a.Description = 'New description';
          }

        }

# Performing Bulk SOQL

  1. SOQL queries can be powerful. You can retrieve related records and check a combination of multiple conditions in one query. 

  2.  By using SOQL features, you can write less code and make fewer queries to the database. 
    
    * Making fewer database queries helps you avoid hitting query limits, which are 100 SOQL queries for synchronous Apex or 200 for asynchronous Apex.

  3. The example makes a SOQL query inside a for loop to get the related opportunities for each account, which runs once for each Account sObject in Trigger.New. If you have a large list of accounts, a SOQL query inside a for loop could result in too many SOQL queries.

    * trigger SoqlTriggerNotBulk on Account(after update) {   
  
        for(Account a : Trigger.New) {
          
            // Get child records for each account
            // Inefficient SOQL query as it runs once for each account!
            Opportunity[] opps = [SELECT Id,Name,CloseDate 
                                 FROM Opportunity WHERE AccountId=:a.Id];
            
            // Do some other processing
        }
      }

  4. This example is a modified version of the previous one and shows a best practice for running SOQL queries. The SOQL query does the heavy lifting and is called once outside the main loop.

    * trigger SoqlTriggerBulk on Account(after update) {  

        // Perform SOQL query once.    
        // Get the accounts and their related opportunities.
        List<Account> acctsWithOpps = 
            [SELECT Id,(SELECT Id,Name,CloseDate FROM Opportunities) 
             FROM Account WHERE Id IN :Trigger.New];
      
        // Iterate over the returned accounts    
        for(Account a : acctsWithOpps) { 
            Opportunity[] relatedOpps = a.Opportunities;  
            // Do some other processing
        }
      }

      - The SOQL query uses an inner query—(SELECT Id FROM Opportunities)—to get related opportunities of accounts.

      - The SOQL query is connected to the trigger context records by using the IN clause and binding the Trigger.New variable in the WHERE clause—WHERE Id IN :Trigger.New. This WHERE condition filters the accounts to only those records that fired this trigger.

      - Combining the two parts in the query results in the records we want in one call: the accounts in this trigger with the related opportunities of each account.
      
      - After the records and their related records are obtained, the for loop iterates over the records of interest by using the collection variable—in this case, acctsWithOpps

      - The collection variable holds the results of the SOQL query. That way, the for loop iterates only over the records we want to operate on. Because the related records are already obtained, no further queries are needed within the loop to get those records.
  
  5. Alternatively, if you don’t need the account parent records, you can retrieve only the opportunities that are related to the accounts within this trigger context. 

    * trigger SoqlTriggerBulk on Account(after update) {  
        // Perform SOQL query once.    
        // Get the related opportunities for the accounts in this trigger.
        List<Opportunity> relatedOpps = [SELECT Id,Name,CloseDate FROM Opportunity
            WHERE AccountId IN :Trigger.New];
      
        // Iterate over the related opportunities    
        for(Opportunity opp : relatedOpps) { 
            // Do some other processing
        }
      }

      - This list is specified in the WHERE clause by matching the AccountId field of the opportunity to the ID of accounts in Trigger.New: WHERE AccountId IN :Trigger.New.

      - The returned opportunities are for all accounts in this trigger context and not for a specific account. 

  6. You can reduce the previous example in size by combining the SOQL query with the for loop in one statement: the SOQL for loop. Here is another version of this bulk trigger using a SOQL for loop.

    * trigger SoqlTriggerBulk on Account(after update) {  
        // Perform SOQL query once.    
        // Get the related opportunities for the accounts in this trigger,
        // and iterate over those records.
        for(Opportunity opp : [SELECT Id,Name,CloseDate FROM Opportunity
            WHERE AccountId IN :Trigger.New]) {
      
            // Do some other processing
        }
      }

  7. Triggers execute on batches of 200 records at a time. So if 400 records cause a trigger to fire, the trigger fires twice, once for each 200 records.

    * For this reason, you don’t get the benefit of SOQL for loop record batching in triggers, because triggers batch up records as well. 

    *  The SOQL for loop is called twice in this example, but a standalone SOQL query would also be called twice. 

    * However, the SOQL for loop still looks more elegant than iterating over a collection variable!

# Performing Bulk DML

  1. When performing DML calls in a trigger or in a class, perform DML calls on a collection of sObjects when possible. 

  2. Performing DML on each sObject individually uses resources inefficiently. The Apex runtime allows up to 150 DML calls in one transaction.

  3. This trigger performs an update call inside a for loop that iterates over related opportunities. 

  4. If certain conditions are met, the trigger updates the opportunity description. 

    *  If each account has one or two opportunities, we can easily end up with over 150 opportunities. The DML statement limit is 150 calls.

    *  In this example, the update statement is inefficiently called once for each opportunity. If a bulk account update operation fired the trigger, there can be many accounts.

      - trigger DmlTriggerNotBulk on Account(after update) {   

          // Get the related opportunities for the accounts in this trigger.        
          List<Opportunity> relatedOpps = [SELECT Id,Name,Probability FROM Opportunity
              WHERE AccountId IN :Trigger.New];       

          // Iterate over the related opportunities
          for(Opportunity opp : relatedOpps) { 

              // Update the description when probability is greater 
              // than 50% but less than 100% 
              if ((opp.Probability >= 50) && (opp.Probability < 100)) {
                  
                  opp.Description = 'New description for opportunity.';

                  // Update once for each opportunity -- not efficient!
                  update opp;
              }
          }    
        }

    * This next example shows how to perform DML in bulk efficiently with only one DML call on a list of opportunities. The example adds the Opportunity sObject to update to a list of opportunities (oppsToUpdate) in the loop

      - trigger DmlTriggerBulk on Account(after update) {   

          // Get the related opportunities for the accounts in this trigger.        
          List<Opportunity> relatedOpps = [SELECT Id,Name,Probability FROM Opportunity
              WHERE AccountId IN :Trigger.New];
                
          List<Opportunity> oppsToUpdate = new List<Opportunity>();

          // Iterate over the related opportunities
          for(Opportunity opp : relatedOpps) {      

              // Update the description when probability is greater 
              // than 50% but less than 100% 
              if ((opp.Probability >= 50) && (opp.Probability < 100)) {
                  opp.Description = 'New description for opportunity.';
                  oppsToUpdate.add(opp);
              }
          }
          
          // Perform DML on a collection
          update oppsToUpdate;
        }


