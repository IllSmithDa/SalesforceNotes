public class ApexClass2 {
    public static void apexFunc(String myName, String myEmail, String accountName) {

    	Contact[] contacts = [SELECT Id, Name, Email FROM Contact WHERE (Name=:myName OR Email=:myEmail OR  Account.Name=:accountName)];
        System.debug(contacts);
    }
    public static void printErr() {
        try{

        	String myString;
            Integer myInteger = myString.length();
            
        }
        catch(Exception ex){
            
            System.debug('Error: ' + ex.getMessage());
            System.debug('Error cause: ' + ex.getCause());
            
        }
        finally {
			System.debug('System: I have reached the finally code block.');
        }
    }
    
    public static void databaseInsert() {
       /* 
        Success_Log__c log = new Success_Log__c();
        Success_Log__c[] myLogs = new List<Success_Log__c>{};
        
        Error_Log__c error = new ErrorLog(Error_Type__c ='null error', Error_Message__c ='value cannot be null', Error_Line__c='23');
       	Error_Log__c[] errorlogs = new List<Error_Log__c> {error};
		Database.SaveResult[] srList = Database.insert(myLogs, false);
        Database.SaveResult[] srList2 = Database.insert(errorLogs, false);*/
		
		Account myAcc = new Account();
        Account myAcc2 = new Account(name='Peter Pan Corp');
        Account myAcc3 = new Account(name='Oscorp Foundation');
        
        Account[] accList = new List<Account>();
        accList.add(myAcc);
        accList.add(myAcc2);
        accList.add(myAcc3);
        Database.SaveResult[] srList = Database.insert(accList, false);
		
        
        for (Database.SaveResult sresult : srList) {
        	if (sresult.isSuccess()) {
          		// success message if everything goes well
          		System.debug('account successly created: ' + sresult.getId()); }
                Success_Log__c log = new Success_Log__c();
            	insert log;
        	}else {  
          		for(Database.Error err : sresult.getErrors()) {  
            		// error message for failed data entries
            		System.debug(err.getStatusCode() + ': ' + err.getMessage()); 
            		System.debug('Fields that have errors ' + err.getFields()); 
                    Error_Log__c error = new ErrorLog(Error_Type__c = sresult.getType(), Error_Message__c = sresult.getMessage(), Error_Line__c = sresult.getLine());
   					insert error;
          		} 
        	}
      	}          
    }
}

public class oppAssignmentTrigger {

    public static void updateStuff(Opportunity myOpp) {
        if (myOpp.stageName == 'Closed Lost') {
            
            Case[] caseList = [SELECT Status, AccountId FROM CASE WHERE AccountId=:myOpp.AccountId];
            
            for(Case myCase: caseList) {
                myCase.Status = "Closed";   
            }
            update caselist;
        }
    }
}