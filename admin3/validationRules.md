# Validation Rules

  1. Works practically as a formula field

  2. Used to create criterias which data entries must be followed

  3. Can be found in the Object Manager and it is the bottom tab below Triggers

  4. Formula error will only show if conditions are met or if the condition is true

# WHat happens to the already existing data after Validation rules active

  1. The errors will not be automatically be catched for already existing data

  2. THe validation error will only catch once data entry is being edited and saved again

  3. So, previously existing data will have to be updated manually before validation rules go into effect for already existing data. 

  4. Formula fields on the other hand does retrospectively calculate the field for previously existing data but not for validation rules. 

# Field types and Validation

  1. Field types come with their own in built validation type

    * e.g email field type will autimatically validate for a valid email

# Roll Up Summary Field

  1. You can create a roll up summary field in the case of master detail relationship

    * You can only create roll up summary in the master or parent object

  2. You cannot create a roll up summary field in case of a look up relationships

  3. There are four types including COUNT, SUM, MIN, MAX

    * You can add criteria to limit the summary to data that passes the criteria

# Verfiying roll up value (especially when data count is high)

  1. You can use SOQL query to determine the legitimacy of roll up summary 

  2. You can also gernerate a report which will also use to verify the data 

# Master detail relationships ID

  1. This Id and relationship is not unique and does not work as a primary key because it describes a one to many relationship

    * e.g one Account with many Opportunities

  2. 