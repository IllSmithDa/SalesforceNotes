# Public Grouping 

  1. users, public groups (nesting)

  2. You can group all your users into a public group

  3. Just go to setup, Public Groups in quick find and create new public groups 

  4. Just because roles have the same level, they cannot see each other's records unless some other sharing rule that allows them to be shown to each other

# Sharing Groups

  1. Go Setup, Sharing settings to create sharing groups

  2. Criteria based sharing rules 
    
    * By setting criteria to match certain records, you can share records with that group even if they do not have permissions based on their role, profile settings, heirarchy, etc. 

  3. Record owner based sharing rules 


# Manual Sharing

  1. You can also manually share a record with anyone else by going to the record itself and use manual sharing settings 

  2. You have to enable manual sharing in the setup settings

# Notes about Profiles

  1. You have to make sure to go to Profiles settings, edit, 

  3. You can also see records that you own even if it was created origally by someone higher in the heirarchy

# Role heirarchy

  1. You can see any records from those that own records that also report to you. 

  2. You can always see records from heirarchy lower than you even if they do not directly report to you

# OWD 

  * Mimimum access level and is always overwritten by profile, which is overwritten by role heirarchy which is then overwritten by manual sharing and sharing rules. 

  * sharing rules and manual sharing will overwrite every other level

  * For OWD, you only have to set up for the parent role as child role will inherit parent settings

  * For other levels of security, you will have to manually set up for parent and child 

# Mass Transfer Records

  * Transfers records to give another user access to standard and custom objects 

  * Mass transfer does not overrule profile read/write access so make sure they have access before you attempt a transfer

  * Go to setup, Enter Mass Transfer Records
  
    - add user you to transfer to 
    
    - add criteria if necessary, 
    
    - click find, select records you wish to transfer and click transfer

# Permission Sets 

  1. In a role heirarchy, people ofen are changing roles, moving up and down a heirarchy

    * Permission sets allows admin to add new permissions, access level without constantly managing 
    and creating new profiles

  2. If a user that did not have delete permission, now needs it, you can create a permission set and assign it to the base profile. 

    * Permission set can be set up for a principal role, and then assign it to a different user who does not have a principal role, but will now share principal permission set

    * You can not use permissions sets to reduce privleges to a assigned profile and user

    * Access Permission sets by going to setup, quick find permission sets, create new and assign the needed permissions

    * You can manage and assign permissions by going to Permissions Sets, Click on the permission name, click manage assignments and add assignment with the desired user and assign

    