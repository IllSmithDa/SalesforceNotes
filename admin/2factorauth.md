# What Is Two-Factor Authentication?

  1. What are the two factors?

    * Something users know, like their password

    * Something users have, such as a mobile device with an authenticator app installed

      - The second factor of authentication provides an extra layer of security for your org. 

    * As an admin, you can require it every time your users log in. Or you can require it only in some circumstances, such as when users log in from an unrecognized device or try to access a high-risk application.

    * Users can be prompted for two-factor authentication in various circumstances.

      - Every time they log in to Salesforce, including API logins. 

      - When they access a connected app, dashboard, or report. This process is known as step-up or high-assurance authentication.

      - During a custom login flow or within a custom app, for example, before reading a license agreement. More on this topic later in the trail.


# How Two-Factor Authentication Works

  1. From Setup, enter Session Settings in the Quick Find box, then select Session Settings.

  2. Under Session Security Levels, make sure that two-factor authentication is in the High Assurance category.

# Create a permission set for two-factor authentication

  1. Log in again as the system administrator of your DE org. 

  2. From Setup, enter Permission in the Quick Find box, then select Permission Sets.

  3. Click New.

  4. Label the permission “2fa Auth for User Logins”.

  5. Click Save.

  6. Under System, click System Permissions. Now you’re on the detail page for the 2fa Auth for User Logins permission set. 

  7. Click Edit.
  
  8. Select Two-Factor Authentication for User Interface Logins.

  9. Click save

# Assign the permission set to the specified User

  1. On the detail page of the new permission set, click Manage Assignments.

  2. Click Add Assignments. On the list of users, select the checkbox next to Sia’s account. (If you wanted, you could assign up to 1,000 users at a time.)

  3. Click Assign.

# Connect the Salesforce Authenticator Mobile App to a User Account

  1. PHONE: Download and install Salesforce Authenticator for iOS from the App Store or Salesforce Authenticator for Android from Google Play.
  
  2. PHONE: Tap the app icon to open Salesforce Authenticator.

  3. DESKTOP: If you’re still logged in to your DE org as a system administrator, log out.

  4. DESKTOP: Use Sia’s username and password to log in. Salesforce prompts you to connect Salesforce Authenticator to Sia’s account.

  5. PHONE: Page through the brief app tour to learn how Salesforce Authenticator works.

  6. PHONE: When you’re done with the tour, enter Sia’s mobile number to create a backup of her accounts. Authenticator sends you a text message with a link to verify Sia’s mobile number. When you get the text message, tap the link to open the Authenticator app. The app prompts you to set a passcode. Sia will use this passcode if she needs to restore her accounts. If you don’t want to pick a passcode for Sia, she can set up backups later.

  7. Tap + to add Sia’s account to Salesforce Authenticator. The app displays a two-word phrase. (Hey, did you get an especially poetic or amusing phrase? Let us know! #Trailhead #AwesomePhrase #SalesforceAuthenticator)

  8. DESKTOP: Enter the phrase in the Two-Word Phrase field.

  9.  DESKTOP: Click Connect.

  10. PHONE: Salesforce Authenticator shows you details about the account you’re connecting: Sia’s username and the name of the service provider—in this case, Salesforce.

  11. PHONE: Tap Connect.

  12. PHONE: Tap Approve to finish logging in to Salesforce as Sia.

  13. DESKTOP: Sia’s in! She can go about her business.

# Automate the Authentication Process

  1. If she lets Salesforce Authenticator use her phone’s location services, she can tell the app to verify her activities automatically when she’s in a particular spot.

  2. DESKTOP: Log out of Sia’s account and then log in as Sia again.

  3. PHONE: At the prompt, select Always verify from here.

  4. DESKTOP: Log out of Sia’s account and log in again. Voila! You’re not prompted for a password. Salesforce Authenticator recognizes that Sia’s logging in to her Salesforce account again using the same device and at the same location. Access granted automatically!

  5. What if Sia no longer trusts a location? Simple. She swipes left. She can clear all trusted locations at once by selecting Salesforce Authenticator settings icon and then Clear Trusted Locations.

  6. Want to restrict users’ automated verifications to trusted IP addresses only, such as your corporate network? Or prevent them entirely? You can. When logged in as an admin, go to your org's Session Settings and change what’s allowed.

# What Happens If Sia Loses Her Mobile Phone?

  1. Log in as an administrator.
  
  2. From Setup, enter Users in the Quick Find box, then select Users.

  3. Click Sia’s name.

  4. On Sia’s user detail page, click Disconnect next to App Registration: Salesforce Authenticator.

# Look Who’s Been Logging In to Your Org

  1. Log in as the system administrator of your DE org. 

  2. From Setup, enter Verification in the Quick Find box, then select Identity Verification History.

