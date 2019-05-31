# Customize Your Salesforce Org URL with My Domain

  1. What Is My Domain?

    * My Domain is sort of like creating your own empire within the Salesforce universe. It’s a Salesforce Identity feature that lets you personalize your Salesforce org by creating a subdomain (empire) within the Salesforce domain (universe).

      - somethingReallycool - Equals your personal subdomain within the Salesforce domain. Typically, it's your company name or whatever drives your brand.

      -  .my.salesforce.com - Is the Salesforce domain name—domain, for short. My Domain URLs all belong to this same domain.

  2. Having a My Domain subdomain isn’t just about convenience and branding an org’s login experience. It's about having more control over your login process and simplifying authentication. In fact, Salesforce requires you to have a My Domain subdomain in place to: 

    * Work in multiple Salesforce orgs in the same browser

    * Set up single sign-on (SSO) with external identity vendors

    * Set up authentication providers, such as Google and Facebook, so that your users can log in to your Salesforce org with their social account credentials
    
    * Use Lightning components in Lightning component tabs, Lightning page, the Lightning App Builder, or standalone apps
  
  3. When you begin a hands-on challenge in Trailhead, the first thing that happens is that you create a Trailhead Playground. And that Playground is set up as a My Domain subdomain.

  4. All Playground subdomains start with a cute animal name and some random numbers to ensure uniqueness. The subdomain ends with -dev-ed, which means that the subdomain is a Salesforce Developer Edition org.

  5. You can have several Playgrounds and can manage them within Trailhead. To list your Playgrounds, from any hands-on challenge, click a Playground name. 

  6. To manage your Playgrounds, you click Manage my hands-on orgs. This ambitious Trailblazer has eight Playgrounds. Notice that among the list of Playgrounds is a Developer Edition org.

# Create a My Domain

  1. From Setup, enter My Domain in the Quick Find box, then select My Domain.

  2. Enter the name for your subdomain. Choose something fun that’s also unique. 

  3. Click Check Availability. Salesforce checks whether this domain name is already in use. 

  4. When you get the green light (3), click Register Domain (4).

  5. Sit back and watch for an email telling you that the process completed. Behind the scenes, Salesforce prepares your subdomain and updates its domain name registries. Don’t worry if the process takes a few minutes. Be assured—your personal empire is on its way.

# Test and Deploy Your Subdomain

  1. Look for an email with a subject like, “Salesforce domain ready for testing.” Now let’s finish setting up your subdomain and rolling it out to your users.

  2. From the email you receive, click the link to get back to the My Domain wizard. 

  3. The link takes you to your Salesforce org. Notice the URL in the browser address bar shows your new subdomain name

  4. Right now, you’re the only one who has this URL. Before you roll out the subdomain to your users, you must check that the links in your org all lead to your subdomain URL. 

  5. Click Log in to continue setting up My Domain. Enter the username and password you used when you signed up for your org.

  6. Click Deploy to Users, and then click OK. 
  
    * Deploying a subdomain rolls out the new subdomain URL throughout your org. Now all your users see the subdomain URL in their browser address bar. 

  7. Click OK.

# After Deployment: Set My Domain Policies

  1. Did you notice that a new section appeared in your My Domain Setup page when you deployed your subdomain to all users? It’s called My Domain Settings and it gives you some more control over how your subdomain is used. Let’s take a look.

  2. If you’re not looking at the My Domain page, from Setup, enter My Domain in the Quick Find box, then select My Domain.

  3. Under My Domain Settings, click Edit. 

  4. Set login policies to control what happens when users try to log in from your old URL instead of from My Domain.

  5. Login Policies

    * Requires users to log in using your subdomain login page. It prevents users from attempting to log in with the generic https://login.salesforce.com/ URL.

  6. Redirect Policy - You can choose between three redirect policies. That is, if someone selects a bookmark such as https://na30.salesforce.com, we redirect them to the subdomain equivalent.

    * Redirect to the same page within the domain. Lets users continue to log in from your URL as well as your subdomain name. This option might be convenient, but it’s like nothing has changed. 

    * Redirected with a warning to the same page within the domain. Reminds users to use your subdomain name when logging in. Yet it still redirects them to your org. This option is good for a few days after you deploy your subdomain to help users transition to your new subdomain name.

    * Not redirected. Requires users to use your subdomain name when accessing your org. The training wheels are off. Expect that your users have transitioned to using the subdomain URL. If they haven’t, they get an error when they try to use your instance URL instead of the subdomain URL.

  7. Rename your My Domain
    Lets you rename your My Domain, for example, if your company’s name or branding changes.

# Customize and Deploy Your Login Page

  1. If you’re not looking at the My Domain page, from Setup, enter My Domain in the Quick Find box, then select My Domain.

  2. Under Authentication Configuration, click Edit. If you’re asked for it, grant permission to open Authentication Configuration in a new tab.

  3. For Logo File, upload an image of your company logo. The logo appears at the top left of the login page. Images can be .jpg, .gif, or .png files up to 100 KB. The maximum image size is 250-by-125 pixels wide.

  4. For Background Color, change the background color of your login page—either enter a hexadecimal color code or click the color picker Select a color from color picker.

  5. Update the content of the right side of the login page. 
  
    * The content is designed to resize to fill about half of the page. On your production org, you enter the URL of a file that’s hosted at a URL using SSL encryption and has the https:// prefix. For now, you can enter the URL for one of our stock pictures: https://mydomain-sample.herokuapp.com.