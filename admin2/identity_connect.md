# What is Identityt Connect?

  1. Identity Connect is a Salesforce Identity product that helps Salesforce admins apply all the data collected in AD to automate Salesforce user management. It syncs changes in AD within seconds. 

    * AD is active directory

# Synchronize Salesforce with Active Directory
 
  1. With Identity Connect, you can manage Salesforce users by relying on the data already entered in AD. Identity Connect constantly monitors AD and updates Salesforce when changes in AD occur. 

  2. When Identity Connect detects differences between AD and Salesforce, it updates Salesforce with the information in AD. Data transfer is in one direction and AD is the source of truth.

  3. With Identity Connect, you can quickly set up users with Salesforce.

  4. You can set up single sign-on (SSO) with Identity Connect so that users can access Salesforce with their AD credentials.

    * When users are added to AD, they can access Salesforce with the same username and password they use for AD.

  5. Identity Connect provides some security during the offboarding process.

  6. Reduce IT Concerns

    * IT will be happy to know that you don't need administrative privileges to AD to use Identity Connect.

    * Identity Connect only needs read-only access to the users and groups in AD that you want to sync with Salesforce.
    
  7. Identity Connect Licensing

    * Identity Connect is an add-on license available for Salesforce users on most Salesforce products: Salesforce platform, Sales Cloud, Service Cloud, Analytics Cloud, and Identity for Employees.

  8. As part of evaluating Identity Connect, you can set it up on your own computer. All you need is access to AD, a Java runtime environment, and a Salesforce org with Identity Connect enabled.

  9. Identity Connect comes with everything you require to try out basic user provisioning and authentication: the application, web services, and an OrientDB database (for storing Identity Connect settings and logs). 

    * If you prefer a different database, you can replace OrientDB when you deploy Identity Connect.

# Mapping Data 
  
  1. Identity Connect creates Salesforce users from the users managed in AD.

  2. Before you sync for the first time, you choose which AD attributes get pulled into Salesforce. You can accept the default mapping that Identity Connect provides. 

  3. What data do you map? Users, attributes, permissions. You can:

    * Tell Identity Connect where to look in AD for Salesforce users.

    * Choose which attributes you want to get from AD. Remove the ones that you want to manage from Salesforce. If you’ve added custom attributes to your Salesforce User object, you can control how they’re managed.

    * Assign permissions. After you define the rules for assigning permissions, you don’t have to think about permissions again.  Woo-hoo.

# It’s Also About Syncing Data

  1. When Identity Connect creates Salesforce users, it creates links to users in AD.

  2. Each Salesforce user is actually a link to the user data stored in AD. Essentially, Identity Connect builds a “virtual” user database in Salesforce from the information in AD.

  3. The first time Identity Connect syncs, it goes to the specified location in AD to create your Salesforce users.

    * After that, Identity Connect monitors the specified location. 

    * If existing users change or if new users are added to the specified location in AD, Salesforce gets the changes the next time Identity Connect syncs.

# Choose Your Salesforce Users

  1. To create Salesforce users from AD, you choose which users you want in Salesforce. 

  2. From the Identity Connect console, you set the base context, which means “start searching at this point.” Then you set filters to refine the scope.

  3. Base Context 

    * AD is organized in a tree structure. So with the base context, you’re specifying the path to the branch under which AD users, groups, and resources (like computers and devices) belong.

  4. User and Group Filters

    * You’ve told Identity Connect where to go to find Salesforce users and groups. Now you refine the scope using filters.

    * Under User Filter, specify which users to sync to Salesforce. For example, all users or only users who belong to specific AD groups. Our example excludes AD objects that are computers.

# Choose your Attributes 

  1. AD and Salesforce share some of the same user attributes, though they don’t use the same name. So you specify which Salesforce attribute corresponds to the attribute in AD.

  2. Default Column

    * Use the Default column to populate a Salesforce attribute when the user’s corresponding AD attribute is empty.

      - For example, if the user doesn’t have the EmailEncodingKey attribute in AD, Identity Connect populates the Salesforce EmailEncodingKey attribute with UTF-8.

  3. Transform Script Column
    
    * This is where you can add a bit of programming logic to create Salesforce values by transforming an AD attribute. 

    * Transform scripts are optional

  4. Do you have custom attributes? They don’t show up by default. But you can have Identity Connect retrieve them from your Salesforce org. Click Add Attribute and your custom attributes show up in the Salesforce column.

# Deployment Architecture

  1. Now let’s take a look at the network resources required to deploy Identity Connect. 

  2. dentity Connect is on-premises software that sits behind your firewall and pushes data to Salesforce. Identity Connect’s server runs within the corporate network and communicates with the AD server over LDAP(S).

  3. It communicates with in-the-cloud Salesforce over HTTPS.   

  4. When using Identity Connect for SSO, put Identity Connect in the DMZ if:

    * Your users log in to Salesforce from outside your trusted network. This way, your external users can access the Identity Connect login page without having to use a VPN.

    * You want users to log in to Salesforce from a mobile device. Otherwise, your users must be on a mobile VPN.

  5. High Availability Clusters 

    * Deploy an Identity Connect cluster of multiple servers to ensure Identity Connect works even when one server goes down. This way, you can make sure Identity Connect is always available on your network.

    * With a high-availability cluster, the primary Identity Connect instance writes all your configuration changes to the database. 
  
  6. Can We Use Identity Connect with Multiple Orgs?

    * Sure. Identity Connect is designed to work with multiple Salesforce orgs. You can set up Identity Connect to manage all these orgs simultaneously.

    * Each org has its own Identity Connect mapping so you can control the user’s attributes and entitlements separately for each org.





