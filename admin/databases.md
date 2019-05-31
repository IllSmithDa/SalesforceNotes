# Databases 
  
  1. data model - A way to model what database tables look like in a way that makes sense to humans
    
    * storing data in a spreadsheet

    * In Salesforce, data model refers to the collection of objects and fields in an app
    
  2. objects - think columns as fields and rows as records 

    * object with fields and a bunch of identically structured records.

    * standard object - objects that are included with Salesforce such as Account, Contact, Opportunity

    * custom object - object you create to store information that is specific to your company or industry

# Fields
  
  1. There are 4 different field types

    * Identity - A 15-character, case-sensitive field that’s automatically generated for every record. You can find a record’s ID in its URL.

    * System - Read-only fields that provide information about a record from the system, like when the record was created or when it was last changed.

    * Name - All records need names so you can distinguish between them. You can use text names or auto-numbered names that automatically increment every time you create a record.

    * Custom - Fields you create on standard or custom objects are called custom fields.
  
  2. Every field has a data type and few examples are as follows

    * Checkbox — for fields that are a simple “yes” or “no,” a checkbox field is what you want.

    * Date or DateTime - these field types represent dates or date/time combinations, like birthdays or sales milestones.

    * Formula - this special field type holds a value that’s automatically calculated based on a formula that you write. For example, D’Angelo can write a formula field that automatically calculates a real estate agent’s commission on a home sale.

# Customize Best Practices 

  1. Be thoughtful about names to make clear what your custom object is and does

  2. Help out your users understand your custom object

  3. Require fields when necessary. 

# Object Relationships 

  1. Object relationships are a special field type that connects two objects together.

    * e.g relationship between the Account object and the Contact object

      - When you look at an account record in Salesforce, you can see that there’s a section for contacts on the Related tab.

    * You can build custom relationships as well. 
  
  2. There are two main types of object relationships: lookup and master-detail.
    
    * Lookup - A lookup relationship essentially links two objects together so that you can “look up” one object from the related items on another object.

      - Lookup relationships can be one-to-one or one-to-many

      - The Account to Contact relationship is one-to-many because a single account can have many related contacts.

      - Often times, relationships in objects do not have to exist as a Contact does not have to be associated with any Account

    * Master-detail relationships - one object is the master and another is the detail. The master object controls certain behaviors of the detail object, like who can view the detail’s data.

      - For example, let’s say the owner of a property wanted to take their home off the market. DreamHouse wouldn’t want to keep any offers made on that property. With a master-detail relationship between Property and Offer, you can delete the property and all its associated offers from your system.

      - In a master-detail relationship, the detail object doesn’t work as a stand-alone. It’s highly dependent on the master. In fact, if a record on the master object is deleted, all its related detail records are deleted as well. When you’re creating master-detail relationships, you always create the relationship field on the detail object.
    
    * hierarchical relationships

      - Hierarchical relationships are a special type of lookup relationship. 

      - The main difference between the two is that hierarchical relationships are only available on the User object. You can use them for things like creating management chains between users.

# Schema Builders

  1. Schema Builder is a handy tool for introducing your Salesforce customizations to a co-worker or explaining the way data flows throughout your system.

# Data Import 

  1. Salesforce offers two main methods for importing data

    * Data Import Wizard — this tool, accessible through the Setup menu, lets you import data in common standard objects, such as contacts, leads, accounts, as well as data in custom objects.

      - It can import up to 50,000 records at a time.

      - t provides a simple interface to specify the configuration parameters, data sources, and the field mappings that map the field names in your import file with the field names in Salesforce.

      - Use when you need to load less than 50,000 records, the objects you need to import are supported by the wizard and you don’t need the import process to be automated.
      
      - . It allows you to export data manually once every 7 days (for weekly export) or 29 days (for monthly export). You can also export data automatically at weekly or monthly intervals. In Professional Edition and Developer Edition, you can generate backup files only every 29 days, or automatically at monthly intervals only.

    * Data Loader  —this is a client application that can import up to five million records at a time, of any data type, either from files or a database connection.

      - a client application that you must install separately.

      - It can be operated either through the user interface or the command line. In the latter case, you need to specify data sources, field mappings, and other parameters via configuration files. This makes it possible to automate the import process, using API calls.

      - Use when You need to load 50,000 to five million records, you need to load into an object that is not supported by the Data Import Wizard and you want to schedule regular data loads, such as nightly imports.


  2. Before you import data, you should 

    * Use your existing software to create an export file.

    * Clean up the import file for accuracy and consistency. This involves updating the data to remove duplicates, delete unnecessary information, correct spelling and other errors, and enforce naming conventions. 

    * Compare your data fields with the Salesforce fields you can import into, and verify that your data will be mapped into the appropriate Salesforce field

    * Make any configuration changes required in Salesforce to handle the imported data. For example, you might need to create new custom fields, add new values to picklists, or temporarily deactivate workflow rules.

    * Try to save your excel files as .csv files as they work well with Salesforce data import 
  
  3. Other tips when importing data

    * New Values for Picklists and Multi-Select Picklists - If you import a picklist value that doesn’t match an existing picklist value:
      
      - For an unrestricted picklist, the Data Import Wizard uses the value that’s in the import file.
    
      - For a restricted picklist, the Data Import Wizard uses the picklist’s default value.

    * Multi-Select Picklists - To import multiple values into a multi-select picklist, separate the values by a semicolon in your import file.

    * Checkboxes - To import data into a checkbox field, use 1 for checked values and 0 for unchecked values.

    * Default Values - For picklist, multi-select picklist, and checkbox fields, if you do not map the field in the import wizard, the default value for the field, if any, is automatically inserted into the new or updated record.

    * Date/Time Fieldsm - Ensure that the format of any date/time fields you are importing matches how they display in Salesforce per your locale setting.

    * Formula Fields - Formula fields cannot accept imported data because they are read-only.

    * Field Validation Rules - Salesforce runs validation rules on records before they are imported. Records that fail validation aren’t imported. Consider deactivating the appropriate validation rules before running an import if they affect the records you are importing.


