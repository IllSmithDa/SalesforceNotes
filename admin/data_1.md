# Bad Data
  1. Bad data includes data that is missing entries, incomplete, duplicate records, not updated or no data standards such as universal naming conventions
    
  2. Can account for 20 percent stalled productivity. 12 percent loss of average revenue and perhaps 40 percent of all business initiative failures

    * Bad Data linked with

      - lost revenue

      - missing or inaccurate insights

      - wasted time and resources

      - slow information retrieval

      - poor customer service

      - reputational damage

    * Good data instead lets your company

      - prospect and target new customers

      - gain account insights

      - increase efficiency

      - faster information retrieval

      - build customer trust 

      - plan better

      - get better leads faster

# Handling Data
  1. Find out how compnay using customer data to achieve its business objectives, bonus objectives, where the data is being stored, how its been used, which customer data is required to support these objectives

  2. Different departments will most likely have diffrent processes for creating records but will share the same customer data which is often created and maintained differently between the different departments
  
  3. Data quality has several key attributes

    * Age - data doesn't age well and must be updated consistently

    * Accuracy - Making sure data is accurate as possible and source is trusted

    * Consistency - same formatting, spelling, language across records

    * Duplication - Making sure each entry is original and not a diplicate entry

    * Usage - Is data actually being used, harnessed in reports, dashboards and apps

  4. Salesfore appexchange package called Data Quality Analysis Dashboard app which assess quality of data across various dimensions.

    * it measures data quality using the key attributes mentioned above
  
  5. Develop a Data Management plan which includes

    * naming - setting naming conventions for records such as including suffixes or abbreviations etc

    * formatting - figure out how dates and money are represented ( using mm/dd/yyyy for dates etc)

    * workflow - determine processes for record creation, reviewing, updating, and archiving. Determine all the stages a record goes through during its life cycle

    * quality - set appropriate standards for data quality, including the ability to measure or score records.
    
    * Roles and ownership - determine who owns records, who is accountable for changes to data, and who is notified when changes to data are made.

    * security and permissions - determine levels of privacy and comply with regulatory, legal and contractual obligations

    * monitoring - outline a process for quality control of data, 

  6. Salesforce tools to help implement data plan

    * required fields can be set up to enforce crucial information in data entries

    * validation rules to enforce certain formatting 

    * workflow rules to automate standard internal procedures and process to save time

    * page layouts to help prioritize important fields

    * dashboards to illustrate data usage and management with graphs

    * data enrichment tools that match your data with trusted sources 

    * duplicate management - to deal with duplicate records 
    
    * custom field types to enforce certain fields 

# Why Duplicate Data Is a Problem

  1. Wastes prospects’ and customers’ time.

  2. Has multiple reps calling the same prospects and customers, which seems overly aggressive.

  3. Appears disorganized.

  4. Duplicate data also affects admins, including you. That’s because duplicate records cause sales teams to lose trust in their CRM system. The last thing you want is for your teams to question the validity of the data they rely on.

# Advantages of Duplicate-Free Data

  1. When your sales reps work with duplicate-free data, there’s no guessing about whether a colleague is already qualifying the same prospect.

  2. Also, your reps can count on having all information in one contact record, instead of hunting for more details in a duplicate record.

  3. It’s important that your sales teams feel confident that you’re managing Salesforce and delivering features with your teams’ trust and success in mind.

  4. When your CRM system is free of duplicate data, your reps trust that the data is clean and worthwhile.

# Tools We Give You for Duplicate Management

  1. Salesforce helps your reps handle the duplicate records—from any device.

    * And we give you options to prevent or discourage your sales reps from creating more duplicate records with Duplicate Management.

  2. Duplicate Management helps you and your sales teams quickly and easily manage duplicates for:

    * Business accounts

    * Contacts

    * Leads

    * Person accounts

    * Records created from custom objects

# Rules for Identifying Duplicates and How to Handle Them

  1. Matching rule

    * The matching criteria to identify duplicate records.

    * Salesforce comes with three standard matching rules: one for business accounts; one for contacts and leads, and another for person accounts. Creating other matching rules is a cinch. We show you how Maria does it in the next unit.

  2. Duplicate rule

    * When Salesforce engages matching rules and determines actions to take as it encounters duplicates.

    * Depending on how you configure Duplicate Management, sales reps see an alert that they’re about to create a duplicate. Or your reps are blocked from creating the duplicate altogether.

    * If your company started using Salesforce in Spring ’15 or later, we give you standard duplicate rules for business accounts, contacts, leads, and person accounts. If your company started using Salesforce in Winter ’15 or earlier, like Maria, you create the rules on your own, which is easy.

