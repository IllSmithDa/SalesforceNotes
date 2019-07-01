# Sales Cloud 

  1. Sales cloud is just one of many clouds that Salesforce offers among service cloud, health cloud, and even financial cloud

  2. You can see many of the standard objects on the sales cloud including Chatter, Leads, Accounts and Contacts

    * Many of the standard object overlap between different clouds such Chatter, Accounts, Contacts, Cases and Dashboards between sales and service cloud
 
# Leads and Leads processes

  1. What is a lead? 

    * Any person who shows interest in the product or services or both that a company offers

      - Key word being 'any' and 'interest'

      - interest will need to be qualified

      - e.g those are just doing a price comparison or price discovery may not be a genuine lead

    * Lead can go through a set of stages 

      - this is the lead management process
    
      - includes different stages including contacted, not contact, converted, not converted

    * Applies both in the business to business interactions and business to indiviudal customer interactions 

      - bulk orders from a company to another comany or individual buyers

# Opportunity 

  * A qualified sales lead

  * An Opportunity is neither a business, nor a person, but rather a potential future sale

  * When a lead is converted, it can include Account, Contact, opportunites 

  * Also contians many stages 

# Pricebook

  * automation process which updates prices for all your products

# CPQ 

  * app that automates the sales process 

    - Quote management

# What is the sales process?

  * ONe of many process among lead process, support process, solution process. 

  * It is the sales lifecycle. 

  * Usually includes 7 or 8 stages which can be customized by the user

  * Salesforce however, comes with 9 stages right out of the box

    - Prospecting
   
    - Qualification

    - Needs Analysis
 
    - Value Proposition

    - Id. Decision Makers

    - Perception Analysis 

    - Proposal/Price Quote

    - Negotiation/Review

    - Closed Won

    - Closed Lost

  3. You can also customize sales process by going to Setup and go Sales process.

    * Go to record types to add the sales process to the opportunity

# Web to Lead 

  * Html form that allows you to enter leads into Salesforce

# Auto response forms and Leads

  1. Auto response is primarily only for emails and for Leads and Cases only

  2. When you register on any website, you typically will get an email which thanks you for trying a product 

  3. In settings, you can find Lead Auto Response rules 

    * You can create entries which are criteria based

      - When criteria is met, a response is given which is a email to the lead.

# Lead queues 

  1. Leads can be only assigned to a user or a queue 

    * Cases can be only assigned to a user or a queue

  2. Neither leads and cases can be assigned to a public group, role or a profile

  3. You can create Lead assignment rules in the settings 

    * You can add rule entries which includes a criteria and who to assign to (user or queue) when
    criteria has been met

# Out of box features 

  1. Web to Case

  2. Email to Case 

  3. Web to Lead

# Custom Aex code required (not out of the box)

  1. Email to Lead is not a out of box feature

  2. Email to Custom Objects

  3. Web to Custom Objects 

# Opportunity Teams

  1. Must be enabled through Opportunity Team Setup 

  2. You can create and add roles to the Opportunity teams 

    * You can reorder and replace them 

  3. You can then add opportunity team members to the team 

  4. Opportunity teams can change based easily on what opportunity is present, what skills are required, and who is necessary to move through the opportunity cycle

  5. You create the teams itself as one of the related list items on the Opportunity page 

# Account Teams

  1. Must be set up through Account Team setup

  2. Irrespective of all opportunities coming in, the account team will be the same

# Case Team

  1. Must also be setup through Case Team Setup

  2. A case team is simply a group of individuals working on a case; there are multiple people involved in the resolution of the case. 

    * A case queue is a holding area where cases not yet assigned reside until someone accepts the case. Nobody has yet started working on the case, so anyone in the queue (people skilled to handle a particular set of problems) can accept the case and begin working on it.

# Email to Case

  1. Email to Case setting 

    * You can notify a owner on new cases through email

  2. For Email-to-Case:

    * Download the Email-to-Case agent from the Apex Developer Network

    * Install the agent behind your network firewall.

    * Configure email routing addresses.

    * Enable Email-to-Case.

  3. Email-to-Case requires downloading the Email-to-Case Agent. The Email-to-Case Agent allows you to keep all email traffic within your network’s firewall and to accept emails larger than 25 MB from customers.
