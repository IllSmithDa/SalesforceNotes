# Salesforce basics

# Problem it addresses 

  1. For businesses running on multiple systems, customer data (e.g email, spreadsheats) can live in different places. 
    
    * Consequences of having customer data in different places    
      - Not getting a complete picture of customer base 
      - Barrier to understanding your own customer data

# Salesforce as Solution

  1. Provides single source of truth and engagement with customers
  
  2. Single place to manage, create, view, and update customer data from any device including mobile securely into the cloud

  3. Customize beyond out of the box functionality to cater towards and personalize for your customers, partners and employees

# What is CRM or Customer relationship management
  
  1. Manage relationships with customers and prospects

  2. Track data related to all your interactions

  3. Gather insights from social media. track important metrics, communications such as email, phone, social and other channels

# Salesforce Data Management

  1. organizes data into records and standard objects similar to a spreadsheet 

  2. uploaded securely into the cloud

  3. manage and access data in more sophisticated manner such as linking records together to see your data is related (like SQL)

  4. Salesforce Objects include: 
    
    * Accounts
      - Companies you are doing business with. Can include individual people, solo contractors
    * Contacts
      - People at the company you are doing business with
    * Leads
      - Potential prospects who are not yet ready to buy or haven't determined what they will be buying
    * Opportunities
      - Qualified leads that have been converted. Account and Contacts are created along with the opportunity

# Salesforce Application examples

  1. Financial Services: Integrated service, sales and marketing for wealth management firms and banks
  
  2. Healthcare: Solution for personalized connected and responsive care

  3. Government: Connecting citizens, agencies and proccesses in the cloud

  4. Higher Education: Use social, mobile and cloud to become a connected campus

  5. Manufacturing: mobilizing sales teams, simplifying order management and integrating external systems


# Account and Contacts

  1. you store information about your customers using accounts and contacts. 

  2. Accounts are companies that you're doing business with, and contacts are the people who work for them

  3. If you’re doing business with a single person, like a solo contractor or an individual consumer, you use a special account type called a Person Account.

    * Differences between Person Accounts and Business Account
      - Person accounts are forever. After they're turned on, you can't turn them off.
      - If your organization uses both business accounts and person accounts, you’ll have to select which type of account you’re creating whenever you add an account. 
      - Person accounts can’t have contacts or account hierarchy

  4. Best practices for managing accounts and contacts

    * always associate contacts with account as they are harder to find and keep track of. 
    * handle inactive accounts and contacts by auditing for inactive accounts and then either re-engage or exlude them from lists view, reports, automated processses etc.
    * maintain account activeness and updating records

  5. Your contacts might be with more than one company and so Salesforce allows you to record them. 
    * primary account is the one contact associate themselves most with

# Account Hierarchies
  1. Accounts or companies can be set up with heirarchies

    * One global company with multiple subsidaries

      - Bethesda Softworks (global) and Bethesda Game Studios and Arkane studio all being subsidary to Bethesda Softworks
      
      - EA game studios having multiple locations in California and Texas

  2. Two ways to establish heiracrhy
    * One global enterprise account linking all contacts to it
      - easy to find account records and report on account 
      - harder to manage because to the large mass of information 
      - not being able to see what each subsidary or location individual needs 
    * Location Specific Accounts include creating account for each location and attaching contacts to that location
      - more maintenance as you are handling multiple accounts
      - track and report on specific locations more easily
      - take advantage of account ownership, heirarchies, specified account settings for each location
      - overall the better setup 

# Account Teams
  1. Accounts for the fact that more than one person works with each Account
    - sales rep, sales manager, support agent, etc. 
  2. Salesforce Account team can hold up to 5 people, each assigned with its own role. 

