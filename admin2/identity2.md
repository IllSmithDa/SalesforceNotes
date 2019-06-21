# Drive Customer Engagement with Salesforce Identity for Customers and Partners

  1.  Now you’ve heard that you can use Salesforce Identity to make it easy for Universal Deliveries’ customers, too. 

  2. Salesforce Identity helps the company attract new customers, even those in the outer reaches of the galaxy. 

  3.  Salesforce calls this feature Identity for Customers and Partners. It’s also called External Identity where “external” refers to users who are outside the corporate network.
# Give Your Users a United User Experience
 
  1. They don’t want one login to contact your Sales team, another for Service, and another for a third-party app. They also want the same experience regardless of whether they’re coming from their desktop, mobile phone, smartwatch, or other connected device. 

  2. Maybe your customers don’t want to log in to your org at all. Customers might prefer to access your Salesforce org using credentials from their social network, be it the latest interplanetary network or one of the old standbys like Facebook or Twitter.

    * Use Salesforce Identity to deliver a connected user experience and bridge identity data silos.

  3. You could give them access to meaningful data, like their order history, or offer them access to apps that they soon can’t live without—like the Salesforce mobile app. Many third-party apps on Salesforce AppExchange can save your customers time. 

  4. Your Mission: Convince Your Company to Use Identity for Customers and Partners

    * You’ve got an answer to the problem, and Universal Deliveries execs should know about it.

# Set Up a Simple Org

  1. Set Up a Profile for Your Customers

    * From Setup, enter Profiles in the Quick Find box, then select Profiles.

    * Next to External Identity User, select Clone

    * Name the profile Customers, and click Save.

  2. Add a role
   
    * From Setup, enter Role in the Quick Find box, then select Roles.

    * From the dropdown list, select Product-based Sample, then select Set Up Roles. It’s at the bottom of the page.

    * Under CEO, click Add Role.

    * For the role label, enter Customer Manager.

    * Click Save.


  3. Assign the Role to a User

    * From Setup, enter Users in the Quick Find box, then select Users.

    * Next to your username, click Edit.

    * Under Role, select Customer Manager.

    * Click Save.

  4. Create an Account

    * Name the account Customers, and click Save.

# Salesforce Communities and External Identity

  1. You set up and manage Salesforce Identity for customers through Salesforce Communities

    * Using the Communities license that you get with Salesforce Identity, you can create and deliver pages for your customers and partners to self-register and log in to your community.

  2. Enable Communities

    * From Setup, enter Communities in the Quick Find box, then select Communities Settings.

    * Select Enable communities.

    * Enter a unique name for your community domain.

    * Select Check Availability.

  3. Create Your Community

    * If you’re not already at the Communities page, from Setup, enter Communities in the Quick Find box, then select All Communities.

    * Click New Community.

    * The Communities Creation wizard displays several templates to choose from. Hover over them to read their descriptions.

  4. Control Membership to your community

    * From Community Workspaces, select Administration, then select Members.

    * Under Select Profiles, from the dropdown list, select All.

    * In the list of Available Profiles, locate the Customers profile and then click Add to add it to Selected Profiles.

    * Click Save.

  5. Complete the Initial Community Setup

    * At the top left, select Administration, then select Builder.

    * At the top right, click Publish, then click Publish again.

  6. You can modify the Login & Registration page to determine the look and behavior of your customers’ login experience.

    * From the top left, click Community Builder icon, then select Administration.

    * Select Login & Registration.

      - Notice that “Community Builder Page” appears under Login and Password. These custom pages come with the Aloha template and were designed using Community Builder.

    * Scan over the Login & Registration page to see which login settings you can configure. For now, we’re going to keep the default values.

    * Click Cancel.

  7. Activate Your Community

    * From the left, select Settings.

    * Click Activate Community, then click OK.

      - Salesforce sends you an email when the community’s activated.

  8. View Your New Login Page

    * If you’re not already there, from the left, select Settings.

    * Right-click the URL and select Open Link in Incognito Window (in Chrome) or Open Link in New Private Window (in Firefox or Safari).

  9. Replace the Logo on the Login Page

    * If you closed Community Workspaces, from Setup, enter Communities in the Quick Find box, select All Communities, then click Workspaces next to customer community URL.

    * Select Administration, then select Login & Registration.

    * Replace the logo. For Logo Type select File. Then select Choose File (or Browse depending on the browser you’re using). Select the file that you downloaded from GitHub and click Save.

