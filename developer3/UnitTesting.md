# Basic Unit Testing Functions

  1. System.assert() 

    * accepts two parameters, one (mandatory) which is the condition to test for and the other a message (optional) to display should that condition be false.

  2. System.assertEquals() and System.assertNotEquals() 

    * accepts three parameters; the first two (mandatory) are the variables that will be tested for in/equality and the third (optional) is the message to display if the assert results in false.

  3. Code coverage for Apex unit testing has a minimum of 75 percent. Only then you can move from Sandbox to Production

    * The exception is a trigger in which code coverage is 1 percent minimum.

  4. The 75 percent coverage is not strictly enforced but only when going from sandbox to production

  5. Sandbox to Sanbox, the code coverage is not applied at all. 

  6. Test classes also do not count against your Apex code count limit in your Salesforce org.

    * Salesforce only charges you for classes and for triggers 

  7. You can go to Apex code settings to test how much code coverage by code lines each class has 

    * e.g 6/7 means 6 lines out of 7 are covered which is above the required 75 percent to move code from sandbox to production

  8. Code co

# Testing Syntax

  1. Anontations are required to indicate that you are running a test 

    * public class TestResult {
        @isTest static void testNegative() {
        
            // call static method of existing class PassFail                   
            String ResTest = Passfail.result(10);
            // testing if resTest returns invalid
            System.assertEquals('Invalid', ResTest);
        }
    }

# Example Test 

  1. Pen_c p = new Pen_c();
    p.price = 200;

    // begins the tests
    test.startTest();
      
    // Existing trigger will raise price to 250 
    insert p;

    test.stopTest();

    // test to see if pen has the expected price 
    Pen__c getPen = [SELECT Price FROM Pen__c WHERE id=:pen.id];
    System.assert('250', getPen.Price);

    * These tests can test governer limits which is 150. 

    * Number of soql qeuries is limited to 100

# anotations

  1. @isVisible:this allows to access pvt. variables in test class

  2. @isTest(seeAllData=True):this will let the test code access all records in org.so no need to create sample data.

  3. @testSetup:when we need to have any sample data during testing ,then we can use our own data as well.

# Test Driven Development

  1. Test Driven development is basically where tests are done first before any code is actually written

  2. Most teams use the agile methodology - business and technology running in paralell. 

  3. Waterfall - waiting for management, basic code to be written before you begin to do anything including coding

# Other 

  1. DML statements in the test.start() and test.stop() are not counted towards DML count limit 

