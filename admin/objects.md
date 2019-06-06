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

  5. You can have currently 500 fields for either a custom or standard object


# Many to Many relationships in objects

  1. Examples of many to many
  
    * many candidates applying for multiple job openings

      - candidates and job openings are both parents with one being primary master and
      the other being the secondary master

      - if candidates is deleted, job openings become primary master

      - There is some sort of junction object to describe this relationship or a two way
      master detail relationship between two masters

    * many students applying to multiple classes

      - student beng primary master and classes being secondary master

    * many people participating in multiple sports

      - people being primary master and sports as the secondary master

    * multiple courses for multiple facilities 

      - courses being prmary master and facilities being secondary master

# Junction Object

  1. Junction object has 2 relationship fields
  
    * e.g one relationship towards the student master and second relationship towards the activity master
  
  2. You can drag object and use master detail option in the schema builder

  3. Custom object can only have up to 2 master detail relationship

  4. You can however, still have up to 40 lookup relationships in total

    * That total goes down by one for every master detail relationships that exists

      - e.g 1 master detail = 39 lookup relationships 
      
      - e.g 2 master detail = 38 lookup relationships

      