# How Duplicate Management Works

  1. Erin creates the contact, and Salesforce looks for possible duplicates (1). Based on the criteria in a matching rule that Maria set up earlier, Salesforce provides a list of possible duplicates (2).

  2. The duplicate rule determines Erin’s options. The rule can block Erin from creating the record or let her create it and show an alert (3). If she does create the contact, the rule can even add the potential duplicate to a report for her manager, Lincoln, to see.

  3. In this case, the standard duplicate rule alerts Erin of the potential duplicate. She has the choice to go to the contact that’s already in Salesforce, or continue creating the record, even though it’s a potential duplicate.

# Rules Deep-Dive

  1. Matching rules and duplicate rules work together to ensure that your sales teams work with data that’s free of duplicates. 

  2. Before your reps save new and updated records, matching rules and duplicate rules provide warnings of potential duplicates. You manage matching rules and duplicate rules in Setup.

  3. We developed our standard matching rules to return the best possible set of match candidates for business accounts, contacts, leads, and person accounts

# Matching Criteria Example

  1. First Name

    * If the record contains a value for both First Name and Last Name fields, those values are transposed to consider possible data entry mistakes.

      - The first name is Luis and the last name is Antonio.

      - The matching rule evaluates the first name as Antonio and the last name as Luis.

  2. Title

    * Considers acronyms and full titles.

      - The title is VP.

      - The matching rule considers VP and Vice President.

  3. Mailing Street

    * Addresses are broken into sections and compared with those sections. Each section has its own matching method and match score. The section scores are weighted to determine one score for the field. This process works best with North American data.

    * Duplicate Management compares these two addresses.

      - 123 Market St, Ste 100

      - 123 Market Dr, Ste 300

    * Only the street number and street name match. The field has a match score of 70 out of a possible 80. This comparison isn’t a match.

    * For example, some of your contacts include phone numbers with country codes. So you create a custom matching rule to include fuzzy matching for phone numbers. Salesforce flags contacts with matching phone numbers as duplicates, even though one includes a country code and the other doesn’t.

# Activate a Matching Rule

  1. We provide standard matching rules for you. If you established your instance of Salesforce for Winter ’15 or earlier, like Maria, you activate the standard rules you want to use. 

  2. From Setup, Maria enters Matching Rules in the Quick Find box, then selects Matching Rules.

  3. Maria selects Contact.

  4. She gives the rule a descriptive name, Custom Contact Matching Fuzzy Mailing Street. She also adds a description so that other admins understand its value.

  5. Maria adds the matching criteria. The option Match Blank Fields compares records with those empty fields and considers the records as duplicates. But that’s not what Maria wants. She saves her rule and activates it.

# Block Duplicates with Fuzzy Mailing Streets

  1. Before an active matching rule can do anything, you pair it with a duplicate rule. Maria wants to prevent sales teams from creating duplicates when the Mailing Street field includes variants, such as SW Barnes Ave and Southwest Barnes Avenue.

  2. From Setup, Maria enters Duplicate Rules in the Quick Find box, then selects Duplicate Rules.

  3. She clicks New Rule and selects Contact.

  4. Maria gives the duplicate rule a name and description.

  5. She blocks the creation of duplicates. She also blocks her teams from editing contacts that result in duplicates.

  6. She compares the new or updated contact with contacts already in Salesforce using the custom matching rule she created earlier. Then, she adds her duplicate rule.

# Report on the Creation of Duplicate Accounts and Leads

  1. Maria doesn’t block reps from creating duplicates for accounts and leads. So Lincoln wants to see the quality of account and lead data and how well the duplicate rules work.

  2. To help Lincoln, Maria sets up custom report types. Lincoln can then run reports on accounts and leads that his reps create after bypassing the warnings of creating potential duplicate records.

  3. From Setup, Maria enters Report Types in the Quick Find box, then selects Report Types. She then clicks New Custom Report Type.

  4. She selects the primary object, Accounts. She gives the report type a name and stores it in a category.

  5. Maria selects Duplicate Record Items, so that newly created duplicate account records appear on the report. Then, she saves the report type.

  6. From here, Maria can adjust the page layout. Then, she repeats this procedure for leads.