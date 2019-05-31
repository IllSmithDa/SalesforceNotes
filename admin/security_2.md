# Manage Object Permissions

  1. You can control whether a group of users can create, view, edit, or delete any records of that object. 

  2. You can set object permissions with profiles or permission sets. A user can have one profile and many permission sets. 

    * A user’s profile determines the objects they can access and the things they can do with any object record (such as create, read, edit, or delete). 

    * Permission sets grant additional permissions and access settings to a user.
  
  3. Use profiles to grant the minimum permissions and settings that all users of a particular type need. Then use permission sets to grant more permissions as needed. The combination of profiles and permission sets gives you a great deal of flexibility in specifying object-level access. 

    * Example: Ben, a hiring manager, should be able to access the recruiting records related to his open positions, but shouldn't have access to other   recruiting records (unless they're owned by other hiring managers who report to him). Also, there are certain sensitive fields that he has no need to see,like the social security number field. Let’s consider the permissions Ben needs for each of the key custom objects in the app.

      - Position — Ben should be able to post new positions, as well as update and view all fields for positions for which he's the hiring manager, but he should only be able to view other managers' positions.

      - Candidate - Ben should only be able to view those candidates who have applied for a position on which he's the hiring manager. Also, since Ben has no reason to see a candidate's social security number, this field should be restricted from his view.

      - Job Application - Ben needs to be able to update the status of job applications to specify which candidates should be selected or rejected. However, he should not be able to change the candidate listed on the job application, nor the position to which the candidate is applying, so we'll have to find a way of preventing Ben from updating the lookup fields on job applications.

      - Review - To make a decision about the candidates who are applying, Ben needs to see the reviews posted by the interviewers, as well as make comments on them if he thinks the interviewer was being too biased in his or her review. Likewise, Ben needs to be able to create reviews so that he can remember his own impressions of the candidates he interviews.

    * Example: Mario, a recruiter, needs to be able to create, view, and modify any position, candidate, job application, or review that's in the system. He also needs to view and modify the recruiting records that all of the other recruiters own, since all the recruiters work together to fill each position, regardless of who created it.

      - We need to make sure a recruiter will never accidentally delete a record with information about a candidate. That’s because state and federal laws require recruitment-related records be saved for a number of years, so that if a hiring decision is questioned, it can be defended in court.

    * Example: Melissa is an engineer who interviews candidates for highly technical positions. She should be able to view only the candidates and job applications to which she's assigned as an interviewer. Also, she shouldn't be able to view the minimum and maximum salary values for any of the positions or the social security number of any candidate, as that’s sensitive information that has nothing to do with her job.

    * Example: Employees, such as Harry, are often the best resources for recruiting new hires, even if they are not active hiring managers or interviewers. For this reason, we need to make sure that employees can view open positions, but that they can't see the values for the positions' minimum and maximum salary fields—otherwise they might tip off friends to negotiate for a position's maximum salary value! Harry also shouldn't be able to view any other records in the Recruiting app.

# Use Profiles to restrict Access

  1. Each user has a single profile that controls which data and features that user has access to. A profile is a collection of settings and permissions. Profile settings determine which data the user can see, and permissions determine what the user can do with that data.\

    * The settings in a user’s profile determine whether she can see a particular app, tab, field, or record type

    * The permissions in a user’s profile determine whether she can create or edit records of a given type, run reports, and customize the app.

    * Standard Profiles include: 

      - Read Only

      - Standard User

      - Marketing User

      - Contract Manager

      - System Administrator

    * Each standard profile includes a default set of permissions for all standard objects available on the platform.

    * System Administrator profile has the widest access to data and the greatest ability to configure and customize Salesforce. The System Administrator profile also includes two special permissions:

      - View All Data

      - Modify All Data

    * These permissions override all other sharing settings, so use caution when assigning them to any profile other than System Administrator. You can view a list of all standard and custom profiles in Setup. 

    * You can’t edit the object permissions on a standard profile. However, you can clone any existing profile, and use that as the basis for a new profile, adjusting the apps and system settings as needed.  Each profile can then be configured to provide the specific type of data access required for a particular role. You can then use permission sets to grant additional permissions, as required.

