# Approvals in Chatter 

  1. Approval processes define the steps to take to approve a record in Salesforce and identify the person who provides approval at each step.

  2. You can configure the approval process to send out an approval request as a Chatter post.

 # Enable Approvals Requests in Chatter

  1. From Setup, enter Chatter Settings in the Quick Find box, and then click Chatter Settings.

  2. Click Edit.

  3. In the Approval Posts section, select Allow Approvals.

# Create a Post Template

  1. You’d like the approval posts that appear in Chatter to be standardized. From Setup, enter Post Templates in the Quick Find box, and then click Post Templates.

  2. Click New Template.

  3. These approvals are for accounts, so select Account and click Next.

  4. Enter the name Account Approval Post Template, and describe it as A template for account approval request posts.

  5. Make this template the default for all account approval request posts by selecting Default.

  6. For Post Template Fields, move Account Number, Account Owner, and Description to the right column. If Account Name isn’t already in the Selected Fields column on the right, move it there, too.

  7. Click Save.

# Create an Approval Process

  1. From Setup, enter Approval Processes in the Quick Find box, and then click Approval Processes.

  2. For Manage Approval Processes For, choose Account.

  3. Click Create New Approval Process, and choose Use Jump Start Wizard.

  4. In the Approval Process Information section

    * For Name, enter: Account Approval Process.

    * To get a unique name for this process to use in the API, click the Unique Name field.

    * Leave Approval Assignment Email Template blank to use the default email template.

    * For Approval Post Template, click the search icon and select Account Approval Post Template. We created this template in the last section.

    * To update all the page layouts for this object, select Add the Submit for Approval button and Approval History related list to all Object page layouts.

  5. In the Specify Entry Criteria section, set up the criteria to kick off this approval process.

    * In our example, we want Allison Wheeler to approve any accounts that she doesn’t own, so we enter these criteria on the first line.

        - Field: Account: Account Owner

        - Operator: not equal to

        - Value: Allison Wheeler

  6. In the Select Approver section, assign all approval requests to Allison Wheeler.

    * Select Automatically assign to approver(s).

    * Select User, and, in the second field, enter Allison Wheeler.

    * Under When multiple users are selected, select Approve or reject based on the FIRST response. If you want all selected approvers to approve, select Require UNANIMOUS approval from all selected approvers.

  7. Click Save.

  8. Click View Approval Process Detail Page.

  9. On the Account: Account Approval Process page, click Activate to activate the approval process.


# Chatter Rollout Strategy

  1. It is critical to develop a Chatter rollout strategy
 
  2. Identify key people to be Chatter champions

    * Executive Sponsor - This person must believe in the power of social collaboration and Chatter. They must be willing to invest time to make Chatter collaboration a success

    * Evangelist - people at your company who have incredible knowledge and already love social collaboration. Your evangelists can help answer questions, encourage other users who are nervous about posting, create and manage groups, and curate content.

    * Community Manager - You need a Community Manager curating quality content and driving user engagement. Examples of great content include helpful files, links to industry news articles or videos, and posts about events or exciting announcements at your company. 
 
  3. A great Chatter rollout needs a solid communication plan. 

    * Create marketing content - ou can send drip emails and videos to advertise that Chatter is coming. Consider allocating budget for fun swag or a launch party with cake and balloons

    * Create a schedule - Choose your launch date carefully. Avoid busy times for your company (for example, the last day of the sales month) and holidays. It’s a general best practice to turn on Chatter after hours. Once you’ve decided on your launch date, create a schedule for your pre-launch communication.

  3. Chat ettiquite - Consider putting together a simple list of guidelines for user behavior. Publish the list and share it with your users. Post it in a public place, like an All Company Chatter group.

    * Put mentions in comments. Placing mentions in comments prevents anyone or any group that’s mentioned from getting notified repeatedly whenever there’s action on the post.

    * Use mentions thoughtfully. You can make every name you enter a mention, but it counts most when a mention triggers a less-frequent and more meaningful notification. 

    * Make mentions count. Where your post lives can impact whether the person or group you mention is notified or has access to the post. Check out the following table for examples.

# Identify Use Cases

  1. An All-Hands Chatter group for company-wide collaboration during quarterly or annual company calls. If your teams are geographically distributed or you have remote employees, an all-hands group is especially important.

  2. A #CorporateGoals Chatter topic to highlight and share around a key company objective. If your company decides it’s the year for giving back, make giving back a topic (#givingback). Encourage your employees to share how they’re giving back in Chatter, and advise them to mark those posts with #givingback. Topics can promote company-wide collaboration and the visibility of company objectives (#CorporateGoals).

  3. A series of quick polls to gauge employee reaction to a planned product enhancement. If you’re looking to get fast feedback while you iterate, consider informal polling in Chatter. Collect insights from your employees with a quick, one-question poll, and draw your employees’ attention to the poll by @mentioning groups and users.

  4. A Competitive Strategy Chatter group where you can share insights on your competitors, access files and tip sheets, and get quick answers from experts.

  5. An Event Planning Chatter group where you can collaborate while planning a department event. Collaborate on the slides for the event, schedule speakers, share details on the agenda. Even invite external vendors who could be supplying food, drinks, or equipment to coordinate all the details.

# Create a Communication Plan

  1. Create Marketing Content

    * You can send drip emails and videos to advertise that Chatter is coming. Consider allocating budget for fun swag or a launch party with cake and balloons. Making the launch of Chatter an event for your company helps to build excitement and momentum.

  2. Create a Schedule

    * Choose your launch date carefully. Avoid holidays and busy times for your company (for example, avoid the last day of the sales month). It’s a general best practice to turn on Chatter after hours. Once you’ve decided on your launch date, create a schedule for your pre-launch communication. Here’s a sample communication schedule.

  3. Measure Results

    * Once you’re live, you can track your results. Download Chatter Usage Dashboards from AppExchange. You can also download the Chatter Challenge Dashboard to monitor Chatter group and following activity.

    * Your Community Manager can use these dashboards to monitor the overall health of your Chatter adoption. Your Community Manager can also conduct surveys, either using Chatter polls or through focus groups, to gauge the response to Chatter and prioritize future work.

# Profile-Based Chatter Rollout Overview

  1. Profile-based rollout of Chatter enables Chatter for a subset of users instead of all users in the organization.

  2. A Chatter profile-based rollout makes Chatter available for a part of your organization, but not for all users. Once profile-based rollout is enabled for your organization, you can turn enable Chatter for the users with the required user profile or permission sets. All other users in your organization don’t have access to Chatter. 