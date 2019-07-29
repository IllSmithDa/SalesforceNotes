# SalesforceA

  1. app launched in 2013

  2. emables salesforce admins to manage users and view data on a mobile device 

  3. Basic admin tasks like freezing, deacitivating, editing, reactiviating, unblocking users on the move

  4. You can't swap between orgs but you can login and logout with different usernames

  5. It is not a sales or marketing app like the Saleforce sales app

# Microsoft outlook can be integrated into salesforce using a salesforce app supported by Salesforce.

  1. programs like Excel connectors which are available on the app exchange

  2. THis will automoatically synce contacts, event and tasks between outlook and salesfroce 

  3. Also allow manually adding outlook emails to salesforce records as Contacts, Leads, and Opportunities

  4. allows Syncing entire org with your outlook. 

  5. Bi-directional synchronization which means changes from either platform will update the other platform to match

  6. To enable integrations, System Admin needs to create at least one outlook configuration
  
  7. Synced items appears in the "my unresolved items" category. 

# Self Relationships and heirarchical relationships

  1. A special lookup relationship with itself is a self relationship. 

  2. It creates a tree diagram object. 

    * e.g The account has a lookup on itself called Parent Account.

  3. The heirarchical is a self relationship with the USER object. 

    * It allows users to use a lookup field to associate one user with another that does not directly or indirectly refer to itself. 

    * Assigning a user on some user field in the User ojbect is an example of a heirarchical object