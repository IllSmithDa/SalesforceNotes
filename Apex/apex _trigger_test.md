# Testing Triggers

  1. Before deploying a trigger, write unit tests to perform the actions that fire the trigger and verify expected results.

  2. Let’s test a trigger that we worked with earlier in the Writing Apex Triggers unit. If an account record has related opportunities, the AccountDeletion trigger prevents the record’s deletion.

# Adding and Running a Unit Test - First, let’s start by adding a test method. This test method verifies what the trigger is designed to do (the positive case): preventing an account from being deleted if it has related opportunities. 

  1. In the Developer Console, click File | New | Apex Class.
  
  2. Enter TestAccountDeletion for the class name, and then click OK.

  3. Replace the default class body with the following.

    * @isTest
      private class TestAccountDeletion {

        @isTest static void TestDeleteAccountWithOneOpportunity() {

          // Test data setup
          // Create an account with an opportunity, and then try to delete it
          Account acct = new Account(Name='Test Account');
          insert acct;
          Opportunity opp = new Opportunity(Name=acct.Name + ' Opportunity',
                                         StageName='Prospecting',
                                         CloseDate=System.today().addMonths(1),
                                         AccountId=acct.Id);
          insert opp;
          
          // Perform test
          Test.startTest();
          Database.DeleteResult result = Database.delete(acct, false);
          Test.stopTest();

          // Verify 
          // In this case the deletion should have been stopped by the trigger,
          // so verify that we got back an error.
          System.assert(!result.isSuccess());
          System.assert(result.getErrors().size() > 0);
          System.assertEquals('Cannot delete account with related opportunities.',
                                result.getErrors()[0].getMessage());
        }
          
      }

      - The test method first sets up a test account with an opportunity

      - Next, it deletes the test account, which fires the AccountDeletion trigger. 

      - The test method verifies that the trigger prevented the deletion of the test account by checking the return value of the Database.delete() call. 

      - The return value is a Database.DeleteResult object that contains information about the delete operation.

      - The test method verifies that the deletion was not successful and verifies the error message obtained.

      - The TestAccountDeletion test class contains only one test method, which tests for a single account record. Also, this test is for the positive case. Always test for more scenarios to ensure that the trigger works in all cases, including deleting an account without opportunities and bulk account deletions.

      - Test data is set up inside the test method, which can be time-consuming as you add more test methods. If you have many test methods, put test-data creation in a test utility class and call the utility class from multiple test methods. 

      - The test method contains the Test.startTest() and Test.stopTest() method pair, which delimits a block of code that gets a fresh set of governor limits. In this test, test-data setup uses two DML statements before the test is performed. 

      - To test that Apex code runs within governor limits, isolate data setup’s limit usage from your test’s.

      - To isolate the data setup process’s limit usage, enclose the test call within the Test.startTest() and Test.stopTest() block.  Also use this test block when testing asynchronous Apex.

      - 
  
  4. To run this test, click Test | New Run.

    * Under Test Classes, click TestAccountDeletion.

    * To add all the methods in the TestAccountDeletion class to the test run, click Add Selected.

    * Click Run.