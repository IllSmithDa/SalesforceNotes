# Annotations

  1. An Apex annotation modifies the way that a method or class is used, similar to annotations in Java. Annotations are defined with an initial @ symbol, followed by the appropriate keyword.

  2. To add an annotation to a method, specify it immediately before the method or class definition. For example:

    * global class MyClass {
        @future
        Public static void myMethod(String a)
        {
             //long-running Apex code
        }
      }

# @AuraEnabled

  1. The @AuraEnabled annotation enables client- and server-side access to an Apex controller method. 

  2. Providing this annotation makes your methods available to your Lightning components (both Lightning web components and Aura components). 

  3. Only methods with this annotation are exposed.

  4. In API version 44.0 and later, you can improve runtime performance by caching method results on the client by using the annotation @AuraEnabled(cacheable=true).

  5. You can cache method results only for methods that retrieve data but do not modify it. 

  6. Using this annotation eliminates the need to call setStorable() in JavaScript code on every action that calls the Apex method.

# @deprecated
 
  1. Use the deprecated annotation to identify methods, classes, exceptions, enums, interfaces, or variables that can no longer be referenced in subsequent releases of the managed package in which they reside. 

  2. This is useful when you are refactoring code in managed packages as the requirements evolve. 

  3. Unmanaged packages cannot contain code that uses the deprecated keyword.

  4. When an Apex item is deprecated, all global access modifiers that reference the deprecated identifier must also be deprecated. 

  5. Any global method that uses the deprecated type in its signature, either in an input argument or the method return type, must also be deprecated.

  6. A deprecated item, such as a method or a class, can still be referenced internally by the package developer.

  7. webservice methods and variables cannot be deprecated.

  8. You can deprecate an enum but you cannot deprecate individual enum values.

  9. You can deprecate an interface but you cannot deprecate individual methods in an interface.

  10. You can deprecate an abstract class but you cannot deprecate individual abstract methods in an abstract class.

  11. You cannot remove the deprecated annotation to undeprecate something in Apex after you have released a package version where that item in Apex is deprecated.

# @future
  
  1. Use the future annotation to identify methods that are executed asynchronously. When you specify future, the method executes when Salesforce has available resources.  

  2. Without the annotation, the Web service callout is made from the same thread that is executing the Apex code, and no additional processing can occur until the callout is complete (synchronous processing).

  3. Methods with the future annotation must be static methods, and can only return a void type. 

  4. The specified parameters must be primitive data types, arrays of primitive data types, or collections of primitive data types.

  5. Methods with the future annotation cannot take sObjects or objects as arguments.

  6. global class MyFutureClass {
     
       @future 
       static void myMethod(String a, Integer i) {
         System.debug('Method called with: ' + a + ' and ' + i);
         // Perform long-running code
       }
     }

  7. To allow callouts in a future method, specify (callout=true). The default is (callout=false), which prevents a method from making callouts.

  8. The following snippet shows how to specify that a method executes a callout:

    * @future (callout=true)
      public static void doCalloutFromFuture() {
         //Add code to perform callout
      }
    
    * Remember that any method using the future annotation requires special consideration because the method does not necessarily execute in the same order it is called.

    * Methods with the future annotation cannot be used in Visualforce controllers in either getMethodName or setMethodName methods, nor in the constructor.

    * You cannot call a method annotated with future from a method that also has the future annotation. Nor can you call a trigger from an annotated method that calls another annotated method.
       
