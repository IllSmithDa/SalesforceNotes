# Apex Unit Testing 

  1. The Apex testing framework enables you to write and execute tests for your Apex classes and triggers on the Lightning Platform

  2. Apex unit tests ensure high quality for your Apex code and let you meet requirements for deploying Apex.

  3. Testing is the key to successful long-term development and is a critical component of the development process. 

  4. The Apex testing framework makes it easy to test your Apex code. Apex code can only be written in a sandbox environment or a Developer org, not in production. 

  5. Apex code can be deployed to a production org from a sandbox. Also, app developers can distribute Apex code to customers from their Developer orgs by uploading packages to the Lightning Platform​ AppExchange. 

  6. In addition to being critical for quality assurance, Apex unit tests are also requirements for deploying and distributing Apex. The following are the benefits of Apex unit tests.

    * Ensuring that your Apex classes and triggers work as expected

    * Having a suite of regression tests that can be rerun every time classes and triggers are updated to ensure that future updates you make to your app don’t break existing functionality

    * Meeting the code coverage requirements for deploying Apex to production or distributing Apex to customers via packages

    * High-quality apps delivered to the production org, which makes production users more productive

    * High-quality apps delivered to package subscribers, which increase your customers trust

  7. Before each major service upgrade, Salesforce runs all Apex tests on your behalf through a process called Apex Hammer. 

    * The Hammer process runs in the current version and next release and compares the test results. 

    * This process ensures that the behavior in your custom code hasn’t been altered as a result of service upgrades.

    * The Hammer process picks orgs selectively and doesn’t run in all orgs. Issues found are triaged based on certain criteria. Salesforce strives to fix all issues found before each new release.

    * Maintaining the security of your data is our highest priority. We don't view or modify any data in your org, and all testing is done in a copy that runs in a secure data center.

# Code Coverage Requirement for Deployment

  1. Before you can deploy your code or package it for the Lightning Platform​ AppExchange, at least 75% of Apex code must be covered by tests, and all those tests must pass. 

  2. In addition, each trigger must have some coverage.

  3. Even though code coverage is a requirement for deployment, don’t write tests only to meet this requirement.

    * Make sure to test the common use cases in your app, including positive and negative test cases, and bulk and single-record processing.

# Test Method Syntax

  1. Test methods take no arguments and have the following syntax:

    * @isTest static void testName() {
        // code_block
      }

  2. Alternatively, a test method can have this syntax:
    
    * static testMethod void testName() {
        // code_block
      }

  3. Using the isTest annotation instead of the testMethod keyword is more flexible as you can specify parameters in the annotation. We’ll cover one such parameter later.

  4. The visibility of a test method doesn’t matter, so declaring a test method as public or private doesn’t make a difference as the testing framework is always able to access test methods.

  5. Test methods must be defined in test classes, which are classes annotated with isTest

    * This sample class shows a definition of a test class with one test method.

      - @isTest
        private class MyTestClass {

          @isTest static void myTest() {
            // code_block
          }

        }
  6. Test classes can be either private or public. If you’re using a test class for unit testing only, declare it as private. Public test classes are typically used for test data factory classes, which are covered later.

# Unit Test Example: Test the TemperatureConverter Class - The following simple example is of a test class with three test methods. The class method that’s being tested takes a temperature in Fahrenheit as an input. It converts this temperature to Celsius and returns the converted result. Let’s add the custom class and its test class.

  1. In the Developer Console, click File | New | Apex Class, and enter TemperatureConverter for the class name, and then click OK

  2. Replace the default class body with the following.

    * public class TemperatureConverter {
        
        // Takes a Fahrenheit temperature and returns the Celsius equivalent.
        public static Decimal FahrenheitToCelsius(Decimal fh) {
        Decimal cs = (fh - 32) * 5/9;
        return cs.setScale(2);
        }
      }

  3. Press Ctrl+S to save your class.

  4. Repeat the previous steps to create the TemperatureConverterTest class. Add the following for this class.

    * @isTest
      private class TemperatureConverterTest {

        @isTest static void testWarmTemp() {
            Decimal celsius = TemperatureConverter.FahrenheitToCelsius(70);
            System.assertEquals(21.11,celsius);
        }
        
        @isTest static void testFreezingPoint() {
            Decimal celsius = TemperatureConverter.FahrenheitToCelsius(32);
            System.assertEquals(0,celsius);
        }

        @isTest static void testBoilingPoint() {
            Decimal celsius = TemperatureConverter.FahrenheitToCelsius(212);        
            System.assertEquals(100,celsius,'Boiling point temperature is not expected.');
        } 
        
        @isTest static void testNegativeTemp() {
            Decimal celsius = TemperatureConverter.FahrenheitToCelsius(-10);
            System.assertEquals(-23.33,celsius);
        }
            
      }

      - The TemperatureConverterTest test class verifies that the method works as expected by calling it with different inputs for the temperature in Fahrenheit. 

      - Each test method verifies one type of input: a warm temperature, the freezing point temperature, the boiling point temperature, and a negative temperature. 

      - The verifications are done by calling the System.assertEquals() method, which takes two parameters: the first is the expected value, and the second is the actual value.

      - There is another version of this method that takes a third parameter—a string that describes the comparison being done, which is used in testBoilingPoint(). This optional string is logged if the assertion fails.

