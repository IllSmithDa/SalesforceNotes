# Introduction to Formula Fields

  1. You’ve got a lot of data in your organization. Your users need to access and understand this data at-a-glance without doing a bunch of calculations in their heads. 
    
    * Enter formula fields, the powerful tool that gives you control of how your data is displayed.

    * Let’s say you wanted to take two numeric fields on a record and divide them to create a percentage. Or perhaps you want to turn a field into a clickable hyperlink for easy access to important information from a record’s page layout. Maybe you want to take two dates and calculate the number of days between them. All these things and more are possible using formula fields.

# Finding the Formula Editor
    
  1. From Setup, open the Object Manager and click Opportunity.

  2. In the left sidebar, click Fields & Relationships.

  3. Click New.

  4. Select Formula and click Next.

  5. In Field Label, type My Formula Field. Notice that Field Name populates automatically.

  6. Select the type of data you expect your formula to return. For example, if you want to write a formula that calculates the commission a salesperson receives on a sale, you select Currency. For now, pick Text.

  7. Click Next. You’ve arrived at the formula editor! Time for our tour.

# Using the Formula Editor

  1. The formula editor comes in two flavors: Simple and Advanced. It’s tempting to use the Simple editor, but we always recommend using the Advanced editor. Advanced doesn’t mean more complicated. It means more tools for you to create powerful formulas.

  2. The Insert Field button opens a menu that allows you to select fields to use in your formula. Inserting from this menu automatically generates the correct syntax for accessing fields.

  3. The Insert Operator button opens a drop-down list of the available mathematical and logical operators.

  4. The Functions menu is where you view and insert formula functions. Functions are more complicated operations that are pre-implemented by Salesforce. Some functions can be used as-is (for example, the TODAY() function returns the current date), while others require extra pieces of information, called parameters. The LEN(text) function, for instance, finds the length of the text you input as a parameter. The formula LEN("Hello") returns a value of 5.

  5. The text area is where you enter your formula. When writing formulas, keep in mind that:

    * Whitespace doesn’t matter. You can insert as many spaces and line breaks as you want without affecting the formula’s execution.

    * Formulas are case sensitive. Pay attention to capitalization of field and object names.

    * When working with numbers, the standard order of operations applies.

  6. Once you’ve written a formula, you can use the Check Syntax button to ensure that everything is in working order before saving. If your formula has issues, the syntax checker alerts you to specific problems

# Using the Formula Editor 

  1. From Setup, open the Object Manager and click Contact.

  2. In the left sidebar click Fields & Relationships.

  3. Click New.
  
  4. For the field type, select Formula and click Next.

  5. Call your field Account Number and select Text for the formula return type. Click Next.

  6. Click Insert Field on the Advanced Formula Editor. Select Contact | Account | Account Number and then click Insert

# Debugging Formulas

  1. Syntax errors are an inevitable part of working with formulas. The Check Syntax button in the editor is an important tool for debugging your formulas

  2. The syntax checker tells you what error it encountered and where it’s located in your formula. Here are some common syntax issues
    
    * Missing parentheses

    * Incorrect parameter type

    * Incorrect number of parameters for function

    * Formula result is incompatible with formula return type

      - You’ll see this error if you select one data type when creating the formula field but write a formula that returns a different data type.

      - My Account Formula expects to return a number (shown in parentheses next to the formula name), but the TODAY() function returns a date.

    * Field does not exist: 

    * Another reason you see this error is if you forget to put quotation marks around a text literal or a hyperlink.

    * Unknown function: In this case, check that Salesforce supports the functions you’re using. You’ll also get this error for misspelled functions. 

# Rolling Summary Fields

  1. While formula fields calculate values using fields within a single record, roll-up summary fields calculate values from a set of related records, such as those in a related list. 

  2. You can perform different types of calculations with roll-up summary fields. You can count the number of detail records related to a master record, or calculate the sum, minimum value, or maximum value of a field in the detail records. For example, you might want:

    * A custom account field that calculates the total of all related pending opportunities.

    * A custom order field that sums the unit prices of products that contain a description you specify.

  3. Master-detail relationships closely link objects together so that the master record controls specific behaviors of the detail and subdetail record. 

    * You define a roll-up summary field on the object that is on the master side of a master-detail relationship. For example, you can create a roll-up summary field on the Account object, summarizing related opportunities:

    * There are a few different types of summaries you can use. 

      - Count - Totals the number of related records.

      - Sum - Totals the values in the field you select in the Field to Aggregate option. Only number, currency, and percent fields are available.

      - Min - Displays the lowest value of the field you select in the Field to Aggregate option for all directly related records. Only number, currency, percent, date, and date/time fields are available.

      - Max - Displays the highest value of the field you select in the Field to Aggregate option for all directly related records. Only number, currency, percent, date, and date/time fields are available.