# Create a Self Registration Page 

  1. How do you add a Register option to your login page?

    * From Setup, enter Communities in the Quick Find box, select All Communities, then click Workspaces next to customers.

    * Select Administration, then select Login & Registration

    * Under Registration, select Allow external users to self-register.

      - Notice that the page expands to display the Registration settings populated by the Aloha template.

    * For Profile, select Customers.

    * For Account, click Lookup magnifying glass and enter Customers in the search box. Choose the Customers account.

    * Click Save.

# Register a New Customer

  1. From your login page in the private (incognito) browser, click Not a member? and make up a name for your new customer. Use your own email address so that you receive the welcome email.

  2. From your Salesforce org, click Accounts and then click the Customers account.
  Your new customer appears under Contacts.

  3. From Setup, enter Users and select Users.

    * Your new customer appears under Users. Your customer is now a user in your org with access determined by the Customers profile and External Identity user license.

# Customize the Login Page with Visualforce Pages

  1. With Visualforce, you can

    * Control how the page looks, right down to the pixel level

    * Include custom CSS and JavaScript

# What Happens When a Customer Self-Registers to Join Your Community?

  1. Salesforce creates a User record and Contact with the information that the registrant provides on the self-registration page.

  2. Salesforce associates the Contact with an Account, in our case, Customers. You created the account earlier as part of setting up your org.

  3. The User record is assigned the Customers profile, that you cloned from the External Identity User profile earlier in this module.

# Social Sign On

  1. To enable customers to log in to Salesforce with their social credentials, you configure an authentication (auth) provider for the social account.

  2. Customer encounters a Salesforce login page with options to log in via Google, Facebook, Twitter, as well as username and password.

  3. Salesforce has several auth providers to choose from—more, if you count those auth providers that your developers can configure using the OpenID Connect protocol. 

    * And even more—if your developers want to create their own authentication provider, they can use Salesforce APIs to do so.

# Create an Authentication Provider

  1. From Setup, enter Auth in the Quick Find box, then select Auth. Providers.

  2. Click New, then select Facebook for the provider type.

  3. Name the auth provider Facebook.

  4. For Registration Handler, click Automatically create a registration handler template.

  5. For Execute Registration As, choose yourself. Heads up: This step is essential and often gets overlooked.

    * In production, you don’t choose yourself. You create a service account instead to avoid problems in the future. If you use yourself and leave the company, the process starts to fail when your Salesforce account is disabled.

  6. For Icon URL, click Choose one of our sample icons, select an icon, copy the URL, and paste it in Icon URL.

  7. Leave the other fields empty. Salesforce supplies the values, including the consumer key and consumer secret, when you use the Salesforce out-of-the-box providers (Facebook, Google, and so on).

  8. Click Save

    * After defining the auth provider, Salesforce generates several URLs. Use the Test-Only Initialization URL to test your connection with the social network.

  9. From the auth provider detail page, under Salesforce Configuration, copy the URL displayed in Test-Only Initialization URL.

  10. Paste the URL into a browser.

    * If it works, you get the Facebook login page.

  11. Log in to the Facebook page.

  12. When prompted, authorize your app.

    * You’re redirected to Salesforce, where you see the XML information that Facebook sent us.

    * This XML information is useful for debugging and adding more functionality to your auth provider. Here we see that the Facebook user is Mel Reynolds, his org ID, link to his Facebook account, and email address.

  13. Login With Facebook

    * From Setup, enter All Communities in the Quick Find box, select All Communities, then click Workspaces next to customers.

    * Select Facebook and click Save.

  14. To confirm your change, return to your private (incognito) browser and reload the login page. Check that the Facebook icon appears on the login page.

  15. Update the Registration Handler

    * The Facebook login doesn’t work because the out-of-the-box Salesforce registration handler for the Facebook authentication provider doesn’t work. Why? Authentication providers like Facebook frequently change authentication requirements to increase security. No problem. We can update the registration handler on our own.

