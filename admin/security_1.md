# Data Security -  how to make sure they can see what they need to see and only what they need to see.

  1. Salesforce provides a flexible, layered sharing model that makes it easy to assign different data sets to different sets of users. 

    * This ensures you can balance security and convenience, minimizing the risk of stolen or misused data while making sure that all users can easily access the data they need.

  2. Salesforce includes simple–to–configure security controls that make it easy to specify which users can view, create, edit, or delete any record or field in the app.

    * You can configure access at the level of the organization, objects, fields, or individual records. By combining security controls at different levels, you can provide just the right level of data access to thousands of users without having to specify permissions for each user individually.
  
# Levels of Data Access - You can configure access to data in Salesforce at four main levels.

  1. Organization 

    * At the highest level, you can secure access to your organization by maintaining a list of authorized users, setting password policies, and limiting login access to certain hours and certain locations.
    
  2. Objects

    * Object–level security provides the simplest way to control which users have access to which data. 

    *  By setting permissions on a particular type of object, you can prevent a group of users from creating, viewing, editing, or deleting any records of that object.

      - For example, you can use object permissions to ensure that interviewers can view positions and job applications but not edit or delete them.

  3. Fields

    * You can use field–level security to restrict access to certain fields, even for objects a user has access to.

      - For example, you can make the salary field in a position object invisible to interviewers but visible to hiring managers and recruiters.

  4. Records

    * To control data with greater precision, you can allow particular users to view an object, but then restrict the individual object records they're allowed to see.

      - or example, record–level access allows interviewers to see and edit their own reviews, without exposing the reviews of other interviewers. 

    * You can manage record–level access in the following ways.

      - Organization–wide defaults - specify the default level of access users have to each others' records. For example, you can give all employees access to an object called Candidate to allow anyone to add a candidate to the database. But you can restrict access to Positions so that anyone can see the jobs available but only the employees with the proper permissions can edit them.

      - Role hierarchies - open up access to those higher in the hierarchy so they inherit access to all records owned by users below them in the hierarchy. Each role in the hierarchy represents a level of data access that a user or group of users needs. For example, you can restrict access to Candidates by setting the organization–wide default to Private, but allow recruiters to view and edit the candidate records that they own. Recruiters can't see candidate records they don't own because recruiters are all at the same level in the role hierarchy. However, hiring managers can be given read/write access to all candidate records because they are at a higher level in the role hierarchy than recruiters.
    
      - Sharing rules - enable you to make automatic exceptions to organization–wide defaults for particular groups of users, to give them access to records they don't own or can't normally see. Sharing rules, like role hierarchies, are only used to give more users access to records—they can't be stricter than your organization–wide default settings. For example, you can allow all employees to view Positions, but use sharing rules to grant full editing access to employees in a role or group called Hiring Managers.

      - Manual sharing  - allows owners of particular records to share them with other users. Although manual sharing isn't automated like organization–wide sharing settings, role hierarchies, or sharing rules, it can be useful in some situations, for example, if a recruiter going on vacation needs to temporarily assign ownership of a job application to another employee.

# Overview of Record–Level Security

  1. You can control data access with greater precision by allowing particular users to view an object, but then restricting the individual records within the object they're allowed to see.

    * For example, you can give all your interviewers access to reviews with organization–wide defaults, but restrict their access to only reviews they own with role hierarchies. 

  2. Even if you grant a profile create, read, and edit permissions on the recruiting objects, if the record–level permissions for an individual recruiting record prove to be more restrictive, those are the rules that define what a recruiter can access. 

    * For example, if you give the Recruiter profile create, read, and edit permissions on the Candidates object but restrict recruiters' access to only the Candidate records they own, recruiters are only able to access those records.

