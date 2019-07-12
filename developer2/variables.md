# Variable Basics 

  1. Integer

    * A 32-bit number that does not include any decimal point. 
    
    * The value range for this starts from -2,147,483,648 and the maximum value is up to 2,147,483,647.

  2. The System.debug() function prints the value of variable so that we can use this to debug or to get to know what value the variable holds currently.

  3. Boolean

    * This variable can either be true, false or null. 
    
    * Many times, this type of variable can be used as flag in programming to identify if the particular condition is set or not set.

    * e.g Boolean shipmentDispatched = true;

  4. Date
  
    * This variable type indicates a date. 
    
    * This can only store the date and not the time. For saving the date along with time, we will need to store it in variable of DateTime.

    * e.g Date ShipmentDate = date.today();

  5. Long

    * This is a 64-bit number without a decimal point. 

    * This is used when we need a range of values wider than those provided by Integer.

    * e.g Long companyRevenue = 21474838973344648L;

  6. Object

    * We can refer this as any data type which is supported in Apex.

    * For example, Class variable can be object of that class, and the sObject generic type is also an object and similarly specific object type like Account is also an Object.

    * Account objAccount = new Account (Name = 'Test Chemical');

  7. String
    
    * String is any set of characters within single quotes.

    * It does not have any limit for the number of characters. 

    * Here, the heap size will be used to determine the number of characters. 

    * This puts a curb on the monopoly of resources by the Apex program and also ensures that it does not get too large.

    * e.g String companyName = 'Abc International';

  8. Time
    
    * This variable is used to store the particular time. This variable should always be declared with the system static method.

    * newInstance(hour, minute, second, millisecond)

    * e.g Time myTime = Time.newInstance(3, 14, 15, 926);
      System.assertEquals(926, myTime.millisecond());
      System.assertEquals(15, myTime.second());

    * Time myTime = Time.newInstance(1, 2, 3, 0);
      Time expected = Time.newInstance(1, 2, 4, 400);
      System.assertEquals(expected, myTime.addMilliseconds(1400));

    * Time myTime = Time.newInstance(18, 30, 2, 20);
      // get minutes
      Integer myMinutes = myTime.minute();
      // add 5 minutes
      myMinutes = myMinutes + 5;
      // add minutes 
      System.assertEquals(myMinutes, 35);

    * Time myTime = Time.newInstance(1, 2, 55, 0);
      Time expected = Time.newInstance(1, 3, 5, 0);
      System.assertEquals(expected, myTime.addSeconds(10));

    * Time myTime = Time.newInstance(18, 30, 2, 20);
      System.debug(myTime);
      myTime = myTime.addHours(2);
      Integer myHour = myTime.hour();
      System.debug(myTime);
      System.assertEquals(myHour, 20);



  9. Blob

    * The Blob is a collection of Binary data which is stored as a single object.

    * You can convert this data type to String or from String using the toString and valueOf methods, respectively. 

    * Blobs can be accepted as Web service arguments, stored in a document (the body of a document is a Blob), or sent as attachments. 

    * e.g String myString = 'StringToBlob';
      Blob myBlob = Blob.valueof(myString);
      // size of integer
      Integer size = myBlob.size();
      System.debug(size);

    * String pdfContent = 'This is a test string';
      Account a = new account(name = 'test');
      insert a;
      Attachment attachmentPDF = new Attachment();
      attachmentPdf.parentId = a.id;
      attachmentPdf.name = a.name + '.pdf';
      attachmentPdf.body = blob.toPDF(pdfContent);
      insert attachmentPDF;

    * String myString = 'StringToBlob';
      Blob myBlob = Blob.valueof(myString);

  10. sObject
   
    * This is a special data type in Salesforce. It is similar to a table in SQL and contains fields which are similar to columns in SQL. 

    * There are two types of sObjects – Standard and Custom.

    * For example, Account is a standard sObject and any other user-defined object (like Customer object that we created) is a Custom sObject.

    * e.g Account objAccount = new Account();
      objAccount.Name = 'ABC Customer';
      objAccount.Description = 'Test Account';
      System.debug('objAccount variable value'+objAccount);

  11. Enum
    
    * Enum is an abstract data type that stores one value of a finite set of specified identifiers.

    * You can use the keyword Enum to define an Enum.

    * Enum can be used as any other data type in Salesforce.

    * Declaring enum for Chemical Compounds
 
      - public enum Compounds {HCL, H2SO4, NACL, HG}
        Compounds objC = Compounds.HCL;
        System.debug('objC value: '+objC);

  12. ID

    * Any valid 18-character Lightning Platform record identifier. 

    * If you set ID to a 15-character value, Apex converts the value to its 18-character representation. 
    
    * All invalid ID values are rejected with a runtime exception.

    * ID id='00300000003T2PGAA0';

