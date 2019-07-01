# Dashboards

  1. Dashboards are your utility for summarizing and displaying your salesforce data in graphical layout

  2. Alows you to present mutilple reports side by side using dashboard components on a single dashboard page layout

  3. Come in a variety of chart types

  4. Customizable in terms of how data is grouped, summarized and displayed for each component

  5. Component types include

    * chart - show data graphically with a variety of chart types including pie chart, line charts and bar charts

    * guage - show single value to show within a range of custom values. Show progress towards a paritcular goal 

    * metric - one key value on display or single number

    * table - show a set of report data in column form like top 5 list

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
 
  8. Dashboard is a visual display of key metrics and trends for records for a organization. 

    * For each dashboard component, there is a single underlying report 

    * stored in folders which controls who has access. 

    * each dashboard has a running user, whose security setting determine which data is displayed in dashbaord. 

    * There is also dynamic dashboards for whcih the running user is always the logged in user.

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

# More on Dashboard 

  1. You can add dashboard to your pages and your custom apps. 

  2. You can view dashboard as other users than yourself. If you set view dashboard as admin, 
  other users will also run dashboard as admin which gives them view access to records and data they would otherwise not have access to. 
    
    * Running user setting overrides OWD, and other sharing settings or field level securities

  3. Historical trending

  4. Reporting snapshots

  