# @InvocableMethod

  1. Invocable methods are called with the REST API and used to invoke a single Apex method. 

  2. Invocable methods have dynamic input and output values and support describe calls.

  3. The following code sample shows an invocable method with primitive data types.

    * public class AccountQueryAction {
        @InvocableMethod(label='Get Account Names' description='Returns the list of account names       corresponding to the specified account IDs.')
        public static List<String> getAccountNames(List<ID> ids) {
          List<String> accountNames = new List<String>();
          List<Account> accounts = [SELECT Name FROM Account WHERE Id in :ids];
          for (Account account : accounts) {
            accountNames.add(account.Name);
          }
          return accountNames;
        }
      }

  4. This code sample shows an invocable method with a specific sObject data type.

    * public class AccountInsertAction {
        @InvocableMethod(label='Insert Accounts' description='Inserts the accounts specified and returns the IDs of the new accounts.')
        public static List<ID> insertAccounts(List<Account> accounts) {
          Database.SaveResult[] results = Database.insert(accounts);
          List<ID> accountIds = new List<ID>();
          for (Database.SaveResult result : results) {
            if (result.isSuccess()) {
              accountIds.add(result.getId());
            }
          }
          return accountIds;
        }
      }

  5. Use the InvocableVariable annotation to identify variables used by invocable methods in custom classes.
   
    * The InvocableVariable annotation identifies a class variable used as an input or output parameter for an InvocableMethod method’s invocable action. 

    * If you create your own custom class to use as the input or output to an invocable method, you can annotate individual class member variables to make them available to the method.

# Other Annotations

  1. Use the @isTest annotation to define classes and methods that only contain code used for testing your application.

    * The @isTest annotation on methods is equivalent to the testMethod keyword. 

    * The @isTest annotation can take multiple modifiers within parentheses and separated by blanks.

    * @isTest
      private class MyTestClass {
      
         // Methods for testing
         @isTest static void test1() {
            // Implement test code
         }
      
         @isTest static void test2() {
            // Implement test code
         }
      
      }

  2. The @ReadOnly annotation allows you to perform unrestricted queries against the Lightning Platform database.

    * It's important to note that this annotation, while removing the limit of the number of returned rows for a request, blocks you from performing the following operations within the request: DML operations, calls to System.schedule, calls to methods annotated with @future, and sending emails.

    * The @ReadOnly annotation is available for Web services and the Schedulable interface.

    * To use the @ReadOnly annotation, the top level request must be in the schedule execution or the Web service invocation. 

  3. The RemoteAction annotation provides support for Apex methods used in Visualforce to be called via JavaScript. This process is often referred to as JavaScript remoting.

  4. The @SuppressWarnings annotation does nothing in Apex but can be used to provide information to third party tools.

  5. Methods defined with the @testSetup annotation are used for creating common test records that are available for all test methods in the class.

    * Test setup methods are defined in a test class, take no arguments, and return no value. The following is the syntax of a test setup method.

    * @testSetup static void methodName() {

      }
 
    * If a test class contains a test setup method, the testing framework executes the test setup method first, before any test method in the class. 

    * Records that are created in a test setup method are available to all test methods in the test class and are rolled back at the end of test class execution.

    * If a test method changes those records, such as record field updates or record deletions, those changes are rolled back after each test method finishes execution.

      - The next executing test method gets access to the original unmodified state of those records
  
  6. Use the TestVisible annotation to allow test methods to access private or protected members of another class outside the test class. 

    * These members include methods, member variables, and inner classes. 

    * This annotation enables a more permissive access level for running tests only. This annotation doesn’t change the visibility of members if accessed by non-test classes.

    * With this annotation, you don’t have to change the access modifiers of your methods and member variables to public if you want to access them in a test method.  

      - For example, if a private member variable isn’t supposed to be exposed to external classes but it should be accessible by a test method, you can add the TestVisible annotation to the variable definition.

    * public class TestVisibleExample {
          // Private member variable
          @TestVisible private static Integer recordNumber = 1;
      
          // Private method
          @TestVisible private static void updateRecord(String name) {
              // Do something
          }
      }   

    * This is the test class that uses the previous class. It contains the test method that accesses the annotated member variable and method.

    @isTest
    private class TestVisibleExampleTest {
        @isTest static void test1() {
            // Access private variable annotated with TestVisible
            Integer i = TestVisibleExample.recordNumber;
            System.assertEquals(1, i);
    
            // Access private method annotated with TestVisible
            TestVisibleExample.updateRecord('RecordName');
            // Perform some verification
        }
    }    