# What’s a registration handler?

  1. A registration handler (sometimes called reghandler) creates and updates a user on the fly with identity information pulled from the authentication provider, in this case, Facebook. 

  2. A registration handler allows you to get additional information from Facebook, like a profile picture, to use when creating the Salesforce user.

  3. We chose the out-of-the-box Facebook registration handler when we selected the Automatically create a registration handler template on the Login & Registration page.

  4. Open the autogenerated registration handler.

    * From Setup, enter Auth. in the Quick Find box, then select Auth. Providers.

    * Next to the Facebook authentication provider, click Edit.

    * Under Registration Handler, click Magnifying glass to view the full name of the autocreated registration handler, for example, AutocreatedRegHandler1467402405056.

    * From Setup, enter Apex Class in the Quick Find box, then select Apex Classes.

    * Next to your registration handler, click Edit.

  5. Replace the registration handler with the one provided in the GitHub repository.

    * In another browser tab, open the registration handler, https://github.com/salesforceidentity/IdentityTrail-Module3/blob/master/SimpleFacebookRegistrationHandler.cls.

    * Copy the code from GitHub and paste it over the autogenerated registration handler in Salesforce.

    * Click Save.

  6. Now try to log in to Facebook again.

    * Return to the private (incognito) browser and reload the login page.

    * Click the Facebook icon and then enter your Facebook username and password.

  7. For Icon URL, click Choose one of our sample icons, select an icon, copy the URL, and paste it in Icon URL.

  8. Leave the other fields empty. Salesforce supplies the values, including the consumer key and consumer secret, when you use the Salesforce out-of-the-box providers (Facebook, Google, and so on).

  9. Click Save.

# Connect to Individual Customers 

  1. From B2B to B2C with Person Accounts

    * Typically, an account record contains information such as company name, location, website, and contacts. When dealing with individual consumers, you keep track of different information, so you need another type of account, called a person account.

  2. Steps to set up person accounts include:

    * Prepare your org for person accounts.

    * Enable person accounts.

    * Configure self-registration for person accounts.

    * After person accounts are enabled, you can’t turn them off. So before you set them up in your production org, make sure to test your person account implementation in a trial, development, or sandbox environment first.

# Prepare Your Org for Person Accounts

  1. From Setup, enter Accounts in the Quick Find box, then select Record Types.

  2. Click New.

  3. For Record Type Label, enter Business Account.

  4. Click Next.

  5. For page layout, select Account Layout as the layout to apply to all profiles

  6. Click Save.

  7. From Setup, enter Security Controls in the Quick Find box, then select Sharing Settings.

    * Make sure that Contact is set to Controlled by Parent.

# Enable Person Accounts

  1. Ask Salesforce to enable person accounts for your org. Then assign a person account record type to profiles that require person accounts.

  2. You know when person accounts are turned on when they show up in Setup. From Setup, enter Person Accounts in the Quick Find box.

# Configure Self-Registration for Person Accounts

  1. From Setup, enter All Communities in the Quick Find box, then select All Communities and click Manage next to the Customers community.

  2. Select Administration, then Pages, then select Go to Force.com.

  3. Click Public Access Settings.

  4. Under Record Type Settings, click Edit next to Accounts.

  5. Select business and person record types and add them to Selected Record Types.

  6. Click Save.

  7. Update the self-registration setting on your login configuration page.

  8. From Setup, enter All Communities in the Quick Find box, then select All Communities and click Manage next to the Customers community.

  9. Select Administration, and then select Login & Registration.

  10. Scroll down to Registration and make sure that the default Account is empty. By removing the default, new users are created as person accounts.

  11. Click Save.

    * You’re done. New users who register with your branded self-registration are treated as B2C customers. Now your independent cosmic outliers can join your external identity community.
  
# What Happens When an Individual Self-Registers to Join Your Community?

  1. Salesforce creates a person account for the B2C customer.

  2. Salesforce creates a contact for the B2C customer.

  3. Salesforce creates a user for the B2C customer.

  4. Salesforce assigns the user the profile that you specified when you set up self-registration. In this case, the profile is Customers, cloned from the External Identity User profile.