# Assign Salesforce Permissions 

  1. In AD, users are granted permissions using AD Groups. In Salesforce, we use profiles, permission sets, roles, and public groups. With Identity Connect, you can map permissions in AD to permissions in Salesforce.

  2. When users are added to or removed from a group in AD, they’re automatically added or removed from the mapped profiles, permission sets, roles, and public groups in Salesforce.

  3. To assign Salesforce permissions from AD, choose which AD groups correspond to Salesforce permissions.

  4. Profile Mapping

    * From the Identity Connect console, choose the Profile Mapping tab. 

    * The AD group containing Identity Connect users, ICusers, gets the Salesforce Standard User profile.

  5. Role Mapping 

    * From the console’s Roles tab, you choose which AD groups map to Salesforce roles. For example, map the Salesforce Executive Staff role to the AD group, Executives.

  6. Permission Sets 
   
    * From the console's Permission Sets tab, Identity Connect displays the permission sets you've defined in your Salesforce org. You choose which AD groups map to your Salesforce permission sets.

# Salesforce Groups to AD Group Mapping

  1. You can map all the Salesforce groups to AD groups under the SF Group to AD Group tab. 

    * For example, map your Salesforce group “Employees” to your AD group “Employees.” 

  2. Fewer Profiles with Targeted Permission Sets

    * Use permission sets to further refine profiles instead of creating more. You can use permission sets to grant access among logical groupings of users, regardless of their primary job function. 

  3. In addition to mapping attributes and permissions, you can define rules to map Salesforce users to AD users.

    * Another way to tell Identity Connect where to find Salesforce users is by creating AD groups. 

# What About High-Availability Clusters?

  1. Deploy an Identity Connect cluster of multiple servers to ensure Identity Connect works even when one server goes down. This way, you can make sure Identity Connect is always available on your network.

  2. If you're using Identity Connect for SSO, set up Identity Connect in a multi-instance cluster to avoid a single point of failure. If the entire company can’t log in to Salesforce, it’s a big deal.

# Consider Other Features 

  1. Brand the Login Page

    * From Settings at the top-right of the Identity Connect console, select Customize Theme. The branding page lets you change:

      - Your logo

      - The background and button colors on the login page 

  2. Live Versus Scheduled Updates

    * Should you choose Schedule Updates or Live Updates? 

      - Answer is both 

    * Live Update

      - Identity Connect monitors AD and updates Salesforce as changes occur. 

      - It’s not a full comparison of everything in both systems, though. So if either the Identity Connect or the primary AD server goes offline, it’s possible to miss AD changes that occurred during that time

    * Schedule Updates

      - Identity Connect makes a full comparison between AD and Salesforce. It collects all user and group information from AD and Salesforce and compares all the data. If any differences exist, Identity Connect updates Salesforce with the data from AD.

      - Salesforce recommends using Schedule Updates at most once per day. Most customers run Schedule Updates every night or every weekend. 

      - Even though the mechanism ensures that the data is in sync, Scheduled Updates consume more resources—including API calls.

# Identity Connect in a Production Org

  1. If you’re configuring Identity Connect in an existing Salesforce org, make sure that you don’t unintentionally change user profile and permission sets.
 
  2. Be sure to test thoroughly before syncing all users in your production org. Not to scare anyone, but we’ve seen cases where a Salesforce admin scheduled a sync before completing the Identity Connect setup, and changed the profile for every user in their Salesforce org.

# Reports

  1. From the Identity Connect console, you can generate different types of reports for different stages.

  2. Run a reconciliation report before syncing. It reports how many users in Salesforce don’t map to AD.

    * Or more specifically, it helps identify data sync issues and data inconsistences between the two platforms.

# Disable Salesforce Passwords

  1. Disable Salesforce passwords to ensure that your users log in to Salesforce with their AD credentials. Without a Salesforce password, users can never bypass Identity Connect when logging in.

  2. Disabling Salesforce passwords is also a big win for reducing compliance overhead. Set your password strength requirements in AD and force all users to use that password. 

  3. To disable passwords, Salesforce Support must enable Delegated Administration. Then you can set Is Single Sign-On Enabled on the profile of users who won’t have a Salesforce password.

# Password Sync Plug-In
 
  1. Password Sync is an optional plug-in that clones your AD password into Salesforce. With it, users can log in to login.salesforce.com (or https://mydomain.my.salesforce.com) using their Salesforce username and AD password.

  2. Password sync works by installing an agent on an Active Directory server instance (domain controller). The agent captures a password every time it changes and sends it to Salesforce through Identity Connect.

# Integration Windows Authentication (IWA)

  1. Integrated Windows Authentication (IWA) offers another way to provide SSO. It’s based on Kerberos authentication.

  2. Having Identity Connect integrated with IWA saves users an extra log in. Once users log in to their computers with their AD username and password, Identity Connect recognizes the user and doesn’t prompt them to log in to Salesforce. I

