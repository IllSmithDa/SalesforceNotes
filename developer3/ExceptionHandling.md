# Exception Handling

  1. Exception includes bug handling and unexpected errors. 

# Types of Exceptions

  1. DML Exception

  2. null pointer exception

  3. list exception

  4. query exception

  5. generic exception

# To Catch an Exception

  1. Try {
     // code which can possible throw an error 
  }

  2. catch(Exception exception) {
    * code which will actually handle the error caught in the try block
    
    * it will allow code to stop continue running and handle error gracefully rather than giving a hard coded error. 

    * Code will run in order from top to bottom so if a error is found, it will exit the try block and into the catch block

      - rest of the try block is ignored

      - once catch block is executed, it will run the finally block
    
    * When running multiple catches, you should put this one last as this is the most general catch block 

      * exception.getMessage() - will give error message 

      * excpetion.getLineNumber() - will get line number of error
  }
  catch(DmlException e) {
      
      * catches DML excpetion. Note that the code will stop at the first ////
      
      * criteria met catch block. In this case, the first general exception catch block will run since every exception meets the criteria. 

      * When performing bult dml operations, it will insert all the records at once
        
        - This means if any of the data is bad, none of the records will get inserted
  }
  catch(SObjectException e) {
    
    * catches SObject Exception. Note that the code will stop at the first criteria met catch block 
  }
  finally {
    
    * The finally statement identifies a block of code that is guaranteed to execute and allows you to clean up your code

    * either finally or catch must be present. Can be both. Most of the time catch is used

  }

# exception methods