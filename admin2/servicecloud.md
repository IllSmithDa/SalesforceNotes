# What Is Service Cloud?

  1. Service Cloud is an easy-to-use customer service application that can help you provide and track excellent service. 

  2. It keeps your customers happy and your support team sane, whether your customers reach out to you by email, phone, social media, or other channels from desktops, mobile devices, or apps. 

# Service Cloud Features

  1. Service Console

    * At the heart of Service Cloud is the Service Console. The console is a help desk that lets anyone on your service team (or anyone at your company) see a personalized view of each customer and their case. 

  2. Case Management
    
    * A case is a customizable record in Salesforce that tracks and describes a customer issue, complaint, request—you name it. 
    
    * All unifying information about a customer is stored on a case, including account, contact, product, and history data so that anyone on your service team can jump in to help. 

    * Case is ultimately just another standard object. 

    * Can be high fequency: call center model 

      - phone: automated, manual, call routing

      - web/email: case submissions, email notifcations, etc. 

    * service process

      - log a case

      - capture details

      - route to right persons

  
  3. Channels and Digital Engagement

    * Whether the case arrived by email, phone call, web chat, social media, or text message, a support agent can quickly respond to it from the console. Agents can track any useful information and engage with customers on their favorite channels, devices, or apps to provide a great service experience.

  4. Automatic Workflows

    * When a case arrives, its information is automatically assessed and routed to the right people to match any custom workflows set up for your team.

    * Notifications keep your service team on track before they miss any key times, required responses, or service agreements. 

  5. Knowledge Base

    * Find, share, and store articles or answers related to cases to speed up service. Or, let customers find answers on their own from your self-service website or community. 

  6. Instant Metrics

    * Information about cases is available in service metrics to gauge your business’s response times, resolution times, and overall service health. Use data to identify strengths and gaps; and make decisions on how to deliver better, faster service. 

  7. Mobile & Field Service Ready

    * Since Service Cloud is part of the Salesforce platform, all of your business data, customized processes, and unique workflows come together in one simple place. You can even see it all on your mobile phone or tablet out in the field. 

  8. Automatic Updates for the Future

    * With each Salesforce release, you automatically get the latest technologies to position your support team for the future and the Fourth Industrial Revolution, including artificial intelligence (AI) for predictive service

# Set Up Service Cloud

  1. Service Setup is where you connect your customers to your service center. Think of it as a dashboard for all things service. 
  
    * Whether you need to turn emails into cases, integrate with Twitter and Facebook, enable a knowledge base, or create a web community, you do it all in Service Setup.

# How to Get to Service Setup

  1. Just click the setup gear icon and select Service Setup. 

  2. If you want to go beyond what’s in Service Setup, and do things like change the appearance of the console or add your company’s brand to it, that’s simple too. But it requires a few more clicks.

  3. To dig deeper into your service app’s details, click the setup gear icon and select Service Setup. Enter App Manager in the Quick Find box, and click App Manager. 

  4. Click the arrow drop-down next to your Service Console (Lightning Service) app, and click Edit. 

  5. You’re now on the App Settings page. Here, you can do things like change the app’s colors and upload a branded image. You can also access other setup features at the left of the screen. From here, you can do things such as add or remove productivity tools from the utility bar. When you’re finished, click Save. 

# Benefits of the console 
    
  1. Split views - From the start, you can see a list of cases alongside your workspace to quickly work through incoming customer issues. 

  2. Related record and related list components - Right out of the box, you can see information related to a customer to get a well-rounded picture of their issue and who they are. Jump to lists of similar cases, and work off lists to keep your cases organized.

  3. Highlights panel component - Without configuring a thing, spot exactly what you need front and center to respond to customers quickly.

  4. Compact case feed - Understand case progression and case history at a glance with a news-like feed and preconfigured pages. Colorful icons help you distinguish between people and interactions instantly, and you can add a quick comment to help your customers or team.

  5. Knowledge component - See suggested articles from your knowledge base to solve cases faster, search articles to find exactly what you need, and attach common solutions from similar cases. (You must enable Lightning Knowledge first.)

  6. Preconfigured utility bar - Increase productivity with tools, such as Notes to jot things down, or History to go back to recently viewed records.

# Benefits for service Cloud 
 
  1. Guided setup flows
    
    * Follow a few simple prompts and your email and social channels are up and running, ready to turn customer issues into cases.

  2. Service metrics

    * Glance at a dashboard to monitor your service performance and check on the health of your team and overall customer satisfaction.

  3. Recommended setup 

    * Discover simple steps to set up key features, learn more about Service Cloud, and get plugged into the Salesforce community.

  4. Setup tree

    * Explore branches of the setup tree and check out all the features at your disposal. Not all Service Cloud–related setup nodes are exposed in the Service Setup tree—only the essentials—so click around to get to where you want to go.