# Organization–Wide Sharing Defaults

  1. These are the defaults that specify the baseline level of access that the most restricted user should have.

  2. You can use organization–wide defaults to lock down your data to this most restrictive level, and then use other record–level security and sharing tools (role hierarchies, sharing rules, and manual sharing) to open up the data to other users who need to access it.

  3. You can specify the default level of access to records with organization–wide sharing settings and you can set them separately for each type of standard or custom object. 
  
  4. You can determine the baseline level of access for all records of an object with object permissions.

  5. You can modify those permissions for records users don't own with organization–wide defaults. You can never use organization–wide defaults to grant users more access than they have through their object permission.

  6. You can determine the organization–wide defaults you need for your app by answering the following questions for each object.

    * Who is the most restricted user of this object?

    * Is there ever going to be an instance of this object that this user shouldn't be allowed to see?

    * Is there ever going to be an instance of this object that this user shouldn't be allowed to edit?

    * As an example, let's go through and answer the list of questions for the Position object in the Recruiting app.

      -  Who is the most restricted user of this object? A member of the Standard Employee profile. All that they're allowed to do is view a position.
    
      - Is there ever going to be an instance of this object that this user shouldn't be allowed to see? No. Although the values for the minimum and maximum pay are hidden from standard employees, they're still allowed to view all position records.

      - Is there ever going to be an instance of this object that this user shouldn't be allowed to edit? Yes. Standard employees aren't allowed to edit any position record. This means that the sharing model for the Position object should be set to Public Read Only.

  7. You can set the sharing model for that object to one of these settings.

    * Private -	Only the record owner, and users above that role in the hierarchy, can view, edit, and report on those records. 

    * Public Read Only - All users can view and report on records but not edit them. Only the owner, and users above that role in the hierarchy, can edit those records.

    * Public Read/Write - All users can view, edit, and report on all records. 

    * Controlled by Parent - A user can perform an action (such as view, edit, or delete) on a contact based on whether he or she can perform that same action on the record associated with it.

  8. Sharing rules work best when they're defined for a particular group of users that you can determine or predict in advance, rather than a set of users that frequently changes. 

    * For example, in the Recruiting app, it’s important to share every position, candidate, job application, and review with every recruiter. Since recruiters all belong to either the Recruiting Manager or Recruiter roles in the role hierarchy, we can easily use a sharing rule to share those objects with the Recruiting Manager role and its subordinates.
    
    * Recruiters need read and update access on every position, candidate, job application, and review record that exists in the app.
        Yes. As we discussed previously, it's easy to pick out the group of recruiters in our role hierarchy.
    
    * Hiring managers need read and update access on position and job posting records on which they're the hiring manager.
        No. It's too hard to predict which positions will be assigned to which hiring manager. We'll need to handle this use case some other way.
    
    * Hiring managers need read access on candidate records on which they're the hiring manager.
        No. Again, it's too hard to predict which positions will be assigned to which hiring manager.

    * Hiring managers need read and update access on every job application and review record.
        Yes. Since we're not restricting which job applications and reviews a hiring manager gets to read and update, we can easily pick out all of the hiring managers from our role hierarchy and define a sharing rule for them.
    
    * Interviewers need read access on the candidate and job application records for people they're interviewing.
        No. As we discussed previously, it's hard to predict who will be a member of an interview team for a particular position. 

# Define a Public Group 

  1. Before creating a sharing rule, it’s important to set up the appropriate public group.

  2.  A public group is a collection of individual users, other groups, individual roles or territories, and/or roles or territories with their subordinates that all have a function in common.

    * For example, users with the Recruiter profile as well as users in the SW Dev Manager role both review job applications. 

  3. Using a public group when defining a sharing rule makes the rule easier to create and, more important, easier to understand later, especially if it's one of many sharing rules that you're trying to maintain in a large organization.

  4. Create a public group if you want to define a sharing rule that encompasses more than one or two groups or roles, or any individual

# Setting up a Public Group 

  1. In Setup, use the Quick Find box to find Public Groups.

  2. Click New.

    * The New Public Group page allows you to choose other public groups, individual roles, individual roles including the roles’ subordinates, or individual users. 

  3. Give your rule the label Reviewers.

    * The Group Name text box populates automatically when you click it. This is the unique name used by the API and managed packages.

  4. In the Search drop-down list, choose Roles.

  5. In the Available Members list, select SW Dev Manager, Director Product Management, and Director QA, then click Add.

  6. Go back up to the Search drop-down list, and this time choose Role and Subordinates.

  7. In the Available Members list, select Recruiting Manager, click Add, and save.

