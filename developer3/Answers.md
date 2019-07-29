fire a query on the account object where industry=chem & collect all those records id in set.final o/p shd be set. 

Set<Account> account = [SELECT Id, Industry FROM ACCOUNT Where Industry='chem'];