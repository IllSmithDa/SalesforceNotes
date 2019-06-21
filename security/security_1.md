# Org level security

  1. User login

    * First level of security which includes standard username and password

    * 2 Factor authentication - having a second layer of authentication required to login

      - username/password + mobile device or email login activation required to login

      - both required to login

    * Username has to be in email format though it doesn't have to be a real email

    * Username must be unique across all Salesforce organizations

  2. Ip restriction and login hours can be assigned further controlling when and where a user
  can access salesforce 

# Restrictions

  1. Hour login settings

    * Found in the profile settings

    * restrict hours when user be able to login

    * If a user that is already logged in and the hours are over, the user will no longer be able to create, update or delete the data. He will not be able to mnaipulate the data. 

  2. IP Address restriction

    * restricts login access to only certain IP addresses to prevent data leaks. 

    * In cases for dynamic IP, you can send a vertification link to an email which might include a code, satisfy the authentication system, and login sucessfully from IP addresses outside the IP ranges.

    * This is a profile based security settings

  3. Trusted IP
    
    * list of IP addresses that user can login without having to challenge for identity vertification

    * This is a organizational wide security settings 

    * If a user attempts to login outside of the trusted IP range, they would not be able to login at all. 

# Object level security

  1. Profile based 

    * User based security based on user responsbility

    * profile contains user permissions and controls what they have access to and what they can edit

    * salesforce allows for custom profile for custom access to objects, fields etc

    * You can delete only custom profiles you create as standard ones must remain

    * You can only edit or clone standard profiles

    * You can access Profiles using the profile settings

  2. All Profiles are always linked to a Salesforce license and all users are linked to a profile and salesforce license

  3. Custom Profile will be checked if profile is custom 

  4. You can control Profile for what apps are visible

  5. Tab Settings 

    * Default On 

      - This will be visible on the top horizontal ribbon and all tabs

    * Default Off

      - May not be visible on the top horizontal ribbon
        
      - Still visible on All tabs

    * Tab hidden

      - Hidden on all tabs and hidden on horizontal ribbon 

  6. Standard Object Permissions

    * Allows you to control a profile's control over CRUD operations over objects

    * CRUD - Create, Read, Update, Delete

    * Note that for standard profiles, you are not allowed to change permissions for CRUD for any objects standard or custom. Its only available for custom profiles

  7. Custom Object Permissions 

    * Same as Standard Object permissions

  8. You can also change password policies at the bottom 

  9. Profile can also control field level security to see which fields profiles have read, write acess to 

  10. All profiles have access to setup. You can control what they can in setup. 

# Record Level Security - Comes in 4 levels 

  1. OWD - Organization wide defaults

    * minimal level access for every user in the organization

    * Go to sharing settings in quick find and you will find OWD option there for each object 

    * 4 Options found that only apply for those above you in the heirarchy. Does not apply for those below you 

      - Public - can read your object records

      - Public read/read write - Those above you can read and write on the object record

      - private - only record owner are allowed to see that record

    * Objects that are child objects inherit from the parent or master object. 

      - If parent or master object is set to private, the child object is also set to private

  2. Roles 

# Roles vs Profile

  1. The difference is very subtle

  2. While every user must be assigned a profile, roles are not mandatory for a user. 

    * THe system will not complain if you leave role left unspecified

  3. Role is part of record level security 

  4. Profile is part of field and object level security

# Role Heirarchy 

  1. CEO, Director, VP of sales,
    
    * regional heads (WEST, EAST, CENTRAL, CANADA, LONDON)

    * state level heads 

    * city sales manager (Los Angeles, New York City etc)

    * sales executives

      - illustartaion of a typical sales heirarchy

    * Products they may be selling

    * Sales target 

    * Tracking opportunities

    * security - can only see record sales of his own team members

    * The state level can see all deatils of city and below

    * Role heirarchies are to model after the organization structure, reporting structure

      - over 95 percent of time, role heirarchies perfectly model after organization structure

    * You can set up Roles in the quick find settings 

# Standard Profiles

  1. Standard profiles cannot be deleted but can be cloned but custom ones can

  2. Access permissions for standard profiles cannot be edited

    * Note that for standard profiles, you are not allowed to change permissions for CRUD for any objects standard or custom. Its only available for custom profiles

  3. Standard profiles have access to all standard objects

  4. Access to tabs and apps can be configured for standard profiles

# Users

  1. Required Fields for creating a user
    
    * last name 
    
    * alias
    
    * email
    
    * username
    
    * nickname
    
    * role
    
    * user license 
    
    * profile

# Field level security

  1. Profile based 

# Record level security

  1. Organziation wide defaults or OWD

  2. private, public read, public read/write

  3. sharing access to particular users, groups or roles

  4. manuel sharing

  5. Go sharing rules to change organization wide defaults

  6. permissions settings used to increase current user permissions

    * often applied with private OWD
    