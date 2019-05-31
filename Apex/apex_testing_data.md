# Create Test Data for Apex Tests 

  1. Create Test Data for Apex Tests

    * Use test utility classes to add reusable methods for test data setup.

# Adding a Test Utility Class

  1. Let’s refactor the previous test method by replacing test data creation with a call to a utility class method. First, you need to create the test utility class.

  2. The TestDataFactory class is a special type of class—it is a public class that is annotated with isTest and can be accessed only from a running test. Test utility classes contain methods that can be called by test methods to perform useful tasks, such as setting up test data. Test utility classes are excluded from the org’s code size limit.

# To add the TestDataFactory class:

  1. In the Developer Console, click File | New | Apex Class, and enter TestDataFactory for the class name, and then click OK.

  2. Replace the default class body with the following.

    * @isTest
      public class TestDataFactory {

        public static List<Account> createAccountsWithOpps (Integer numAccts, Integer numOppsPerAcct) {
            List<Account> accts = new List<Account>();
            
            for(Integer i=0;i<numAccts;i++) {

                Account a = new Account(Name='TestAccount' + i);
                accts.add(a);
            }
            insert accts;
            
            List<Opportunity> opps = new List<Opportunity>();

            for (Integer j=0;j<numAccts;j++) {
                Account acct = accts[j];

                // For each account just inserted, add opportunities
                for (Integer k=0;k<numOppsPerAcct;k++) {
                    opps.add(new Opportunity(Name=acct.Name + '       Opportunity ' + k,
                                           StageName='Prospectin      g',
                                           CloseDate=System.      today().addMonths(1),
                                           AccountId=acct.Id));
                }
            }

            // Insert all opportunities for all accounts.
            insert opps;
            
            return accts;
        }
      }

  3. This test utility class contains one static method, createAccountsWithOpps(), which accepts the number of accounts (held in the numAccts parameter) and the number of related opportunities to create for each account (held in the numOppsPerAcct parameter). The first loop in the method creates the specified number of accounts and stores them in the accts list variable.

  4. The first loop in the method creates the specified number of accounts and stores them in the accts list variable. 

  5. The second loop creates the opportunities. Because each group of opportunities are linked to one account, the outer loop iterates through accounts and contains a nested loop that creates related opportunities for the current account. 

  6. The next time the nested loop is run, opportunities are added to the same list using the add() method. 

  7. Opportunities are linked to their parent accounts using the AccountId field.

    * ld. The total number of all opportunities that are created is the product of the number of opportunities with the number of accounts (numOppsPerAcct*numAccts). 
    
    * Next, the insert() DML statement is efficiently called outside the loop to create all opportunities in the collection for all accounts in one call only.
  
# Calling Utility Methods for Test Data Creation

  1. Now that you’ve added the test utility class, modify the test class to take advantage of this class. In the TestAccountDeletion class, replace the block that starts with // Test data setup and ends with insert opp; with:

    * // Test data setup
      // Create one account with one opportunity by calling a utility method
      Account[] accts = TestDataFactory.createAccountsWithOpps(1,1);

    * The array returned by the TestDataFactory.createAccountsWithOpps(1,1) call contains one Account sObject.

    * @isTest
      private class TestAccountDeletion {

        @isTest static void TestDeleteAccountWithOneOpportunity() {
          // Test data setup
          // Create one account with one opportunity by calling a utility method
          Account[] accts = TestDataFactory.createAccountsWithOpps(1,1);
          
          // Perform test
          Test.startTest();
          Database.DeleteResult result = Database.delete(accts[0], false);
          Test.stopTest();
          
          // Verify that the deletion should have been stopped by the trigger,
          // so check that we got back an error.
          System.assert(!result.isSuccess());
          System.assert(result.getErrors().size() > 0);
          System.assertEquals('Cannot delete account with related opportunities.',
                               result.getErrors()[0].getMessage());
        }        
      }
    
# Testing for Different Conditions

  * @isTest
    private class TestAccountDeletion {
        @isTest static void TestDeleteAccountWithOneOpportunity() {

            // Test data setup
            // Create one account with one opportunity by calling a utility method
            Account[] accts = TestDataFactory.createAccountsWithOpps(1,1);
            
            // Perform test
            Test.startTest();
            Database.DeleteResult result = Database.delete(accts[0], false);
            Test.stopTest();

            // Verify that the deletion should have been stopped by the trigger,
            // so check that we got back an error.
            System.assert(!result.isSuccess());
            System.assert(result.getErrors().size() > 0);
            System.assertEquals('Cannot delete account with related opportunities.',
                                 result.getErrors()[0].getMessage());
        }
        
        @isTest static void TestDeleteAccountWithNoOpportunities() {

            // Test data setup
            // Create one account with no opportunities by calling a utility method
            Account[] accts = TestDataFactory.createAccountsWithOpps(1,0);
            
            // Perform test
            Test.startTest();
            Database.DeleteResult result = Database.delete(accts[0], false);
            Test.stopTest();

            // Verify that the deletion was successful
            System.assert(result.isSuccess());
        }
        
        @isTest static void TestDeleteBulkAccountsWithOneOpportunity() {

            // Test data setup
            // Create accounts with one opportunity each by calling a utility method
            Account[] accts = TestDataFactory.createAccountsWithOpps(200,1);
            
            // Perform test
            Test.startTest();
            Database.DeleteResult[] results = Database.delete(accts, false);
            Test.stopTest();

            // Verify for each record.
            // In this case the deletion should have been stopped by the trigger,
            // so check that we got back an error.
            for(Database.DeleteResult dr : results) {
                System.assert(!dr.isSuccess());
                System.assert(dr.getErrors().size() > 0);
                System.assertEquals('Cannot delete account with related opportunities.',
                                     dr.getErrors()[0].getMessage());
            }
        }
        
        @isTest static void TestDeleteBulkAccountsWithNoOpportunities() {
            // Test data setup
            // Create accounts with no opportunities by calling a utility method
            Account[] accts = TestDataFactory.createAccountsWithOpps(200,0);
            
            // Perform test
            Test.startTest();
            Database.DeleteResult[] results = Database.delete(accts, false);
            Test.stopTest();
            // For each record, verify that the deletion was successful
            for(Database.DeleteResult dr : results) {
                System.assert(dr.isSuccess());
            }
        }
    }

# Running All Test Methods

  1. The final step is to run the test methods in our test class, now that the class contains more comprehensive tests and has been refactored to use a test data factory. Since you’ve already run the tests in the TestAccountDeletion class, you can just rerun this test class to run all its test methods.

    * To execute the same test run, click the Tests tab, select your test run, and then click Test | Rerun.

    * Check the results in the Tests tab by expanding the latest test run. The test run should report that all four tests passed!