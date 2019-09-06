# Deployment

  1. There are at least 3 ways to do deployment. Here are some

    * Change sets with inbound and outbound changesets

    * Ant Migration tool - ANT scripts 

    * Ecplise IDE allows you to deploy (to be soon replaced by visualforce)

    * You can deploy using the workbench though not as common as the other three options

  2. Always start by creating a sandbox which is found under deployment settings rather than going to edit production straight away

    * Sandbox is replica of production and is safe way to work without affecting production in a negative way

    * refresh is copying from production into sandbox

    * migration is copying from sandbox to production

  3. Developer sandbox 

    * Only copies the org settings not data 

    * upload or load data up to 200mb

    * you can refresh once a day

  4. Partial Copy sandbox

    * refreshes every 5 days 

    * 5gb of data 

  5. Full copy sandbox

    * refreshes every 29 days 

    * copies an exact replica of production environment 

  6. Sandbox login 

    * test.salesforce.com

      - salesforce sandbox url uses test instead of login for url

    * username: sam@akidev.com.Sandbox2
     
      - Name of sanbox org daisy chained to end of username

  7. Make sure to prepare a connection between the sending and recieving environment using deployment settings. 

    * It is basically a handshake activity


# Change sets 

  1. Need paid edition for change sets and sandbox org 

  2. You can only use in the case of connected orgs using handshake protocol

    * Connection between sending and recieving using Deployment Settings and select the needed checkbox at Sandbox. Minimum of 1 Sb environment must be selected

  3. In paid version, there is Deployment Settings and Deployment Status 

  4. You have to login using the test.salesforce.com to access a sandbox environment

  5. Once connection is set, prepare a suitase/changeset into outbound change set from SB

    * This will add project and content from SB to Production environment.

    * Salesforce will check for all the elements in the suitcase, upload the change set and will upload to production

  6. You will see entry of this in Production under the inbound change set
 
    * Verify it using validate button

    * perform the deployment using the 'Deploy' button

  7. When you add to outbound changesets (found in setup under Deploy), here are some things to add 

    * applications

    * custom objects

    * custom fields 

    * View/Add dependnecies will check whatever is missing, or what is needed because these items are interrelated. 

      - It will fail if you do not add these items to the change sets

  8. When migration is completed, you can find your suitcase in the inbound changeset (found in setup under deploy)
   
    * First validate to check whether you should proceed or not

    * You can have it run all tests, local test, or specific test or just keep it at default if you have no tests.

    * once validation succeeds (in validation history), you can then select deploy and even include the appropriate test settings

  9. In deployment status, you can check your status for deployment and validation

    * At this point, you will be able to have everything you need in production that was from the sandbox environment

# Ant Migration

  1. Basic Docs for ANT Migration
    
    * https://developer.salesforce.com/docs/atlas.en-us.daas.meta/daas/forcemigrationtool_install.htm

  2. Ant Migration Tool .zip file contains following files and folders

    * A Readme.html file that explains how to use the tools

    * A Jar file containing the ant task

    * A sample folder containing: 

      - classe folder that contains your classes 

      - trigger folder 

      - object folder

      - XML folder 

      - A sample build.properties file in which you must edit in your credentials in order to run your Ant tasks in build.xml You have two different options for entering your credentials. Include your packages that are installed and necessary for production.
    
      - package.xml file which tries to retrieves your triggers and apex classes 

        * use the * key in the members tag if you want to add all of that type such as getting all objects

      - A sample build.xml file that exercises deploy and retrieve api calls. It actually holds the values of your org. 

    3. Ant migration copies meta data 

# Migration tools steps
  
  1. enter salesforce credential in salesforce.properties

  2. Create retrieve targets in build.xml

  3. Construct a project manifest in package.xml

  4. Run the Ant Migration Tool to retrieve metadata files from Salesforce
  Enter credentials and connection information for destination Salesforce organization in build.properties

  5. Run the Ant Migration Tool to deploy metadata files or deletions to Salesforce

# Ant commands

  1. ant retrieveunpackage

  2. ant deployunpackage

# Salesforce and Eclipse IDE 

  1. Links

    * https://developer.salesforce.com/docs/atlas.en-us.eclipse.meta/eclipse/ide_install.htm

  2. connected orgs is what determines whether we use change sets and if we do not have connected orgs, the other options like Ant will come in handy. 