# General Setup Process

  1. Here’s a high-level view of the process:

  2. Automate case management - First, route customer questions, comments, and feedback to the right people and places with as little work as possible. Analyze service metrics to spot trends and make better choices about service. 

  3. Add multiple channels - Once your case management system is in place, engage with customers on their favorite communication tools, such as phones, emails, websites, social media, and more.

    * Sync all your channels to a console so that your team can respond to customers anywhere. 
  
  4. Capture knowledge - As customer engagement provides your team with insights, store all useful information in an easy-to-search Knowledge base so helpful articles are just a click away for support agents or customers.

  5. Expand efficiencies with AI - Finally, include artificial intelligence and bots to streamline more tasks and predict service before it’s needed. 

# Case Management Tools

  1. Case management means organizing customer cases into one place and making sure they go to the right person, for the right answer, by the right time. 

  2. Main case automation tools

    * Queues - Automatically prioritize your support team’s workload by creating lists from which specific agents can jump in to solve certain types of cases.

    * Assignment Rules - Automatically assign incoming cases to specific agents so that the right people work on the right cases.

    * Escalation Rules - Automatically escalate cases to the right people when the cases aren’t solved by a certain time.

    * Auto-Response Rules - Automatically send personalized email responses to customers based on each case’s details.

# Plan for Case Automation

  1. Do support agents work as a team on specific issues? 

    * Yes, some agents work off a list of emails as they arrive from customers. 

      - Tool: Queues 

  2. How is the support team structured? 

    * We have Gold and Platinum support teams. Platinum support shares a workload. 

      - Tool: Queues or Assignment rules

  3. Do support agents work on specific products or have special skill sets? 

    * Some agents work on solar panel installation while others work on solar panel performance.
      
      - Tool: Assignment Rules

  4. Do cases need to escalate to someone if they’re not solved by a specific time? 

    * Yes, we can’t have customers waiting more than 5 hours to get their issues solved. 

      - Tool: Escalation Rules

  5. Should customers receive automatic responses? 

    * Yes, we want customers to know that we received their issue and that we care about them. 
     
      - Tool: Auto-response Rules

# Create a Case Queue

  1. From Service Setup, enter Queues in the Quick Find box, then select Queues.

  2. Click New.

  3. Type a Label and Name for the queue, such as Platinum Support.

  4. If you want the support agents included in the queue to receive an email when a new case arrives, leave Queue Email blank. Otherwise, type an email address to notify a person or persons with the email address when each new case arrives.

  5. Add Case to Selected Objects.

  6. Add members, including yourself, to the queue and click Save.

    * Now that the queue is created, let’s check it out as if we were support agents. We can get there with a few clicks.

  7. Click the Cases tab.

  8. From the View list, choose Platinum Support. 

  9. Here’s the queue, which is empty at this time. 

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

# Add an Auto-Response Rule

  1. Sets up response rules so that customers are automatically sent a personalized email when they reach out for help.

  2. From Service Setup, enter Case Auto-Response Rules in the Quick Find box, then select Case Auto-Response Rules.

  3. Click New.

  4. Type, Welcome to Support, then click Active and Save. Activating a rule deactivates any existing active rules.

  5. Select the rule you just created, and click New to add a rule entry.

    * Here’s where we add a few details that determine which email template we’ll send to a customer. 
  
  6. In Sort Order, type 1 so that the entry we add is processed first. 
    
    * In the real world, you’d create one response rule with many different entries,which are processed in chronological order. When a customer issue comes in and is converted to a case, it’s assigned based on the first entry it matches.

  7. For entry criteria, select Case: Case Origin equals email.

    * Similar to escalation rules, you can determine the automatic response to send to a customer based on fields from records other than cases.

  8. Add a name and email address to include in the From line of the email template to send to customers.

  9. From the lookup field, pick any template to see how this works. 

  10. Click Save and you’re done!

# More Case Management Tools

  1. Page Layout Editor - Customize a case page’s contents, like the fields and buttons that appear on the page, along with what is visible to whom. Additionally,customize the structure of the page, and the position of its components, with the Lightning App Builder.

  2. Email Templates - Create email templates to save time and standardize communications sent to customers from cases. Automate information on emails with merge fields. Templates are automatically available to anyone in the org.

  3. Entitlement Management - Provide the correct level of support for customers. Define, enforce, and track service agreements and service contracts as part of an overall support management process. 

  4. Omni-Channel - Manage support agents’ priorities and their capacity to take on work items so that they’re given only the number of assignments that they can handle. Route all assignments to the correct agents so that they no longer have to choose work assignments manually from a queue.

  5. Macros - Help support agents automatically complete repetitive tasks on cases, such as selecting the right email templates, so that they can spend time doing more important things.

  6. Quick Text - Create predefined messages for support agents, like greetings, answers to common questions, and short notes to insert in cases, emails, web chats, and more. Save time and standardize on messaging to customers.

  7. Give support agents quick access to productivity tools, like notes, history, softphones, and more in the footer of the console.

