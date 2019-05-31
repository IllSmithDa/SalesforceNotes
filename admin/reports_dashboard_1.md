# Reports and Dashboard
  1. Reports typically come in form of a question which can include 

    * Which products are my top sellers? 
    
    * Who are my highest value prospects? 

    * Which marketing campaign have been the most successful? 

    * How satisfied are my customers?

  2. It can also include follow up questions as well 

    * Original question is Which products are my top sellers?

      - followup questions: What makes a product a top seller, revenue or quentity

      - Do you want to see the results grouped by product family?

      - What is your date range

  3. You then also define requirements for top products such as 

    * "Top sellers" here means quantity rather than revenue

    * group products by product family

    * show all closed/won opportunities

    * do not show inactive products

  4. Finally you also include a criteria in your report such as 

    * report type = Opportunities with product

    * grouping = product family

    * show = all opportunities

    * range = current FY 

    * filter = product 'equals' active

  5. Report overall is a list of records that meet the criteria you define. Its displayed in Salesforce rows and columns, and can be filtered, grouped, or displayed in a graphical chart

    * Every report is stored in a folder which can be publi, hidden, or shared and set to read/write

    * You control who has access to the contents of the folder based on roles, permissions, public groups, and license types.

  6. Dashboard is a visual display of key metrics and trends for records for a organization. 

    * For each dashboard component, there is a single underlying report 

    * stored in folders which controls who has access. 

    * each dashboard has a running user, whose security setting determine which data is displayed in dashbaord. 

    * There is also dynamic dashboards for whcih the running user is always the logged in user. 

  7. Report type - is like a template which makes reporting easier and contains 

    * The report type determines which fields and records are available for use when creating a report. This is based on the relationships between a primary object and its related objects.

      - For example, with the ‘Contacts and Accounts’ report type, ‘Contacts’ is the primary object and ‘Accounts’ is the related object.

# Benefits of Reports and Dashboards 

  1. Visibility into data—reports and dashboards give you easy access to key data insights, which helps managers make better decisions.

  2. Time savings — you don't have time to manually dig through all your many objects, records, and fields to pull together answers to your manager's questions. Reports give you a quick way to answer both simple or complex questions.

  3. Flexibility—with reports and dashboards you can pull data from all your standard and custom objects and fields. You have many powerful options for tailoring reports and dashboards to the specific needs of your end users.
  
#Report Builder 
  1. Criteria you enter is essentially a question and results are the answers to that question. 
  
  2. Report type refers to the object type by which you are querying records
    * e.g For Contacts and Accounts, the only records displayed in the report are Contacts that have at least one related Account records
  
  3. Results when report building fall into one of two categories

    * Primary object with related object

      - Records returned are only those where the primary object has at least one related object record. In our example of Opportunities with Products, theonly records that would be displayed on the report would be opportunities that have at least one related product record.

    * Primary object with or without related object

      - Records returned are those where the primary object may or may not have a related object record. If we were to create a custom report type, Opportunities with or without Products, then opportunities would be displayed whether or not they have a related product record.

    * never usually just the related object on its own or pimary object on its own

  4. There are many filter types when building your report

    * standard filter - default filter which include standard filters such as 'Show Me' and 'Date'

    * field filter - filter based on different fields, list views, workflow rules 

    * filter logic - add boolean logic to control how fields are evaluated 
    
    * cross filter - filter a report by child object using with or without conditions. 

      - extend your report types to objects related to the original objects defined in the report type.

      - e.g Accounts with Opportunities, select Opporunity filter with Opporunity Name equals ACME subfilter to include only those opportunities

    * row filter -  For tabular reports, select the maximum number of rows to display
  
  5. These filters have 3 basic operations 

    * AND - find records that match both values

    * OR - find records that match either values

    * NOT - find records that match neither values

  6. The four different types of reports are : tabular (default), summary, matrix, and joined

  7. Report builder is automatically enabled in new Salesforce organizations. For existing organizations, you may need to enable it. If report builder is automatically enabled in your Salesforce organization, then you won’t see any options to turn it on or off in Setup. It’s always on!

    * If report builder isn’t automatically enabled in your Salesforce organization, then you can verify that it’s turned on in Setup. Enter Reports and Dashboard Settings in the Quick Find box, then select Reports and Dashboard Settings. Review the Report Builder Upgrade section of the page, and if necessary, then click Enable. If you don’t see the button, report builder has been enabled for your organization. Confirm your choice by clicking Yes, Enable Report Builder for All Users.

# Cross Object Filters

  1. Cross Object Filters allow you to extend your report types to objects related to the original objects defined in the report type. 

  2. Cross filters help you fine tune your results, without writing code or using formulas. 

  3. Some Examples include: 

    * Stale Opportunities - Opportunities without activities in the past 30 days. 

    * Orphan Contacts -  Contacts without accounts

    * Neglected Accounts - Accounts with no opportunities