# Managing Profiles 

  1. The profile overview page provides an entry point for all of the settings and permissions for a single profile. In Setup, use the Quick Find box to find Profiles and click the profile you want to view.

  2. The easiest way to create a profile is to clone an existing profile that’s similar to the one you want to create, and then modify it. 

    * To do that, find User Management Settings in the Quick Find box in Setup, then enable Enhanced Profile User Interface and click Save

  3. To clone Profile

    * In Setup, use the Quick Find box to find Profiles.
    
    * Click Clone next to a profile similar to the one you want to create.
    
    * Give your new profile a name, and save.

  4. To Assign Profile 

    * Find Profiles in Setup.

    * Select a profile and then click Object Settings. Click Edit to see its settings.

    * Set the most restrictive settings and permissions you can for this user type, and save.

    * Find Users in Setup and click Edit next to one of them.

    * From the Profile dropdown select the profile you just set up, and save.

# Permission Sets 

  1. A permission set is a collection of settings and permissions that give users access to various tools and functions. The settings and permissions in permission sets are also found in profiles, but permission sets extend users’ functional access without changing their profiles.

  2. Permission sets make it easy to grant access to the various apps and custom objects in your org, and to take away access when it’s no longer needed.

  3. Users can have only one profile, but they can have multiple permission sets.

  4. You'll be using permission sets for two general purposes: to grant access to custom objects or apps, and to grant permissions—temporarily or long term—to specific fields.

  5. A permission set’s overview page is the entry point for all of the permissions in a permission set. To open a permission set overview page, find Permission Sets in Setup, then select the permission set you want to view. In each permission set, permissions and settings are organized into app settings, system settings, object permissions, and field permissions.

# Create Permission Set 

  1. Use the Quick Find box to find Permission Sets in Setup.

  2. Click Clone next to the set you want to copy.

  3. Enter a label and a description.

    * he API name is a unique name used by the API and managed packages. It automatically replicates the label, but you can modify it.

  4. If this is a new permission set, select a user license option.

    * If you plan to assign this permission set to multiple users with different licenses, select --None--.

    * If only users with one type of license will use this permission set, select that user license.

  5. If only users with one type of license will use this permission set, select that user license.

  6. In the permission set toolbar, click Manage Assignments, then click Add Assignments. 

  7. Select the users to assign to this permission set and click Assign. Review the messages on the Assignment Summary page. If any users weren’t assigned, the Message column tells you why.

  8. Click Done to return to a list of the users assigned to the permission set

# Control Access to Fields 

  1. Modify Field-level Security 

    * In some cases, you want users to have access to an object, but limit their access to individual fields in that object.

    * Field-level security settings—or field permissions—control whether a user can see, edit, and delete the value for a particular field on an object. 

    * These are the settings that allow us to protect sensitive fields such as a candidate's social security number without having to hide the candidate object

    * Unlike page layouts, which only control the visibility of fields on detail and edit pages, field-level security controls the visibility of fields in any part of the app, including related lists, list views, reports, and search results. 

    *  In fact, to make absolutely sure that a user can't access a particular field, it's important to use the field-level security page for a given object to restrict access to the field.

      - There are simply no other shortcuts that provide the same level of protection for a particular field.

    * For example, here are some field-level security settings you can set for the Recruiting app.

      - Position object—hide minimum and maximum pay from standard employees and interviewers.
      
      - Candidate object—hide social security numbers from hiring managers and interviewers.
      
      - Job Application object—make the Position and Candidate lookup fields read-only for hiring managers.

    * Field settings can be applied either by modifying profiles or permission sets or from the Field Accessibility menu in Setup. 

    * After setting field-level security for users, you can:

      - Create page layouts to organize the fields on detail and edit pages. 

      - Verify users’ access to fields by checking the field accessibility.

      - Customize search layouts to set the fields that display in search results, in lookup dialog search results, and in the key lists on tab home pages.

