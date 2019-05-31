# Single Sign On

  1. With a custom domain and login page, you make it easy for employees to log in to your Salesforce org with a secure, easy-to-remember URL.

    * Do you want to make it even easier so that they don’t have to log in at all? Then set up single sign-on (SSO). 

  2. SSO has lots of advantages.

    * You spend less time managing passwords.

    * Your employees save time when they don’t have to manually log in to Salesforce. Did you know that users take 5–20 seconds to log in to an online application? Those seconds add up.

    * More people use Salesforce. Users can send out links to Salesforce records and reports, and their recipients can open them in a single click.

    * You can manage access to sensitive information from one place.

    * You can also set up outbound SSO in which users log in to Salesforce and then access other services without logging in again. We’ll save that topic for another module.

# Configure Inbound SSO with a Third-Party Identity Provider

  1.  You’ll set up inbound SSO using the Axiom Heroku web app as the identity provider.

# Step 1: Create a Federation ID

  1. It’s basically a term that the identity industry uses to refer to a unique user ID. Typically, you assign a Federation ID when setting up a user account. 

  2. From Setup, enter Users in the Quick Find box, then select Users.

  3. Click Edit next to Sia’s name.

  4. Under Single Sign On Information, enter the Federation ID: sia@jedeye-tech.com.

  5. Click Save.

# Step 2: Set Up Your SSO Provider in Salesforce 

  1. In this step, you’re on the Salesforce side providing information about the identity provider, in this case, Axiom.

  2. In a new browser window, go to http://axiomsso.herokuapp.com.

  3. Click SAML Identity Provider & Tester.

  4. Click Download the Identity Provider Certificate. 

    * You upload this certificate later to your Salesforce org, so remember where you save it.

  5. In your Salesforce org, from Setup, enter Single in the Quick Find box, then select Single Sign-On Settings.

  6. Click Edit.

  7. Select SAML Enabled. 

  8. Click Save.

  9. In SAML Single Sign-On Settings: 

    * Click New.

    * Enter the following values. 

      - Name: Axiom Test App
        Issuer: http://axiomsso.herokuapp.com
        Identity Provider Certificate: Choose the file you downloaded in step 3.
        Request Signature Method: Select RSA-SHA1.
        SAML Identity Type: Select Assertion contains the Federation ID from the User object.
        SAML Identity Location: Select Identity is in the NameIdentifier element of the Subject statement.
        Service Provider Initiated Request Binding: Select HTTP Redirect.
        Entity ID: Enter your My Domain name, including “https.” Use the subdomain name that you set up in the “Customize Your Login Process with My Domain” unit. Copy and paste it from the browser   address bar. 

  10. Click Save and leave the browser page open.

# Step 3: Link Your Identity Provider to Salesforce

  1. Now that you’ve configured Salesforce to know about the identity provider (Axiom), you teach your identity provider about your service provider (Salesforce).

  2. Return to the Axiom web app. If you don’t have the app open in a browser window, go to http://axiomsso.herokuapp.com.

  3. Click SAML Identity Provider & Tester.

  4. Click generate a SAML response.

  5. Enter the following values. Leave the other fields as is. 

    * SAML Version: 2.0
      Username or Federated ID: sia@jedeye-tech.com
      Issuer: http://axiomsso.herokuapp.com
      Recipient URL: Get the URL from the Salesforce SAML Single Sign-On Settings page. Don’t see it? It’s at the bottom labeled Salesforce Login URL.
      Entity Id: The Entity ID from the Salesforce SAML Single Sign-On Settings page.

# Step 4: Make Sure It All Works

  1. In the Axiom settings browser window, click Request SAML Response. (It’s way down at the bottom.) 

  2. Axiom generates the SAML assertion in XML. Does it look like language used by a robot communicating with desert outpost moisture evaporators? Look again. You can see that it doesn’t look all that bad. To get to the interesting information, scroll through the XML. 

  3. Click Login.


  