# Tabular Reports
  
  1. Fastest and simplest way to look at your data 

  2. similar to spreadsheet, they consist of ordered sets of fields in columns with each matching record listed in a row

# Create Tabular Reports 

  1. On Reports, click New Report, choose the ‘Opportunities’ report type, and click Continue.
  
  2. Click FILTERS, then apply the following filters:

    * For the Show Me standard filter, select All opportunities and click Done.

    * For the Opportunity Status standard filter, select Open and click Apply.

    * For the Date Field standard filter, select Created Date and Current FY for the range and click Apply.

  3. Name your report and enter a description 

  4. Click Save and then you can run

# Summary Reports

  1. Similar to tabular reports, it allows users to group rows of data, view subtotals and create charts

  2. Most common and often seen type of report

  3. can contain graphs and used in dashboards 

    * Summary reports give us many more options for organizing the data, and are great for use in dashboards. 

# Create Summary Reports

  1. From the Reports tab, click New Report, choose the ‘Cases’ report type from the Customer Support Reports folder, and click Continue.

  2. Click FILTERS, then apply these standard filters:

    * For Show Me, select All Cases and click Apply.

    * For Date Field, select Opened Date and All Time for the range. Then click Apply.

  3. To make this report a summary report, you need to group rows. To group rows, first click OUTLINE.

  4. Under GROUP ROWS, from the Add group... picklist, select Priority.

  5. Turn off Detail Rows at the bottom of the preview page to see just the totals for each priority level.
  
  6. Name your report and enter a description 

  7. Click Save and then you can run


# Matrix Reports

  1. Matrix reports allow to group records both by row and column

  2. time consuming but provides to most deatiled view of your data

  3. can contain graphs and used in dashboards 

# Create Matrix Report 

  1. On the Reports tab, click New Report, choose the ‘Opportunities’ report type, and click Continue.

  2. Click FILTERS, then apply these standard filters:

    * For the Show Me standard filter, select All Opportunities and click Done.

    * For the Opportunity Status standard filter, select Closed Won and click Apply.

    * For the Date Field standard filter, select Close Date. For Range, select Current FY. Click Apply.

  3. To summarize the report by Sum of Amount, click the More actions dropdown arrow on the Amount column. Then, click Summarize and select Sum.

  4. To change the report format to matrix, first group rows by Close Month and columns by type. To start grouping, click Outline.
    
    * Under GROUP ROWS, from the Add group... picklist, select Close Month.

    * Under GROUP COLUMNS, from the Add group... picklist, select Type.

  5. You may want to hide the report details when viewing a matrix report. Matrix reports are usually easiest to consume with details hidden. To hide the report details, turn off Detail Rows. 

  6. Name your report and enter a description 

  7. Click Save and then you can run

# Joined Reports

  1. lets you create different views of data from multiple report types. 

  2. Data or each report  is organized by blocks and blocks act like sub reports with its own fields, columns, sorting, filtering

    * can hold up to 5 block or 5 different reports

  3. You can add charts to a joined reports

# Dashboards

  1. Dashboards are your utility for summarizing and displaying your salesforce data in graphical layout

  2. Alows you to present mutilple reports side by side using dashboard components on a single dashboard page layout

  3. Come in a variety of chart types

  4. Customizable in terms of how data is grouped, summarized and displayed for each component

  5. Component types include

    * chart - show data graphically with a variety of chart types including pie chart

    * guage - show single value to show within a range of custom values

    * metric - one key value on display

    * table - show a set of report data in column form 

    * visualforce page - custom made component

  6. Dashboard filters - You can make dynamic dashboards to provide different combinations of data from a single dashboard

    * Filters can’t be added to dashboards that contain Visualforce components.

    * It’s not possible to filter on bucket fields. However, it is possible to use a report filtered on a bucket field on the dashboard page.

    * Filters aren’t applied when you schedule or email a dashboard.

    * You can’t filter data on a joined report in dashboard view or add a filter to a dashboard that only has joined reports.

  7. Dynamic Dashboards

    * With dynamic dashboards, each user sees the data they have access to without needing to create separate dashboards for each user. 

    * This means a single powerful dashboard can be used for multiple users in your company, as data only gets selectively shown based 
    on user's security clearance

    * up to three dyanmic filters can be used per dashboard

# Creating Dashboards

  1. From the Dashboards tab, click New Dashboard.

  2. Name your dashboard and, optionally, enter a description.

  3. Click Create. 

  4. To insert a component, click + Component.

  5. From Select Report, choose the Leads report you created earlier and click Select. From Add Component, select the donut chart.

  6. Optionally give your component a subtitle and footer.

  7. Click Add. Your new component appears on the dashboard.  

  8. Optionally, resize your dashboard component by clicking on it, then dragging the corners and sides.

  9. Click Save and then click Done

