# Sanbox has many types

  1. Developer Sandbox 

    * load up data up to 200 mb

    * Copy only organization config

      - does not copy data

  2. developer pro sb

    * load up to 1gb data 

      - 500k records 

    * same as developer sanbox otherwise

  3. partial copy sandbox

    * generally intended to be used a testing environment 

    * up to 5gb of the data 

    * refreshed every week

  4. Full copy sandbox 

    * Store an exact copy of your production org 

       - Amount of data will be same as your production 

    * Can be refreshed every 29 days 

    * Has the option of copying aconfigurable amount of field history data from the production and can handle Chatter posts and activity from production if desired. 

  5. Go to Setup and under Deploy, you can find the Sandbox settings 

    * Not seen in the free Salesforce developer org 

    * You have to use the paid edition of Salesforce to see these options as Sandbox is meant for production process

# Sandbox

  1. url is test.salesforce.com not login.salesforce.com

  2. username will be followed by the name of the sandbox 

     Username will otherwise be same as the production environment

  3. Prepare a connection between sandboxes and recieving using Deployment settings. It is basically like a handshake activity.

    * COnnection to a sanbox to another sandbox 

    * connect a production org to another produciton 

  4. Prepare a suitcase and every thing you build in the Sandbox environment. 

    * Also called a outbound change set 

# Suitcase 

  1. Prepare a suitcase change set from SB

    * THis will add projects and content from SB to Produciton

  2. Add all elements to the suitcase 

    * You can click a verify button which Salesforce will check if there are elements you are missing

    * Make sure to intentional of which elements you are including for moving the suitcase 

  3. Upload the change set into the inbound change set. 

    * Inbound change set also exists under the Deploy settings 

  4. See the components if you want to check what all elements coming from SB in that 

  5. Perform deployment by checing Deploy button