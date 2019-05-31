# Sales Process
  1. Sales Process starts with a lead or in case of salesforce a prospect
  2. leads or prospect are interested in your products or services but have not yet commited to your product
  3. Sources are where you get your leads in salesforce
  4. Salesforce activities are tasks, calls, and events that track in relation to the lead. 
  5. When lead is converted, they are pushed into Account, Contact and Opportunities
    * Note that opportunities are potential revenue generating deals that sales rep track in the sales cycle
    until the dael is closed. 

# Opportunities Tab in Salesforce
  1. Multiple stages involved for an Opportunity in salesforce
    * Example of what a Opportunity stages might look like 
      - Prospecting
      - Developing
      - Negotiation/Review
      - Closed/Won
      - Closed/Loss
  2.  Stages can be customized for specific needs and processses
    * You can change name of each stage or add new ones 
    that intuitive for your salespeople
  3. Contact roles for opportunities tell you which contacts
  you're dealing with for the opportunity and how they are related to that opportunity or what their role is
  4. You can also create opportunity team when it is a team rather than a individual that is closing a deal
    * more common than a solo contact

# Leads or Prospect
  1. They are optional though there are advantages to using them
    * Advantages include
      - knowing who is in your pipeline
      - track deals, reporting them and target them with marketing campaigns
      - help make decisions or concentrate on potential deals most likely to close

  2. Leads by default belong to the administrator who set up that process but you can manually assign it to someone who is more appropriately associated with the lead. 

  3. Qualifying a lead means you can convert a lead record into a opportunity record which you then try to close out
  
# Regional Company Settings 

  1. Your company settings are the collection of information about your organization. This collection is mostly captured when you purchase a Salesforce product, but you can update the settings if your company moves operations or expands globally.

  2. What the company settings consist of:

    * Company Information
        
      - Name and Address - Used for billing and support 

      - Primary contact - also used for billing and support 

      - Default locale - Updating this one setting determines the way a ton of information is displayed within Salesforce

      - Default currency - Currency applied to records 

      - Currencies - Lists all currencies used in the org 

      - Storage Used - puctures, documents etc

      - Lincenses Available - Includes Salesforce and feature license 

    * Fiscal Year Information

      - Fiscal Year - Used in reporting and forecasting 
    
    * Support Information 

      - Business Hours - These are used when escalation rules do their escalating 

      - Holidays - Days that cases skip escalation 

  3. What are Locale Settings 

    *  The Salesforce locale settings determine the display formats for date and time, users’ names, addresses, and commas and periods in numbers

      - Displaying information to your users in a familiar way improves users’ Salesforce experience and makes them more efficient secret agents. 

    * As the admin, you set the default locale, but your users can set a personal locale if they’re based in a different location

  4. Locale Settings include

    * Locale 

      - Date and Time Format - mm/dd/yyyy or dd/mm/yyyy 

      - Number Format - 1,000 or 1.000 for one thousand 

      - Name Order - Last, First or First Last 

      - Address Format - Country, Zip Code, State, then Street 

      - Phone Number Format - (123) 456-7890 or +12 2345 67-0 

    * Language

      - All Text - Standard tabs and fields

      - Online Help - Text language in Help 

    * Time Zone

      - Event Start/End Time - Calendar entries and events 

      - Date or Time Fields 

# Update Company Information 

  1. Go into Setup

  2. Enter Company Information in the Quick Find box and select Company Information. This page displays your org’s address, locale, time zone, currency, and lets you view storage used and licenses.

  3. Click Edit.

  4. Update the information related to your new location: 

  5. Click Save.

# Update Fiscal Year 

  1. From Setup, enter Fiscal Year in the Quick Find box, then select Fiscal Year.

  2. Change the Fiscal Year Start Month to July. 

    * Note: You can also opt to change whether the fiscal year is based on ending or starting month or configure a completely custom fiscal year.

  3. Keep the other settings and click Save and then OK.

# Update Your Personal Locale
  
  1. In the header, click your profile icon and select Settings.

  2. Enter Language in the Quick Find box, then select Language & Time Zone.

  3. From this Settings area, the user selects the Time Zone, Locale, and Language that match their situation. 
  
    * For our example, we select the Pacific time zone, English (United States) locale, and Portuguese language. Note: Don’t do this now or your Salesforce org will display all UI in Portuguese. (Unless of course you speak Portuguese, and then go for it!)

  4. If multicurrency is enabled and configured (we show you how in the next unit) you can also set the personal currency here—in this case the Brazilian Real.


  5. Click Save.

