# Sosl is list of lists because you are searching many objects 

  1. Use FIND keyword rather than SELECT 

    * FIND 'IBM' RETURNING Account(name), Opportunit(name)

      - find record matching 'IBM' returning the record Account Name and Opportunity Name

    * FIND {Ree*} RETURNING Pen__c(id, name)

      - find records matching term that starts with Ree and returns reords Pen object id and name   

    
  2. Most of the time you use SOQL queries as most of the time you know which object you want 
  to search and you only need one object

# SOSL Use case 

  1. When you have less certainty of where record is 

  2. You do not know which object a particular record exists or data exists 

  3. multiple object search is the main advantage in SOSL query 

    * If you want, retrieve records from multiple objects, use SOSL