# Dynamic Dashboards 

  1. With dynamic dashboards, each user sees the data they have access to without needing to create separate dashboards for each user. 

    * This means a single powerful dashboard can be used for multiple users in your company, because the logged-in user viewing the dashboard sees the data they should see, based on their security and sharing settings. 

    * It also lets you selectively choose which part of the data a user can see as well as who can see the dashboard in general

# Set up a Dynamic Dashboard

  1. From the Dashboards tab, create a new dashboard or edit an existing one.

  2. Open the Properties menu

  3. Under View Dashboard As, select who people view the dashboard as:

    * Me — Dashboard readers see data in the dashboard according to your access to data.

      - For example, if you can only see Opportunities in Canada, then dashboard readers only see data about Opportunities in Canada.

    * Another person — Dashboard readers see data in the dashboard according to the data access level of whomever you specify. 

      - For example, if you choose someone who can see Opportunities from any country, then dashboard readers see data about Opportunities from all countries.

    * Optionally, select Let dashboard viewers choose whom they view the dashboard as to let a reader with appropriate user permissions choose who they view the dashboard as. With the “View My Team’s Dashboards” user permission, the reader can view the dashboard as themself or as anyone beneath them in the role hierarchy. With the “View All Data” user permission, the reader can view the dashboard as anyone. 

    * The dashboard viewer -  Dashboard readers see data as themselves, according to their own access to data. These types of dashboards are often called dynamic dashboards.

    * Your organization can have up to 5 dynamic dashboards for Enterprise Edition, 10 for Unlimited and Performance Edition, and 3 for Developer Edition. Dynamic dashboards aren’t available in other editions. Additional dynamic dashboards may be available for purchase.

  4. Dynamic Dashboard limitations: 

    * Dynamic dashboards don’t support following components.

    * You can’t save dynamic dashboards in private folders.

    * You can’t schedule refreshes for dynamic dashboards. They must be refreshed manually.

# Report Charts 
 
  1. If you don’t want to create a dashboard, but just want to add a chart to your report, then report charts may be right for you. Report charts allow you to place a single chart right at the top of your report, so that when you view the report, you can see the chart and the report results in one view.

  2. Here’s how you add a report chart:

    * From the Reports tab, open the report you made earlier, Leads by Lead Source.

    * A chart may already appear at the top of your report. You can show or hide the chart by clicking the chart icon (Chart button).

# Modifying an Existing Report 

  1. The very first thing you need to remember when modifying an existing report is to make a copy. The last thing you want to do is mess up someone else’s report! 

    * To make a copy of a report, open it and click Save As.

    * Give your copied report a name, choose the Private Reports folder, and click Save. You can always move it to another report folder later, but this is a safe place to experiment with reports before you’re ready to have others use them.

# Modifying an Existing Dashboard 

  1. As with reports, make sure you clone a copy so that you don’t mess up someone else’s dashboard! 

    * To clone the dashboard, open it up and click Clone. 
    
    * Enter a name, specify a folder, and click Create. Then click Edit to open the dashboard in edit mode in the drag-and-drop dashboard builder. Now you can see how the dashboard was initially created. Let’s take a closer look. 

# Folder Sharing 

  1. reports and dashboards get stored in folders each with its own permission settings

  2. folder sharing allows you to restrict access to reports and dashboards by users, roles and their subordinates, 
  territories, territories and their subordinates, and public and private groups

    * Three types of folder access 

      - viewer access - you can see data but not edit it except by cloning data 

      - editor access - you can view and modify the reports and dashboards it contains and move them to other folders

      - manager access - you can view, modify and control other users

# Scheduled Reports 

  1. reports done on a consistent basis. Could be monthly, weekly, or even daily basis 

  2. Scheduling report  benefits include 

    * gets the latest data without having to manually run a report each time 

    * gets the data automatically periodically

    * get the report in HTML format with a link for easy access to the source report 

# App Exchange
  1. there are sample report and dashboard packages available from Salesforce Lab

  2. best practice is to install first in a sandbox. With reports and dashboards, here are a few considerations:

    * Some of the packages come bundled with a handful of custom fields. 

    * Reports, dashboards, folders, and custom fields all have names, which may conflict with existing names in your org.

    * Packages all come with report and/or dashboard folders. 

  3. The very first thing you need to remember when modifying an existing report is to use ‘Save As’. The last thing you want to do is copy over someone else’s report! 

  4. You can also clone dashboards

    * This will open up the dashboard in edit mode in the drag-and-drop dashboard builder. Now you can see how the dashboard was initially created