# Adding New Users 

  1. As a new administrator, you perform user management tasks like creating and editing users, resetting passwords, granting permissions, configuring data access, and much more.

  2. A user is anyone who logs in to Salesforce. Users are employees at your company, such as sales reps, managers, and IT specialists, who need access to the company's records.

  3. Every user in Salesforce has a user account. The user account identifies the user, and the user account settings determine what features and records the user can access. Each user account contains at least the following:

    * Username
    
    * Email Address
    
    * User's First and Last Name
    
    * License
    
    * Profile
    
    * Role (optional)

  4. To view and manage the users in your organization, from Setup, enter Users in the Quick Find box, then select Users. The user list shows all the users in your organization. 

    * From Here you can: 

      - Create one or more users.

      - Reset passwords for selected users.

      - View a user's detail page by clicking the name, alias, or username.

      - Edit a user's details.

      - Log in as any user if the system permission is enabled or if the user has granted you system administrator login access.

  5. Key Terms 

    * Usernames 

      - Each user has both a username and an email address. The username must be formatted like an email address and must be unique across all Salesforce organizations. It can be the user's email address, so long as it is unique.

    * User Licenses

      - A user license determines which features the user can access in Salesforce. For example, you can allow users access to standard Salesforce features and Chatter with the standard Salesforce license. But, if you want to grant a user access to only some features in Salesforce, you have a host of licenses to choose from. For example, if you have to grant a user access to Chatter without allowing them to see any data in Salesforce, you can give them a Chatter Free license.
    
    * Profiles

      - Profiles determine what users can do in Salesforce.

      - They come with a set of permissions which grant access to particular objects, fields, tabs, and records. Each user can have only one profile. Select profiles based on a user’s job function (the Standard User profile is the best choice for most users). Don’t give a user a profile with more access than the user needs to do their job. You can grant access to more items the user needs with a permission set.
      
    * Roles

      - Roles determine what users can see in Salesforce based on where they are located in the role hierarchy.

      - Users at the top of the hierarchy can see all the data owned by users below them. Users at lower levels can't see data owned by users above them, or in other branches, unless sharing rules grant them access. Roles are optional but each user can have only one.

      - Roles are only available in Professional, Enterprise, Unlimited, Performance, and Developer editions of Salesforce.

    * Alias

      - An alias is a short name to identify the user on list pages, reports, or other places where their entire name doesn't fit. By default, the alias is the first letter of the user's first name and the first four letters of their last name.

# Adding Users Guideline

  1. Username: Each user must have a username that is unique across all Salesforce organizations (not just yours). 

  2. Username Format: Users must have a username in the format of an email address (that is, jdoe@domain.com), but they don't have to use a real email address.

  3. Email: Users can have the same email address across organizations.

  4. Passwords: Users must change their password the first time they log in.

  5. Login Link: Users can only use the login link in the sign–up email once. If a user follows the link and does not set a password, you (the admin) have to reset their password before they can log in.

# Add Users 

  1. Depending on the size of your organization or your new hire onboarding process, you may choose to add users one at a time or several at a time. 

  2. To Add Users 

    * From Setup, enter Users in the Quick Find box, then select Users.

    * Click New User to add a single user or click Add Multiple Users to add up to 10 users at a time.

    * Enter each user's name, email address, and a unique username in the form of an email address. By default, the username is the same as the email address, but you can overwrite this.

    * Select the user license you want to associate with the users you create (the license determines which profiles are available for each user).

    * Select a profile.

    * Select Generate passwords and notify user via email to email a login name and temporary password to each new user.

    * Click Save.

  3. Access to user management and Setup isn’t limited to the desktop. If you’re not at your desk and you need to get your admin duties on, you can take Setup on the go with the SalesforceA mobile app. 

    * Logging in to Salesforce Mobile App is as easy as pie. You need just a couple of key ingredients to log in to mobile app successfully.

      - Username
      
      - Password

      - Correct instance - The instance can vary from production, sandbox, or a custom domain. By default, the Salesforce Mobile App connects to the production environment
  
  4. Freeze a User from Anywhere if a account has been compromised

    * Go to the compromised user’s profile page, then tap and select Freeze.

    * Now the user’s compromised account is frozen to prevent any trouble

# Deactivate User 

  1. In Setup, use the Quick Find box to go to Users.
  
  2. Click Edit next to the name of the user you want to deactivate.

  3. Clear the Active checkbox and click Save. 

    * If you can’t immediately deactivate an account (for example, when the user is selected in a custom hierarchy field), you can freeze their account. That prevents the user from logging in to your organization while you’re working on deactivating them.

# Set Password Policy 

  1. Password policies - Set password and login policies, such as specifying an amount of time before all users’ passwords expire and the level of complexity required for passwords.

  2. User password expiration - Expire the passwords for all the users in your org, except for users with “Password Never Expires” permission.

  3. User password resets - Reset the password for specified users.

  4. Login attempts and lockout periods - If a user is locked out due to too many failed login attempts, you can unlock the person’s access.

    * Use the Quick Find box to find Password Policies in Setup.

    * Customize the password settings.

      - How long should passwords be? Longer is usually better, within reason.

      - How complex do you want your passwords? You can require alphabetical, numeric, uppercase, lowercase, or special characters.

      - How many days is a password valid?

      - How many times can someone try to log in with invalid credentials before being locked out?

    * Choose what to do about forgotten passwords and locked accounts.

    * Click Save. 