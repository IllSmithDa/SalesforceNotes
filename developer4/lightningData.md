# Lightning Data Service

  1. Lightning Data services allows you to get data from a database without using Apex classes or SOQL queries

  2. Minimalizes the amount of server side customization and server side code (Apex classes)

  3. It covers many use cases though there may be some limitations 

  4. aura:recorddata - If it is in record page, it will fetch all records of current object you are viewing

# Types of Lightning Data Services
  
  1. There are many different types of lightning data services

  2. @api recordId is basic syntax for implementing a lightning data services function as well as the following imports (using Account record as example)

    * import { getRecord, getFieldValue } from 'lightning/uiRecordApi';

    * import ACCOUNT_OBJECT from '@salesforce/schema/Account';

  3. Lightning Data services is also more secure as it utilizes less server side code 