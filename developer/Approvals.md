# Get Started with Approvals

  1. An approval process automates how Salesforce records are approved in your org. In an approval process, you specify:

    * The steps necessary for a record to be approved and who approves it at each step. 

      - For example, when an employee creates a time-off request, have Salesforce automatically send an approval request to the employee’s manager.

    * The actions to take based on what happens during the approval process. 

      - For example, if a time-off request is approved, update fields on the employee’s record. But if the request is rejected, send a notification to the employee.

  2. When a user first requests approval for a new position, initial submission actions occur. 

    * If the direct manager rejects the request, the final rejection actions are executed, setting the position’s approval status to Rejected.

    * If the direct manager approves the request, the record moves to the next step—approval from the CEO. If the CEO rejects the position, the same final rejection actions occur.

    * If the CEO approves the position, final approval actions are executed. They set the approval status to Approved, unlock the record for future updates, and notify the employee who requested the new position.

# More on Approval Processes 

  1. If a record of a object - lets say a entry or record for Opportunity does not meet a criteria for an approval, it will not be used when we click Submit Approval. 

  2. Though an Admin can move onto the next steps in the case of a rejected approval, a regular salesforce user will not be able to. 

  3. Once the approval has been edited and approved, the user will be able to move onto the next step. This is a class case of how approvals work in the real world. 

# Build an Approval Process - You need to make sure that a manager approves opportunities that are discounted more than 40%. The opportunity should reflect its approval status: Approved or Not Approved.

  1. Create an Email Template

  2. From Setup, enter Templates in the Quick Find box, and then select Classic Email Templates. 

  3. Click New Template.

  4. Select Text as the template type, and click Next. 

  5. Configure the email template. 

  6. Click Save.

  7. Add Custom Fields by doing the following: 

  8. From Setup, enter Object Manager in the Quick Find box, and then select Object Manager.
  
  9. Click Opportunity.

  10. Select Fields & Relationships and click New.

  11. n the Data Type column, select Percent and then click Next.

  12. Add a Percent field with these values.
Field

# Create an Approval Process

  1. From Setup, enter Approval in the Quick Find box, and then select Approval Processes.

  2. For Manage Approval Processes For, select Opportunity.

  3.  Click Create New Approval Process | Use Jump Start Wizard. The Jump Start Wizard helps you create a simple approval process by making some decisions for you.

  4. Configure the approval process.

  5. Save the approval process.

  6. Click View Approval Process Detail Page.

  7. Under Final Approval Actions, click Add New | Field Update, and configure it 

  8. Click Save.

# Make Sure That Records Are Submitted

  1. You've done a bunch of work to automate what happens when a record gets submitted for approval. Now, when users click Submit for Approval on an opportunity, it goes through your approval process. But what if—the horror—users forget to click the button?

  2. Enter Process Builder. One of the available process actions is Submit for Approval, which means you can build a process that automatically submits records for approval. And that means your users don’t have to remember to submit opportunities for approval. For example, in a process that runs when opportunities are created or edited:

    * Add a criteria node that checks whether Discount Percent is greater than 0.4.

    * Add a Submit for Approval action that submits the opportunity for approval.
    