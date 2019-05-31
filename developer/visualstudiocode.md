# Make Visual Studio Code Salesforce Ready 

  1. Install the Command Line Interface (CLI) 

    * windows 64 bit - https://sfdc.co/sfdx_cli_win64   

    * macOS - https://sfdc.co/sfdx_cli_osx  

    * Debian/Ubuntu 64 - https://sfdc.co/sfdx_cli_linux  

  2. Install the Salesforce Extension Pack 

    * In the marketplace, Enter 'Salesforce Extension Pack' in the search field and install

# Command Palette to create project

  1. Press Command + Shift + P on Mac or Ctrl + Shift + P on Windows to make the command palette appear.

  2. Make sure the new prompt starts with >

  3. Type SFDX: Create Project

  4. Press Enter.

  5. Type: VSCodeQuickstart .

# Terminal to create project

  1. Click Terminal on the top options bar.

  2. From the dropdown select New Terminal.

  3. Type 'sfdx   '

# Search your Files 

  1. Press Command + P on Mac or Ctrl + P on Windows to make the search palette appear. This shifts the focus to search files.

  2. Type project-scratch-def.json into the field.

  3. Click the result to open the file.

  4. Search for orgName.

  5. Click the first time it is found in project-scratch-def.json.

  6. Change the orgName value (after the : and in between the “”) to Learning VS Code.

  7. Save the file by pressing Command + S on Mac, Control + S on Windows.


# Activate your playground 

  1. Press Command + Shift + P on Mac or Ctrl + Shift + P on Windows to make the command palette appear.

  2. Type SFDX: Authorize an Org.

  3. To accept the default login URL, press Enter.

  4. Enter the alias 'VSCodePlayground'

  5. Notice that your default browser opens a new Salesforce login window. Log in to your playground using your playground username and password retrieved from the last step.

  6. When you are asked to grant access to the connected app, click to allow.  

  7. Close the browser window.


# Create an Apex Class 

  1. Under the VSCODEQUICKSTART directory, click force-app to show its folder tree. You should see main, then default, then aura and lwc.

  2. Right click the default folder.  

  3. Click New Folder.

  4. Name the new folder classes.  

  5. Press Command + Shift + P on Mac or Ctrl + Shift + P on Windows to make the command palette appear.

  6. Type SFDX: Create Apex Class.

  7. Enter the name AccountController.

  8. If VS Code asks, select force-app/main/default/classes as the directory you wish to add AccountController.cls to. In the newly opened AccountController.cls file, replace the default code with the following:

    * public with sharing class AccountController {
        public static List<Account> getAllActiveAccounts() {
          return [SELECT Id,Name,Active__c FROM Account WHERE Active__c = 'Yes'];
        }
      }

  9. Save your file.

# Query  

  1. In line 3 of the code, highlight the query SELECT Id,Name,Active__c FROM Account WHERE Active__c = 'Yes'

  2. Press Command + Shift + P on Mac or Ctrl + Shift + P on Windows to make the command palette appear.

  3. Search for SFDX:Execute SOQL Query with Currently Selected Text.

  4. Press Enter

  5. Select REST API and press Enter.

    * In the Output tab of the integrated terminal, view the results of your query. You should have also received a notice that states: SFDX: Execute SOQL Query ... ended with exit code 0. This means it successfully ran.

# To Deploy 

  1. Right click the classes folder. 

  2. Click SFDX: Deploy Source to Org.

  3. In the Output tab of the integrated terminal, view the results of your deployment. You should have also received a notice that states: SFDX: Deploy Source to Org ... ended with exit code 0. This means it successfully ran.

    * Now you’re ready to explore some of the more complex topics, such as debugging with the Apex Replay Debugger, customizing your editor to fit your needs, and running your developer pipelines with Visual Studio Code.