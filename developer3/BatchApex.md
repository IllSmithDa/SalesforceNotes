# Batch Apex Methods

  1. Batch Apex allows you to define a job that can be divided into manageable chunks, where each chunk can be processed separately

  2. A single process can handle up to 10000 records 

  3. It will fetch all the records, divide into chunks of 200 records, and the operation will be performed on these separate chunks.

  4. To use Batch apex, You must implement Database.Batchable. Includes three methods 

    * Start 

      - automatically called and will collect records on which operation will be performed

    * Execute 

      - operation which we want to perform on the records fetched from start methods 

    * Finish

      - executes after execute method finishes and processes all data

      - sends email notification as confirmation 

  5. Example

    * global Database.QueryLocator start(Database.BatchableContext BC) {
        String query = 'SELECT Id FROM Account';
        return Database.QUeryLocator(query);
    }

    * global void execute(Database.BatchableContext BC, Account[] scope) {
        for (Account a: scope) {
            a.Name = a.Name + 'alpha'
        }
        update scope;
    }

    * global void finish(Database.BatchableContext BC,) {
        
    }