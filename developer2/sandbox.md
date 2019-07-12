# Sandbox purpose
 
  1. It is there to protect your production data and configuration

  2. Sandbox Refresh 
    
    * Cycles between the Production and the Sandbox modes 

# Four types of sandbox

# Sanbox has many types

  1. Developer Sandbox 

    * load up data up to 200 mb

    * Copy only organization config

      - does not copy data

    * Production moved into Sanbox can be refreshed every 24 hours 

      - during that time, you cannot do anything to that org

  2. developer pro sb

    * load up to 1gb data 

      - 500k records 

    * same as developer sanbox otherwise

  3. partial copy sandbox

    * generally intended to be used a testing environment 

    * up to 5gb of the data 

    * refresh every 5 days

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

    * Username will otherwise be same as the production environment

    * Add a '.' followed by the sandbox name for the user name 

      - e.g badboy@salesforce.com.sandboxName1

  3. Prepare a connection between sandboxes and recieving using Deployment settings. It is basically like a handshake activity.

    * Connection to a sanbox to another sandbox

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

# Creating new Sandbox

  1. Name it and create a apex class which then it will be executed on

  2. It can take many hours for the sandbox to be created 

# Deploying Sandbox 

  1. Go to Deployment settings 

  2. Deployment connections and click production 

  3. Save the production connection 

  4. Go next start up the suitcase and go into production mode 

  5. Both production and sandbox can now communicate with each other 

    * Communication is always done through packing the chain set or suitcase

# 2 Types of suitcase 

  1. Outbound chain set for going outside salesforce environment 

    * Go to outbound settings 

    * Name your new Chain Set 

    * Add the items you need which includes Applications, objects, fields and profiles 

    * You send it using upload and pick the organziation you want to send it to. 

    * You have to clone chain set in order to use any of those objects or else they cannot be touched during this time 

    * Don't directly click deploy but always validate first which will test to see if there are any issues before you deploy

      - After checking all components, it will notify you of any error and whether if its ready for deployment

      - You can also run test on your apex code and components as well

    * After you deploy, you can check the deployment status periodically. It will let you know if deployment was successful. 

    * Deployment nmechanism - you will see all the items you added in the chainsets show up in the productin environment

      - Very thorough system

  2. An inbound change set is a change set that has been sent from another Salesforce org to the org you are logged in to. 
  
    * A change set must be deployed for the changes to take effect. You can deploy the contents of an inbound change set as a whole but not on a component-by-component basis.

# Refresh Your Sandbox
 
  1. Refreshing a sandbox updates the sandbox’s metadata from its source org. If the sandbox is a clone or if it uses a sandbox template, the refresh process updates the org’s data in addition to its metadata.   