# Digital Engagement Tools

  1. Today’s customers live in an instant, mobile, web-driven world and expect one-to-one service on their channel of choice anywhere, every time. If they can’t reach you on their favorite channel, they might think less of your brand, think that you’re behind the times, or think that you’re putting them through a service circus. 

# Plan for Engagement 

  1. What is the maximum size of email attachments to support?

    * Under 25 MB is fine. 

  2. Should outgoing emails from Salesforce route through Ursa Major Solar’s email servers for security or compliance reasons? 

    * No, outgoing emails can route through Salesforce. 

  3. Does customer service use email templates, and if so, are there branding requirements? 

    * No, we don’t use email templates, but we should in the future for consistency. We should also add our logo to email templates at some point.
  
  4. Can we add a code snippet to our customer website to display a web form? 

    * Yes, no problem.

  5. Do we need to create any custom case fields to capture information for the web form? 

    * No, not now. Let’s see how this thing works first. 

# Add Email Service

  1. Click the setup gear icon and select Service Setup. 

  2. Under Email Setup, click Get Started. 

  3. Read the prompts to better understand the process, then click Start. 

  4. Select your email provider. For this exercise, choose Other. 

  5. Click Next.

  6. Enter your support email address, the email address as it will appear to customers, and the priority automatically assigned to cases created by emails. Since this is an exercise, we suggest you use an email address that’s not that important to you or your company. 

  7. Click Next.

  8. Follow the message to open your email in another browser tab, and to click the verification email sent to you by Salesforce. 

  9. On the new tab that appears verifying your routing address, click Continue. 

    * You’re redirected to the Service Console and can close the tab.

  10. On the tab with the guided email setup, select the box that you’ve verified your email address, and click Next. 

  11. Copy the email-forwarding link that appears. 

  12. Paste the email address into your email application’s appropriate email forwarding field. 

  13. Select the box that confirms you’ve set up email forwarding, and click Next. 

  14. After Salesforce tests that your email forwarding works, click Finish. 

    * Now when customers send emails to the address provided, they automatically route to Salesforce as cases. 

# Add Web Form Service

  1. From Service Setup, enter Web-to-Case in the Quick Find box, then select Web-to-Case.

  2. Select Enable Web-to-Case.

  3. Deselect Require reCAPTCHA Verification. We’re not going to cover reCAPTCHA here. 

  4. Choose a default case origin like Web.

  5. Select a response template to automatically notify customers that their case was created. Pick any template to see how this works. 

  6. Click Hide Record Information to prevent case information from appearing in the email sent to customers—this is only in the unlikely event that a case fails to create.

  7. If you’d like to use an email signature that’s different than the one in the response template, enter a new signature.

  8. Click Save.

    * Now you’re ready to generate the HTML form to send to your web developer.

  9. From Service Setup, enter Web-to-Case HTML Generator in the Quick Find box, then select Web-to-Case HTML Generator.

  10. Add the case fields you want on the form. 

  11. Enter the URL to appear after customers submit their case, such as a “thank you” page. 

  12. If Include reCAPTCHA in HTML is selected, deselect it. We’re not going to cover reCAPTCHA here. 

  13. Click Generate.

  14. Copy the HTML code and send it to your web developer to post on your website.

  15. Click Finished.

# More Digital Engagement Channels

  1. Call Center & Open CTI - Boost phone productivity by integrating Salesforce with third-party computer-telephony integration (CTI) systems. See Salesforce data for incoming calls, make outgoing calls directly from the console, and report on call outcome, duration, and more. 

  2. Self-Service Communities - Help customers find answers, log cases, and update orders on their own from web communities. Customize, create, and brand communities with easy-to-use templates, components, and apps. 

  3. Social Customer Service - Help support agents listen, respond, and log cases for customers on social platforms like Twitter, Instagram, Facebook, and more. Use keywords, classifiers, and language detection to make sure that agents find the right posts and work the right issues. 

  4. Live Agent & Snap-ins Chat - Engage with customers browsing the web with real-time, live chat. Quickly embed unobtrusive chat capabilities on company websites for both desktop and mobile browsers to let customers chat with agents and deflect cases before they get logged. 

  5. Snap-ins for Mobile & SOS - Add service to mobile apps so that customers can get help from apps on phones and tablets. With an SDK (software development kit), developers can let customers create and manage cases, live chat with support agents, video chat and screen share with agents (SOS), and view knowledge base articles on the go. 

  6. LiveMessage - Engage with customers using messaging apps like SMS text and Facebook Messenger, so that they can connect with support agents instantly from anywhere. Help agents manage multiple text conversations at once and see each text alongside relevant Salesforce data. 

  7. Field Service - Support onsite visits out in the field with mobile solutions like job schedules, van inventory, and more—with or without web connections. 