# Creating the Summary Field

  1. From Setup, open Object Manager and click Account. 

  2. On the left sidebar, click Fields & Relationships.

  3. Click New.

  4. Choose the Roll-Up Summary field type, and click Next.

  5. For Field Label, enter Sum of Opportunities and click Next. 

  6. The Summarized Object is the detail object that you want to summarize. Choose Opportunities.

  7. Choose the SUM summary type and choose Amount as the Field to Aggregate.

  8. Click Next, Next, and Save.

# Validation Rules 

  1. Validation rules verify that data entered by users in records meet the standards you specify before they can save it.

  2. A validation rule can contain a formula or expression that evaluates the data in one or more fields and returns a value of “True” or “False.” 

  3. Validation rules can also include error messages to display to users when they enter invalid values based on specified criteria.

  4. Using these rules effectively contributes to quality data. 

  5. Validation Rules Examples: 

    * Account Number Is Numeric - Validates that the Account Number is numeric if not blank.

      - AND(
        NOT(ISBLANK(AccountNumber)),
        NOT(ISNUMBER(AccountNumber))
        )
      
      - Error Message: Account Number is not numeric.

    * Date Must Be in the Current Year - Validates that a custom date field contains a date within the current year.
 
      -  	YEAR( My_Date__c ) <> YEAR ( TODAY() )

      - Error Message: Date must be in the current year.
      
    * Number Range Validation - Validates that the range between two custom fields, Salary Min and Salary Max, is no greater than $20,000.

      - (Salary_Max__c - Salary_Min__c) > 20000

      - Error Message: Salary range must be within $20,000. Adjust the Salary Max or Salary Min values.

    * Website Extension - Validates a custom field called Web Site to ensure its last four characters are in an explicit set of valid website extensions.

      - AND (
          RIGHT( Web_Site__c, 4) <> ".COM",
          RIGHT( Web_Site__c, 4) <> ".com",
          RIGHT( Web_Site__c, 4) <> ".ORG",
          RIGHT( Web_Site__c, 4) <> ".org",
          RIGHT( Web_Site__c, 4) <> ".NET",
          RIGHT( Web_Site__c, 4) <> ".net"
        )

      - Message: 	Web Site must have an extension of .com, .org, or .net.

    * Valid Billing Country 

      - OR(
        LEN(BillingCountry) = 1,
        NOT(
        CONTAINS(
        "AF:AX:AL:DZ:AS:AD:AO:AI:AQ:AG:AR:AM:" &
        "AW:AU:AZ:BS:BH:BD:BB:BY:BE:BZ:BJ:BM:BT:BO:" &
        "BA:BW:BV:BR:IO:BN:BG:BF:BI:KH:CM:CA:CV:KY:" &
        "CF:TD:CL:CN:CX:CC:CO:KM:CG:CD:CK:CR:CI:HR:" &
        "CU:CY:CZ:DK:DJ:DM:DO:EC:EG:SV:GQ:ER:EE:ET:FK:" &
        "FO:FJ:FI:FR:GF:PF:TF:GA:GM:GE:DE:GH:GI:GR:GL:" &
        "GD:GP:GU:GT:GG:GN:GW:GY:HT:HM:VA:HN:HK:HU:" &
        "IS:IN:ID:IR:IQ:IE:IM:IL:IT:JM:JP:JE:JO:KZ:KE:KI:" &
        "KP:KR:KW:KG:LA:LV:LB:LS:LR:LY:LI:LT:LU:MO:MK:" &
        "MG:MW:MY:MV:ML:MT:MH:MQ:MR:MU:YT:MX:FM:MD:MC:" &
        "MC:MN:ME:MS:MA:MZ:MM:MA:NR:NP:NL:AN:NC:NZ:NI:" &
        "NE:NG:NU:NF:MP:NO:OM:PK:PW:PS:PA:PG:PY:PE:PH:" &
        "PN:PL:PT:PR:QA:RE:RO:RU:RW:SH:KN:LC:PM:VC:WS:" &
        "SM:ST:SA:SN:RS:SC:SL:SG:SK:SI:SB:SO:ZA:GS:ES:" &
        "LK:SD:SR:SJ:SZ:SE:CH:SY:TW:TJ:TZ:TH:TL:TG:TK:" &
        "TO:TT:TN:TR:TM:TC:TV:UG:UA:AE:GB:US:UM:UY:UZ:" &
        "VU:VE:VN:VG:VI:WF:EH:YE:ZM:ZW",
        BillingCountry)))

      -  A valid two-letter country code is required.

# Defining Validation Rules

  1. From Setup, go to Object Manager and click Account.
  
  2. In the left sidebar, click Validation Rules.

  3. Click New.

  4. Enter the following properties for your validation rule: 

    * Rule Name: Account_Number_8_Characters

    * Error Condition Formula: 
  
      - e.g LEN( AccountNumber) != 8

      - If this condition is met, the entry is then invalidated 

  5. Error Message: Account number must be 8 characters long.

  6. To check your formula for errors, click Check Syntax.

  7. Click Save to finish.

# 
