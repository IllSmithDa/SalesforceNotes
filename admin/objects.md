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

# External lookup

  1. Links an object with external object outside your salesforce organizaiton

# More on Picklists 

  1. Global value sets

    * Global value sets let you share the same picklist values with more than one picklist field. 

      - Imagine your bakery has several places where it needs to list ingredients. Assign the same set of ingredient values to more than one picklist field.

    * Pick a single ingredient in one picklist field, and several ingredients in a custom multi-select field from the same value set.

  2. Create a Global Value Set

    * From Setup, enter Picklist in the Quick Find box, then select Picklist Value Sets.

    * Next to Global Value Sets, click New.

    * Enter a label for the global value set. This name identifies the set in Setup, and appears as Values option when users create a picklist field.

    * To tell users what these values are for, enter a specific description of the global value set. This text appears on the Picklist Value Sets list page in Setup.

    * Enter the values, one per line.

    * Optionally, choose to sort the values alphabetically or to use the first value in the list as the default value, or both. If you select both options, Salesforce alphabetizes the entries and then sets the first alphabetized value as the default.

# Manage Values for Global Value sets 

  1. From Setup, enter Picklist in the Quick Find box, then select Picklist Value Sets.

  2. Click the Label of the global value set to see its details

    * Some things to consider about editing global value sets:

      - To replace a value, create the new value first. Then click Replace to start the process.

      - When replacing a value, the Replace all blank values option assigns the new value to all picklist fields that are currently blank.

      - Deleting a value in a global value set goes to the background jobs queue. When the job completes, your picklist is updated and you’re notified by email.

# Promote Existing Field Values to a Global Value Set

  1. Go to the Fields & Relationships section of the object that contains the picklist you want to convert.

  2. Click the Field Label for the picklist.

  3. Click Edit.

  4. Click Promote to Global Value Set.

  5. Enter a label for the global value set.

  6. Accept the Field Name or edit it.

  7. Optionally, enter a description to identify it when using the values for other custom picklists.

  8. Click Promote to Global Value Set, again.

  