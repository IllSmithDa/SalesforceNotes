# A Mobile-First World

  1. The latest stats (2018 State of the Connected Customer) show that at least 82% of customers prefer to engage with brands through mobile devices.

# Mobile-First Identity

  1. How about when you want to get to a site quickly, but your password doesn't work? 
   
    * According to recent research: (https://swoopnow.com/passwordless-login), 75% of users quit after a password reset. 30% of online customers abandon their shopping carts if required to register with a password.

  2. Enter Salesforce mobile-first identity where:

    * You don't have to require customers to enter a password to interact with your community.

    * Your customers can get to you anytime, anywhere, and from any device or desktop.

# Salesforce’s Mobile-First Identity Login Experience

  1. Salesforce Mobile-First Identity simplifies the login experience for your customers.

    * we're referring to all aspects of identity verification and authentication: from sign-up, to log in, to handling identity verification, to resetting passwords, to logging out.

  2. Take email verification. Your users can enter their password and immediately get an email message with a verification code that they enter to access the app. 

    * It's not a link to a desktop app that requires another login attempt. This extra step might not sound like much, but it's enough to rule out a hefty percentage of potential business.

    * This feature allows you to protect your apps with authorized access with little effort from you. 

# Available on All External User Licenses

  1. Lincenses including External Identity, Customer Community, Customer Community Plus, Partner Community, Lightning External Apps, Lightning External Apps Plus

  2. Mobile-first identity comes with email verification for free. You can also offer mobile verification via text message for an extra cost

  3. SMS messaging requires a Salesforce add-on license for Identity Verification Credits. Purchasing the credits gives your org a predetermined number of SMS messages for mobile identity verification. To evaluate the SMS option, contact your Salesforce account representative.

  4. In Production orgs, you can see if your org has purchased SMS credits on the Company Information Setup page under Usage-based Entitlements.

# What does this mobile-identity feature give you? 

  1. Passwordless Login

    * Salesforce prompts users for their email address or phone number on your community’s login page.

    * Users enter their email address or phone number on the login page.

    * Salesforce sends users a unique verification code to the specified Inbox or phone number.

    * Users enter the verification code on the Salesforce Verify page.

    * Salesforce validates that the code is correct, and that the email or phone number exists and belongs to your org.

    * Users are logged in.

  2. Passwordless Login Versus Login Discovery

    * You choose the Login Discovery Page type from your community's Workspaces Login & Registration page. Salesforce performs the necessary backend work to verify users' identity with their email address or phone number.

    * Why is the page type called Login Discovery? Login Discovery doesn’t know how to verify the user until it determines—discovers—how the user is identified. Think of Login Discovery as a two-step process.

    * First step: Determine the identity of the user, which can be by username, email address, phone number, or a custom identifier that you define.

    * Second step: Challenge users to verify their identity. Users then prove that they are who they say they are.

    * They can be asked to verify their identity by a passwordless method such as:

      - A verification code sent via email or SMS

      - Their social network credentials

      - Salesforce Authenticator

      - A one-time temporary passcode (TOTP)

      - A physical device like a yubikey

    * Or users can be required to enter their password. In other words, Login Discovery supports both password and passwordless login.

    * How you challenge users is completely independent of the identifier. For example, users can be asked to identify themselves with a phone number, but to verify their identity, they might be:

      - Required to enter a verification code received in a text or email message

      - Required to enter their password

      - Redirected to Facebook (or another social network) for social sign-on

# Login Discovery

  1. Login Discovery gives users the option to log in with something other than their username.

  2. For Login Page Type, select Login Discovery Page.

  3. For Login Prompt, enter Email or Phone.

  4. Click Create a Login Discovery Handler. After you save this page (but wait—don't save it yet!), Salesforce generates a default login discovery handler.

    * The Login Discovery Handler points to an Apex class that implements the Login Discovery logic. You can learn more about the handler and how to customize it in the next unit.

  5. For Execute Login As, select yourself. Click Magnifying glass icon and select your name.

    * The Execute Login As field is required and it provides the context in which the Login Discovery handler runs. (In production, admins typically create a system user for this field. This way operations performed by the handler can be easily traced back to the login process.)

  6. Select Allow internal users to log in directly to the community.

  7. Click Save.

  8. Let’s see what your login page looks like with Login Discovery page type.

    * From Administration, click Settings

    * Right-click the URL and select Open Link in Incognito Window (in Chrome) or Open Link in New Private Window (in Firefox or Safari).

# Configurable Self-Registration
  
  1. Mobile-first users like a quick sign-up process. To attract more people to your site, keep sign-up brief.

# Customizations with a Few Lines of Code

  1. Salesforce Mobile-First Identity gives you a simple, clicks-not-code way to set up your mobile-first login experience. But with a few lines a code, you can customize it to address more of your login needs, like allowing users to log in with through their social network account. 

  2. By default, users can log in with their email address or phone number. You can customize login to use another unique identifier, like an account number or license plate.

 # Locate and customize Default Login Discovery Handler

  1. When you create your login discovery handler from the Login & Registration page, Salesforce creates the default handler as an Apex class. 

  2. From the Login & Registration page, under Login Page Setup, note the handler name that is listed in the Login Discovery Handler text box.

  3. In another tab, from Setup, enter Apex Classes in the Quick Find box, and click Apex Classes.

    * The handler appears in a list of classes on the Apex Classes page.

  4. Locate the name of the login discovery handler in the list.

    * It’s not so easy scanning the list of Apex classes to find the handler, is it? We can fix that by renaming the handler to something more recognizable. Plus, by renaming it, you can see at a glance that the handler is customized. The handler no longer has to be “auto created,” so let’s go ahead and change the name to reflect it.

  5. Click Edit next to the name of the handler.

    * The handler name appears on the first line of code.

  6.  Replace the Salesforce name with your own and click Save.

# Understand the default Login Handler

  1. The first step is to get the identifier (email or phone number), passed in from the login page. Then check whether the identifier is in a valid format.

  2. Next, query the database for a user associated with that identifier. If the user is active, and if the identifier is unique, check whether the user has already verified that identifier.

    * If the identifier has been verified, send a verification code via email or text message, and specify where the user goes after successful verification. 

  3. Then redirect the user to the Verify page where the user enters the verification code. If the identifier has not been verified, redirect the user to the page where the user enters a password.

# Customize the Login Discovery Handler for Social Sign-On

  1. Customers often like to log in to a community with their social network credentials, such as Twitter, Google, or LinkedIn. If you’ve set up your org to allow social sign-on, Login Discovery makes it even easier for your customers.

  2. Set Up Salesforce Auth. Providers.

    * The first step to customizing the handler for social sign-on is to check whether your org is configured for the social networks that you want to support. Your org must have authentication providers to connect to each one.

      - Salesforce provides several default authentication providers to connect with popular social networks—and we add new ones as they emerge. If you don’t have the social networks you want, you can create them in a few clicks.

    * From Setup, enter Auth. Providers in the Quick Find box, and select Auth. Providers.

    * Create an authentication provider for a social network.

  3. Locate SSO URL for Your Social Network.

    * When you add Auth. Providers programmatically, you need the appropriate SSO Initialization URL to the social network.

    * From Setup, enter Auth. Providers in the Quick Find box, and select Auth. Providers.

    * Click the link to the name for your desired social network. You click the name itself, not the Edit link.

    * Expand Communities.

      - The SSO URL for each authentication provider in your org is listed.

      - Note the Single Sign-On Initialization URL listed for the desired authentication provider.

  4. Add the SSO Logic to Your Login Discovery Handler.

    * Add logic to your Login Discovery handler to determine when users are redirected to their social network. 
    
    * Your custom code includes logic to determine whether the user should use a social network or log in directly to Salesforce. 
    
      - For example, it can look up a custom field on the User object.

# Gather User Information with Request Attributes

  1. You can determine login policies based on the user's browser state when they access the login page.

    * For example, you can have different policies based on whether people are logging in from the United States versus people logging in from China.

  2. To collect the browser data, use the requestAttributes parameter of the LoginDiscovery.login method. 
    
    * The parameter passes in these values: CommunityUrl, IpAddress, UserAgent, Platform, Application, City, Country, and Subdivision. City, Country, and Subdivision values come from IP geolocation.

    * e.g 
    private PageReference getSsoRedirect(User user, String startUrl, Map<String, String> requestAttributes) {
      
      // Send iOS users through Facebook SSO
      if(requestAttributes.get('Platform') == 'iPhone') { 
          String ssoURL = 'https://sampledomain.my.salesforce.com/nto/services/auth/sso/Facebook';  
          return new PageReference(ssoURL);
      }
      return null;
    }

# Ensure Uniqueness for External Users

  1. Your production org can have multiple users with the same verified email address and mobile number. But your customers must have unique identifiers.

  2. To address this problem, you can add a few lines of code to the login discovery handler that filters users to ensure uniqueness.