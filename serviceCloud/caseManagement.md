# Case Management
    
  1. A case is a customizable record in Salesforce that tracks and describes a customer issue, complaint, request—you name it. 
    
  2. All unifying information about a customer is stored on a case, including account, contact, product, and history data so that anyone on your service team can jump in to help. 

  3. Case is ultimately just another standard object. 

  4. Can be high fequency: call center model 

    * phone: automated, manual, call routing

    * web/email: case submissions, email notifcations, etc. 

  5. service process

    * log a case

    * capture details

    * route to right persons

# Add an Case Assignment Rules 

  1. From Service Setup, enter Case Assignment Rules in the Quick Find box, then select Case Assignment Rules.

     * Note that only one person can be assigned to a case at a time 

  2. Click New.

  3. Add Assignment rule name and click Save.

  4. Select the rule you just created, and next to Rule Entries, click New.

    * Here’s where we add the little details that determine case assignment.

  5. In Sort Order, type 1 so that the entry we add is processed first. Typically, you’d create one assignment rule with many different entries, which are processed in chronological order. When a case matches an entry, it’s assigned without proceeding to other entries. 

  6. For entry criteria, select Case: Case Reason equals Installation.

    * One of the many useful things about case assignment rules is that you can determine how cases are assigned based on fields from records other than cases. For example, you can choose case assignment based on fields from accounts, contacts, assets, or users.

  7. Add yourself as the User assigned to the rule entry. We assume you’re a support agent who’s an expert at solar panel installation. 

  8. In Email Template, click the lookup and choose a template so that you receive an email whenever a case with an installation reason is assigned to you. 

  9. Click Save.

  10. Click Edit to mark the rule as Active, then click Save.

    * When you activate an assignment rule, it disables any other assignment rules in your organization, so make sure that your active rule includes all of the assignment entries that your support team needs.

# Define When Cases Escalate

  1. From Service Setup, enter Escalation Rules in the Quick Find box, then select Escalation Rules.

    * Used eithr for a high priority case or a case that has been active for too long. 

  2. Click New.

  3. Type Gold Support, then click Active and Save. Activating a rule deactivates any existing active rules.

  4. Select the rule you just created, and click New to add a rule entry.

    * Here’s where we add the details that determine when the case gets escalated. 

  5. In Sort Order, type 1 so that the entry we add is processed first. 
  
    * In the real world, you’d create one escalation rule with many different entries, which are processed in chronological order. 
    
    * When a customer issue comes in and is converted to a case, it’s assigned based on the first entry it matches.

  6. For entry criteria, select Case: Status equals New.

    * Similar to other rules, you can determine automatic case escalation based on fields from records other than cases.

  7. Set business hours to your organization’s default 24/7 support.

  8. Set that escalation times are based on when cases are created.

  9. Click Save, then New to add an escalation action.

  10. In Age Over, enter 5.

    * Here, 5 is the number of hours at which cases escalate when they have a status of New. Remember, we want cases Closed after 5 hours. 
    
    * You can set up escalation actions in 30 minute increments by clicking 0 minutes and selecting 30 minutes.

  11. Auto-assign cases to you, and from Notification Template, click the lookup icon to pick any template. At a real company, you’d assign cases to a support manager or team. 

  12. Select yourself as the user to notify, and from Notification Template, click the lookup icon to add a template to see how this works.

  13. Click Save.

# Define When Cases Escalate

  1. From Service Setup, enter Escalation Rules in the Quick Find box, then select Escalation Rules.

    * Used either for a high priority case or a case that has been active for too long. 

  2. Click New.

  3. Type Gold Support, then click Active and Save. Activating a rule deactivates any existing active rules.

  4. Select the rule you just created, and click New to add a rule entry.

    * Here’s where we add the details that determine when the case gets escalated. 

  5. In Sort Order, type 1 so that the entry we add is processed first. 
  
    * In the real world, you’d create one escalation rule with many different entries, which are processed in chronological order. 
    
    * When a customer issue comes in and is converted to a case, it’s assigned based on the first entry it matches.

  6. For entry criteria, select Case: Status equals New.

    * Similar to other rules, you can determine automatic case escalation based on fields from records other than cases.

  7. Set business hours to your organization’s default 24/7 support.

  8. Set that escalation times are based on when cases are created.

  9. Click Save, then New to add an escalation action.

  10. In Age Over, enter 5.

    * Here, 5 is the number of hours at which cases escalate when they have a status of New. Remember, we want cases Closed after 5 hours. 
    
    * You can set up escalation actions in 30 minute increments by clicking 0 minutes and selecting 30 minutes.

  11. Auto-assign cases to you, and from Notification Template, click the lookup icon to pick any template. At a real company, you’d assign cases to a support manager or team. 

  12. Select yourself as the user to notify, and from Notification Template, click the lookup icon to add a template to see how this works.

  13. Click Save.

# 