# Let’s run the methods in this class.

  1. In the Developer Console, click Test | New Run.

  2. Under Test Classes, click TemperatureConverterTest.

  3. To add all the test methods in the TemperatureConverterTest class to the test run, click Add Selected.

  4. Click Run.
  
  5. In the Tests tab, you see the status of your tests as they’re running. Expand the test run, and expand again until you see the list of individual tests that were run. They all have green checkmarks.

    * After you run tests, code coverage is automatically generated for the Apex classes and triggers in the org. You can check the code coverage percentage in the Tests tab of the Developer Console. In this example, the class you’ve tested, the TemperatureConverter class, has 100% coverage, as shown in this image.
  
  6. A known issue with the Developer Console prevents it from updating code coverage correctly when running a subset of tests. To update your code coverage results, use Test | Run All rather than Test | New Run.

  7. Whenever you modify your Apex code, rerun your tests to refresh code coverage results.

  8. Obviously, it isn’t possible to verify every data point, but you can test for common data points and different ranges of input. For example, you can verify passing positive and negative numbers, boundary values, and invalid parameter values to verify negative behavior.

    * Boundary conditions are about minimum and maximum values

      -  For invalid inputs, there is no invalid temperature but the only invalid input is null

# Increase your Code Coverage 

  1. Don’t just aim for 75% coverage, which is the lowest coverage that the Lightning Platform requires for deployments and packages. 

  2. The more test cases that your tests cover, the higher the likelihood that your code is robust. Sometimes, even after you write test methods for all your class methods, code coverage is not at 100%. 

# Create and Execute a Test Suite

  1. A test suite is a collection of Apex test classes that you run together.  

    * For example, create a suite of tests that you run every time you prepare for a deployment or Salesforce releases a new version.
      
      -  Set up a test suite in the Developer Console to define a set of test classes that you execute together regularly.

# Test Suite Example:

  1. In the Developer Console, select Test | New Suite

  2. Enter TempConverterTaskUtilSuite for the suite name, and then click OK.

  3. Select TaskUtilTest, hold down the Ctrl key, and then select TemperatureConverterTest.

  4. To add the selected test classes to the suite, click >.

  5. Click Save.

  6. Select Test | New Suite Run.

  7. Select TempConverterTaskUtilSuite, and then click > to move TempConverterTaskUtilSuite to the Selected Test Suites column.

  8. Click Run Suites.

  9. On the Tests tab, monitor the status of your tests as they’re running. Expand the test run, and expand again until you see the list of individual tests that were run. Like in a run of individual test methods, you can double-click method names to see detailed test results.

# Creating Test Data

  1. Salesforce records that are created in test methods aren’t committed to the database. They’re rolled back when the test finishes execution

  2. This rollback behavior is handy for testing because you don’t have to clean up your test data after the test executes.

  3. By default, Apex tests don’t have access to pre-existing data in the org, except for access to setup and metadata objects, such as the User or Profile objects

  4. You can create test data directly in your test method, or by using a utility test class as you’ll find out later.

# More on Apex Unit Testing 

  1. You can save up to 6 MB of Apex code in each org. Test classes annotated with @isTest don’t count toward this limit.

  2. Even though test data rolls back, no separate database is used for testing. As a result, for some sObjects that have fields with unique constraints, inserting duplicate sObject records results in an error.

  3. Test methods don’t send emails.

  4. Test methods can’t make callouts to external services. You can use mock callouts in tests.

  5. SOSL searches performed in a test return empty results. To ensure predictable results, use Test.setFixedSearchResults() to define the records to be returned by the search

