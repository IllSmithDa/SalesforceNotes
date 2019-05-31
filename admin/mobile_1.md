# Salesforce Mobile App

  1. The Salesforce app is an enterprise-class mobile app that provides your users with instant access to your company’s CRM data from a phone or tablet. 

  2. Salesforce Mobile Features

    * The mobile app is included with every Salesforce license or free. Procrastinating on your mobile rollout is basically like setting piles of money on fire.

    * The app is plug-and-play, which means users just download it from the App Store or Google Play and go. It works out of the box with no setup required. 

    * The app is cross platform, so it runs on Android and iOS operating systems out of the box

    * The app has offline capabilities .Your mobile users won’t be affected by capricious cellular signals, FAA regulations, subway commutes, or bunker-style buildings.

    * It isn’t just an app. It’s a platform. Because the app is powered by the Salesforce platform, it’s infinitely customizable. You can use point-and-click tools to make it your own.

  3. How is it possible that the Salesforce app works instantly, right out of the box? The secret is your metadata.

  4. Salesforce Work Environment

    * When you log into the Salesforce mobile app, you’re automatically connected to your production org.

    * You can also log into your sandbox, which is the best place to play around with the mobile settings and customizations

# Compact Layout in Mobile

  1. When you open a record in the Salesforce mobile app, you see highlights about that record in the header of the page. Compact layouts control which fields appear in the header. For each object, you can assign up to four fields to display in that area.

  2. Creating and customizing compact layouts for your objects isn’t required because system defaults are provided out of the box. However, we recommend using compact layouts to put important fields into record headers to help your mobile users get the information they need quickly.

# Create a Compact Layout 

  1. From the object management settings for the object, go to Compact Layouts and click New.

  2. In the Field Label field, enter name such as Mobile Contact Layout.

  3. Add the fields to the layout such as Name, Phone, Stage, Email.

  4. Sort the fields by selecting them and clicking Up or Down. Be sure to put the object’s Name field first to provide context for your users when they view a record.

  5. Click Save

# Assign the Compact Layout to Users

  1. Click Compact Layout Assignment in the Object setting in Compact Layouts

  2. Click Edit Assignment

  3. In the Primary Contact Layout dropdown list, select Mobile Contact Layout.

# Customize Navigation 
  
  1. Well, we need visual cues to find our way in apps, too. And that’s what the mobile navigation menu is: a signpost. Your users rely on it to get from place to place in the Salesforce mobile app as efficiently as possible.

  2. The items in the menu are grouped into sections. They include:

    * Menu Items: Any items you place above the Smart Search Items element when you customize the navigation menu.

    * Smart Search Items: Includes a set of the user’s recently accessed objects. When expanded, it shows all tabs to which the user has access. Although you can control where in the menu these recent items appear, each user’s list is specific to their own usage history.

    * Apps Section: Contains any items you place below the Smart Search Items element.

  3. One easy way to improve the mobile experience for your users is to fine-tune the navigation menu so they can get around faster. When you customize the navigation, you can add, remove, or reorder the items in the mobile menu.

  4. Keep in mind that the Recent section of the menu is dynamic. It changes based on what a user has recently accessed in the mobile app. So although you can move the Recent section to a different spot in the menu, you don’t have any control over the items that appear in it.

  5. You can’t set different menu configurations for different types of users.

  6. If you want to include Visualforce pages, Lightning Pages, or Lightning components in the mobile navigation menu, you have to create tabs for them.

  7. Before adding a Visualforce page to the Salesforce app, make sure the page is enabled for mobile. Thoroughly test your Visualforce pages in the Salesforce app because they don’t always work the same in the mobile app. See the resources section for more information.

  8. The first item in the Selected list becomes your users’ Salesforce app landing page.

# Customize the Navigation Menu 

  1. From Setup, enter Navigation in the Quick Find box, then select Salesforce Navigation.

  2. Rearrange the selected items so that the top five are in the following order: Events, Chatter, Tasks, Dashboards, and Smart Search Items. The order determines how the items display in the navigation menu.

  3. Now let’s remove a few items the brokers don’t need to see: Approvals and Paused Flow Interviews.

  4. Click Save 

# Mobile Publisher

  1. It’s a fully branded version of your Salesforce app or mobile Lightning Community implementation. Your app icon, your name, your colors, and—most important—your very own listing in Google Play and the Apple VPP App Store.

  2. You want your Salesforce mobile app to represent your company and reinforce your brand not the Salesforce brand.

  3. With Mobile Publisher, your company is now a full-blown mobile development agency, and you can put a custom branded app into the hands of every single employee, partner or customer.

  4.  Until now, if you wanted to release a branded app with the Salesforce Platform, you had to build one yourself using our Mobile SDK. The SDK is awesome, but it does require mobile expertise and costly development resources that many companies simply don’t have.

  5. we came up with a few use cases for productivity-boosting employee and partner apps.

    * 