# So What Is a Salesforce Campaign?

  1. campaigns can help them track each of their marketing initiatives in detail.

  2. These can include typical advertisements and solicitations, emails, or more specialized marketing events like demos and conferences. 

  3. By tracking leads and contacts targeted by each initiative, as well as their responses, Margaret, the marketing manager, can tailor each campaign to the type of marketing effort it represents.

  4. Marketers use campaigns to analyze how many leads they’re generating, how much pipeline they’re building, and how many deals they’re closing as a result of marketing efforts.

  5. With campaigns, you can group your marketing programs together into hierarchies for greater visibility into the results of a large group of campaigns. 

    * Jamie sees a chance to wean Margaret off her spreadsheets with Campaign Path, an optional component that shows how a campaign is moving through the pipeline. 

    * With the Calendar object, for example, Margaret can see all her current and planned campaigns by month, day, or year.

# Let’s Create a Campaign

  1. Note: Select the Marketing User checkbox in your user profile and make sure you have permission to create campaigns. Your admin can give you that permission if you don’t already have it.

  2. To check whether you have the Marketing User option in your user profile, go to Setup and enter Users in the Quick Find box.

  3. Click Users and then your username. Then look for the Marketing User checkbox on the user detail page. If the box isn’t checked, edit the record and select the checkbox.

  4. To create first campaign, From the Campaigns tab, click New.

  5. Enter a name for the campaign.

  6. Select a campaign type, such as advertisement, email, webinar, conference, and so forth.

  7. Select a status for the campaign.

  8. For now, enter an estimate for Budgeted Cost and Expected Revenue.

  9. Enter a description.

  10. Click Save.

# Hierarchies to the Rescue

  1. By using the Parent Campaign field on her campaigns, Margaret can relate her campaigns to each other in a hierarchy. 

  2. With a hierarchy, she can group her campaigns into categories that suit her business.

  3. There are a few different ways hierarchies can be applied to a business’s marketing practices. 

    * A common approach is to use the hierarchy to group campaigns by marketing strategy. 

    * The hierarchy can have as many levels as she wants, but three levels works well for many companies. 

    * The top level can represent an overall strategic focus, such as selling a new product in a company’s lineup, or building brand awareness.

    * The second level can be for the different aspects of that focus, like the product launch, getting feedback from purchasers, or upselling previous customers.

    * Finally, the third level can represent individual marketing efforts, like an email, an online ad, invitations to demos, or the demo itself.

    * Another way of using hierarchies is to group campaigns by time period. In this approach, the top level can be for the marketing efforts for the entire year, the second level can be for each fiscal quarter, and the third level for individual campaigns in each quarter.

    * A third way of using hierarchies is to use the first level for a large event, such as an annual conference. The second level can then be for supporting marketing efforts like the registration and emails, and the third level can be for individual sessions at the conference. 

  4. With her campaigns in a hierarchy, Margaret will be able to see the results not just for individual campaigns, but also for whole sections of the hierarchy. This means that she’ll be able to see the overall results for the entire product launch, and for the entire new product strategy. That’s just what she needs.

    * To make a campaign a child of another campaign, all Margaret has to do is:

      - Create the parent campaign.

      - Create the child campaign and enter the parent campaign name in the Parent Campaign field.


# Get Specific with Record Types

  1. Jamie tells her that with record types, she can create customized campaign records for each type of campaign she runs. So for example she can have one record type for email campaigns, another for demo events, and so on.

  2. Her email campaign record type can include a field for the email template used, while her demo event record type can have custom fields for things like the location, timing, equipment needed, staffing, and whatever else she needs to track

# Add Prospects to Your Campaigns

  1. With each campaign she creates, she can then add leads, contacts, and person accounts as campaign members. There are a lot of options for adding members to her campaigns.

    * Add a lead, contact, or person account individually from their record detail page.

    * Add one or more members by clicking Manage Campaign Members from the dropdown menu on the Campaign Members related list.

    * Add one or more leads by clicking Add Leads from a campaign’s Campaign Member related list.

    * Add contacts from an account by clicking Add Contacts in the Campaign Members related list on a campaign and searching for the account name.

    * Add members from the Contacts related list on an account detail page.

    * Add members from a lead, contact, or person account list view.

    * Add members from lead or contact report results.

    * Import or add existing leads, contacts, and person accounts to a campaign with the Data Import Wizard.

  2. When you have decided on a set of member statuses that works for each kind of campaign you run, add those values when you create each campaign.

    * To have Salesforce automatically track the number of members who have responded to your campaigns, note which of your statuses you’d like to count as responses

    * You do this by checking the Responded box next to the value in the Campaign Member Statuses related list. 

    * If you don’t see the Campaign Member Statuses related list, ask your admin to add it to campaign detail pages.

  3. To add campaign member statuses to a campaign,

    * On the campaign detail page, click New in the Campaign Member Statuses related list.

    * Enter a name for the status.

    * If you’d like the status to show that your prospect has replied to the campaign, click the Responded option and then click Save.

# What Else Can You Learn About Your Campaigns?

  1. With built-in campaign reports, Margaret can easily see who her campaigns are targeting, who has responded to each campaign, and how much revenue they’re generating.

  2. You can find the built-in campaign reports by clicking the Reports tab, then New Report, and then Campaigns from the list of report types. The Campaigns report folder contains several reports.

  3. To see who her campaigns have targeted, Margaret can look at the Campaigns with Contacts or Campaigns with Leads reports.

  4. The Campaigns with Contacts report lists each of your campaigns and all of the contacts associated with them.

  5. The Campaigns with Campaign Members report shows how many campaign members—including any combination of leads, contacts, and person accounts that you added to your campaigns—have responded to each 

  6. The Campaign with Opportunities report shows all the opportunities generated by your campaigns. Add the Amount field to see the revenue from each opportunity. You can filter the report to show only closed deals to focus on revenue generated, or show all deals to focus on pipeline built from your marketing efforts.

  7. You can group report results by campaign type to see how your email campaigns or events are performing. The custom fields you add to your campaign greatly affect the level of detail you get with reports. For example, capturing fields like campaign focus or product let you report on the success of marketing efforts in those specific areas.