# Define a Sharing Rule

  1. In Setup, use the Quick Find box to find Sharing Settings. This is the same page used to define org-wide defaults.

  2. In the Manage sharing settings for drop-down list, choose Job Application.

    * Choosing an object in this drop-down list allows you to focus in on the org-wide defaults and sharing rules for a single object at a time rather than looking at all of them in a long page—a useful thing if you've got a large org with multiple custom objects. Let’s use this Sharing Rules related list to create a sharing rule that applies to both the Job Application and the Review objects.

  3. In the Job Application Sharing Rules area, click New and give your rule the label Review Records.

    * The Rule Name text box populates automatically when you click it.

  4. For the rule type, make sure Based on record owner is selected.

  5. For Select which records to be shared, select Public Groups, then choose Entire Organization.

  6. For Select users to share with, select Public Groups, then choose Reviewers.

  7. For Select the level of access for the users, select Read/Write, then save.

# How to Set Organization wide sharing defaults

  1. From Setup, enter Sharing Settings in the Quick Find box, then select Sharing Settings.

  2. Click Edit in the Organization-Wide Defaults area.

  3. For each object, select the default access you want to use. (Recall the questions you answered in the previous section to help you figure out which default access setting is most appropriate.)
  
  4. To allow employees at higher levels in the role hierarchy to access records automatically, select Grant Access Using Hierarchies for any custom object that does not have default access of Controlled by Parent.

# Tips on setting Organization wide sharing settings 

  1. In environments where the organization-wide sharing setting default for an object is set to Private or Public Read Only, you can grant users more access to records by setting up a role hierarchy or defining sharing rules. Just remember, you can only use sharing rules to grant more access. You cannot use them to restrict access to records beyond what was originally specified with the organization–wide sharing defaults.

  2. By default, Salesforce uses hierarchies, like a role hierarchy, to automatically grant record access to users above the record owner in the hierarchy. Setting an object to Private makes those records visible only to record owners and users above them in the role hierarchy.

    * If you want to disable access to records for users above the record owner in the hierarchy for custom objects, use the Grant Access Using Hierarchies checkbox.

    *  If you deselect this checkbox for a custom object, you restrict record access to only the record owner and users granted access by the organization–wide defaults.

  3. When you update the organization-wide defaults, you cause a sharing recalculation to run automatically and apply any access changes to your records. 

    * You receive a notification email when the recalculation completes and you can refresh the Sharing Settings page to see your changes. To view the updated status, from Setup, enter View Setup Audit Trail in the Quick Find box, then select View Setup Audit Trail.
  
  4. Once you've secured your data with organization-wide defaults, the resulting settings might be too restrictive for some users. You can then use the remaining record-level security controls: role hierarchies, sharing rules, and manual sharing to open up record access selectively to specific employees who need it.



# Audit System Use

  1. Auditing provides important information for diagnosing potential security issues or dealing with real ones.

  2. Someone in your organization should audit regularly to detect potential abuse. Look for unexpected changes or patterns of use.
  Record Modification Fields

  3. Basic Audit Methods

    * Record Modification Fields - All objects include fields to store the name of the user who created the record and who last modified the record. This provides some basic auditing information.

    * Login History - You can review a list of successful and failed login attempts for the past six months.

    * Field History Tracking - You can turn on auditing to automatically track changes in the values of individual fields. Although field-level auditing is available for all custom objects, only some standard objects allow it. 

    * Setup Audit Trail - The Setup Audit Trail logs when modifications are made to your organization’s configuration.

# Whitelist Trusted IP ranges for the Org 

  1. The first time you log in to Salesforce, the IP address is cached in your browser.

  2. . Anytime you log in from a different IP address, you will be asked to verify your identity, typically by entering a verification code. You can bypass this step for trusted IP ranges. 

  3. How to Whitelist Ip

    * From Setup, in the Quick Find box, enter Network Access, then select Network Access.

    * Click New.

    * Enter the start and end point of the range of trusted IP addresses, and click Save.

  4. Restrict Login Access by IP Address Using Profiles - You can restrict where users can log in from using profiles. 

    * From Setup, in the Quick Find box, enter Profiles, then select Profiles.

    * Select a profile and click its name.

    * Click IP Ranges. If you don't have Enhanced Profile Interface enabled, scroll down to the Login IP Range related list.
    
    * Click New.

    * Enter the start and end point of the range of trusted IP addresses, and click Save.

  5. Restrict Login Access by Time - For each profile, you can specify the hours when users can log in. 

    * In Setup, use the Quick Find box to find Profiles.

    * Click the profile you want to change.

    * Under Login Hours, click Edit.

    * Set the days and hours when users with this profile can log in to the organization.

      - To allow users to log in at any time, click Clear all times.

      - To prohibit users from using the system on a specific day, set the start and end times to the same value.

  
