# Enable Live Agent and Communities 

  1. Example in this link

    https://trailhead.salesforce.com/en/content/learn/projects/build-a-community-with-knowledge-and-chat/enable-live-agent-and-communities

# Turn on Communities 

  1. Click Setup icon  and select Service Setup.
  
  2. Enter Communities Settings in Quick Find, then select Communities Settings.
  
  3. Select Enable Communities.
  
  4. Enter a unique value to be used as your domain name and click Check Availability.
  
  5. Note: Keep in mind that you can't change the domain name after you save it. You have to call Salesforce to change it.
  
  6. Click Save.
  
  7. Click OK.

# Create New Community

  1. You should have been redirected to the All Communities page in Setup, but if not, enter All Communities in Quick Find, then select All Communities.

  2. Click New Community.

  3. Select the Customer Service template.

  4. Click Get Started.

  5. For Name, enter Category 1 Biking.

  6. Click Create.

# Run the Live Agent Guided Setup Flow 

  1. The Live Agent setup flow is a quick way to get up and running with live web chat. When you complete the flow, you’re ready to start chatting with your customers.

  2. Click Community Workspaces at the top left of the page

  3. Select Salesforce Setup.

  4. You should be returned to the All Communities page in the Service Setup. If not, enter All Communities in Quick Find, then select All Communities.

  5. Copy the URL associated to the Category 1 Biking community.

  6. Click the Home tab to go to Service Setup Home.

  7. Click View All and then search for and select Live Agent Setup.

  8. Click Start and follow through the steps

# Modify the Live Agent Chat Window Title 

  1. Enter Deployments in Quick Find, then select Deployments. 

    * Note: If Deployments does not appear as an option in Quick Find, refresh the page.

  2. Click Edit next to Live Agent Setup Flow.

  3. Update the Chat Window Title to Category 1 Biking.

  4. Click Save.

# Create a Live Agent Skill  

  1. Skills are areas of expertise you assign to agents, so chats are routed to an agent with the right knowledge base. You can create skills for channels, products, escalation paths, and more. For example, Category 1 Biking might want to assign different skills for bikes for adults versus bikes for kids. 

  2. Enter Skills in Quick Find, then select Skills.

  3. Click New.

  4. In the Basic Information section, enter these details.. 

    * Name: Web Support

    * Developer Name: Web_Support

  5. In the Assign Profiles section, add Custom: Support Profile, Standard User, and System Administrator.

# Create a Live Agent Configuration 

  1. Enter Live Agent Configurations in Quick Find, then select Live Agent Configurations.

  2. Click New.

  3. In the Basic Information section, enter these details. 

    * Live Agent Configuration Name: Web Support Configuration

    * Developer Name: Web_Support_Configuration

  4. In the Assign Profiles section, add Custom: Support Profile, Standard User, and System Administrator.

# Add Live Agent to the Service Console 

  1. From the Service Setup, enter App in Quick Find, then select App Manager.

  2. Click the down arrow next to Service Console and click Edit.

  3. Click Navigation Items.

  4. Search for and select Live Agent Sessions in the Available Items list, then click the Add arrow, to move it to the Selected Items section.
 