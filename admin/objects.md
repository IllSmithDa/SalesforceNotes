# Standard object 

  1. Common objects used by every client including Account, Leads, Orders, Contacts

  2. Standard objects can have standard fields and you can add custom fields 

# Custom Objects

  1. Objects that are specifically taylored to a client's needs

  2. The autonumber option allows you to assign an ID to 

  3. The api name is used by salesforce internally

    * api - aplication programming interface 

        - allows external application to interact with current applicaiton

  4. There are many different types of fields in objects 

    * there will definitely be questions on this matter on credentials 

    * red vertical line are required fields

  5. One object and one tab relationship 
    
    * Anything else is not allowed 

    * you can have object without a tab

  6. Validation rules are basically glorified version of formula fields

  7. Picklist field type are great for standardizing values of a field 

    * Prevents users from manually entering different variations of the same value 

      - e.g Ca or California or Cali 

    * You can add an additional textbox field if a value is not available in the picklist

# Object Fields 

  1. required - must not be an empty field

  2. unique - not allow duplicate values

  3. External ID - unique ID indentifier used by external systems

    * helps prevention of duplicate records when importing data into Salesforce

    * you can only have a few data types as external data types

    * these fields are automatically indexed

  4. Custom fields in the api is always followed by '__c'