# Restrict Field Access with a Profile

  1. Use the Quick Find box to find Profiles in Setup.
    
  2. Select the profile you want to change. "Standard User" will do nicely.
  
  3. Click Object Settings and select the object for which you want to update the field settings.
    
  4. Click Edit.
    
  5. For each field, specify the kind of access you want for users with this profile, and save your settings.

# Add Field Access with a Permission Set

  1. Let’s look at how field settings can be applied by modifying permission sets. Remember, a permission set is for expanding a user’s access to fields that are restricted in their profile.

  2. We worked with Permission Sets when we set up our custom objects

    * In Setup, use the Quick Find box to find Permission Sets.

    * Select a permission set and click Object Settings.

    * Click the object you're working with, then click Edit.

    * Under Field Permissions, specify the kinds of access your interviewers need, then save this permission set.

    * Click Manage Assignments and select the users who you expect to need the permissions you’ve just specified. Click Add Assignments and Done, and you're done!

# Control Access to Records 

  1. To control data access precisely, you can allow particular users to view specific fields in a specific object, but then restrict the individual records they're allowed to see.

  2. Record access determines which individual records users can view and edit in each object they have access to in their profile. First ask yourself these questions: 

    * Should your users have open access to every record, or just a subset?

    * If it’s a subset, what rules should determine whether the user can access them?

  3. Let’s say you create a new profile called Recruiter to give recruiters the object-level permissions they need. You restrict the power to delete recruiting-related objects, so recruiters will never be able to delete these objects. However, granting recruiters permission to create, read, or edit recruiting objects does not necessarily mean recruiters can read or edit every record in the recruiting object. This is a consequence of two important concepts: 

    * The permissions on a record are always evaluated according to a combination of object-level, field-level, and record-level permissions.

    * When object-level permissions conflict with record-level permissions, the most restrictive settings win.

    * That means even if you grant a profile create, read, and edit permissions on the recruiting objects, if the record-level permissions for an individual recruiting record are more restrictive, those are the rules that define what a recruiter can access. 

# Role Hieracrhy

  1. A role hierarchy works together with sharing settings to determine the levels of access users have to your Salesforce data. Users can access the data of all the users directly below them in the hierarchy. 

  2.  Each role in the hierarchy just represents a level of data access that a user or group of users needs.

    * A manager always has access to the same data as his or her employees, regardless of the org-wide default settings.
    
    * Users who tend to need access to the same types of records can be grouped together. We'll use these groups later when we talk about sharing rules.

  3. Users at any given role level can view, edit, and report on all data owned by or shared with users below them in the role hierarchy, unless your sharing model for an object specifies otherwise. 

  4. Specifically, in the Organization-Wide Defaults related list, if the Grant Access Using Hierarchies option is disabled for a custom object, only the record owner and users granted access by the org-wide defaults receive access to the object's records.

  5. By default, the Grant Access Using Hierarchies option is enabled for all objects. It can only be changed for custom objects.

  6. To control sharing access using hierarchies for any custom object, enter Sharing Settings in the Quick Find box and select Sharing Settings. 

# Define a Role Heirarchy 

  1. From Setup, use the Quick Find box to find Roles.

    * The default view for this page is the tree view, as indicated in the drop-down list on the far right side of the Role Hierarchy title bar. When creating a role hierarchy, it's probably easiest to stick with this or the list view, because they both make it easy to see how the roles all fit together in the hierarchy.

  2. Just under the company name, click Add Role. 

  3. In the Label text box, enter CEO

  4. In the This role reports to text box, click the lookup icon Lookup icon and click Select next to the name of your org. By choosing the name of the org in the This role reports to text box, we’re indicating that the CEO role is a top-level position in our role hierarchy and  doesn't report to anyone.

  5. In the Role Name as displayed on reports text box, enter CEO.

  6. Leave any other options, such as Opportunity Access, set to their defaults, and save.

  7. Now that you’ve created your first role, you can assign the appropriate user to it. Click CEO, and on the CEO role detail page, click Assign Users to Role.

  8. In the Available Users drop-down list, select All Unassigned.

  9. Choose a user from the list, and click Add to move her to the Selected Users for CEO list, then save.