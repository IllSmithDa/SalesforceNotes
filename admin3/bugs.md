# If salesforce trailhead can't find certain criterias and actions even though you clearly created them, go Remote Site settings, and add your current site to the list of remote site 

  1. if your salesforce org is na123 then add remote site na123 to the list with url https://na123.salesforce.com

# Security Specialist Badge part 1 and 2 steps to ensure everything works 

  1. create a brand new developer org 

  2. modified org wide opportunity sharing settings 

    * set opportunity to private 

  3. create 3 required profiles mentioned in the module with the appropriate profile settings including clone for all three a standard user (with salesforce license)

    * Field Sales User, Inside Sales User and Sales Executive User

  4. created 1 public group called Project Managers

  5. created 3 roles mentioned in the module (this time I paid more attention to the read/write settings when creating these.)

    * Field Sales, Inside Sales, Sales Executive

  6. created 2 sharing rules
   
    * One is owner based where sales executive and subordinates share with inside sales

    * other is criteria based where opporunity type is existing customer - upgrade and stage is closed won and it is shared with Public Group Project Managers

  7. created 1 user mentioned in the module which is Samantha Cordero

  8. loged in as her, created 2 opportunities (both named needs analysis just in case) mentioned in the Security module

  9. Install package mentioned in module and run the tests according to how the module asks you to 

# Not being able to login into Salesfore data loader 

  1. Reset your security token by going to settings in your profile 

  2. Reset your password for your develop org or trailhead org
  
# Lightning Experience Reports & Dashboards Specialist 

  1. Use a trialhead org in this one not developer org or else Data Import will not show up 

  2. Step 1 issue 

    * If you create 'Status Folder' make sure Api name is Status_Folder instead of the default StatusFolder. 

      - Failure to do this will cause you to fail step 1 of the superbadge

      - https://success.salesforce.com/answers?id=9063A000000t1svQAA

      - https://saturn.salesforce.com/answers?id=9063A0000019cxUQAQ&fbclid=IwAR1xU5AFB6bAkxmdMr3IzQf_Ez8JuDeG_5tnEXafID51Cx3VwMTDA2JpDm0

  3. Another Step 1 issue 

    * Solutions is only available in salesforce classic 

    * Also follow these steps 

      - Go to Setup 

      - Search report types 

      - click new custom report types 

      - Name and store in other reports using name and description provided by the module

      - make sure to check deployed 

    * Finally Go to Report Types in Setup

      - Edit Object relationship

      - connect it to SolarBot Status (b)

    * Go to Field Available for Report, click edit layout

      - Make sure to remove fields as request but make sure to add the rest 

      - do this for both SolarBots and SolarBot Status and save

