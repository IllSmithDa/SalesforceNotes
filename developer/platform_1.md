# Salesforce Platform 

  1. At Salesforce, we group our services by clouds. There’s Sales Cloud for CRM, Service Cloud for customer support, and a handful of other clouds that help companies support their business functions.

  2. And while each of these clouds serves a unique purpose, there’s one thing they all have in common: the power of the Salesforce platform.

  3. Like any platform, the Salesforce platform is a group of technologies that supports the development of other technologies on top of it.

  4. What makes it unique is that the platform supports not only all the Salesforce clouds, but it also supports custom functionality built by our customers and partners. 
    
    * This functionality ranges from simple page layouts to full-scale applications.

  5. Our core platform lets you develop custom data models and applications for desktop and mobile. And with the platform behind your development, you can build robust systems at a rapid pace.

  6. And then there’s the Heroku platform. Heroku gives developers the power to build highly scalable web apps and back-end services using Python, Ruby, Go, and more. It also provides database tools to sync seamlessly with data from Salesforce.

  7. And then there’s the host of Salesforce APIs. These let developers integrate and connect all their enterprise data, networks, and identity information.

  8. And then there’s the Mobile SDK. The Mobile SDK is a suite of technologies that lets you build native, HTML5, and hybrid apps that have the same reliability and security as the Salesforce app.

# Develop Without Code 

  1. When you look at data in Salesforce, you might think that you're looking at a user interface sitting on top of a run-of-the-mill relational database. But what you’re actually looking at is an abstraction of the database that’s driven by the platform’s metadata-aware architecture.

  2. In this abstraction, objects are our database tables. The fields on those objects are columns, and records are rows in the database. This analogy is true both for standard objects that come with Salesforce by default and custom objects that you build yourself.

  3. You can see metadata in action on record detail pages. On this detail page for an account record, you can see field names like Type, Account Number, and Website. These are the metadata that define the structure of your app. The values of each of these fields are our actual data, and in terms of our data model, they aren’t particularly relevant.

  4. In short, metadata forms the structure of your org. Whether you’re defining fields, business processes, or something more complex, metadata holds your configuration. The platform then renders your app’s metadata in the user interface along with its associated data.

    * This metadata-driven development model is one of the key differences between developing on the platform and developing outside of Salesforce. 

    *  Because the platform is metadata-aware, it can auto-generate a significant part of your user experience for you. Things like dialogs, record lists, detail views, and forms that you’d normally have to develop by yourself come for free.

    * You even get all the functionality to create, read, update, and delete (affectionately referred to as CRUD) custom object records in the database.

    * All this prebuilt functionality frees up your development time to work on more sophisticated custom features. Let’s take a look at how the metadata-driven development approach works in action.

  5. Schema Builder provides both coders and non-coders with an easy way to visualize and configure an app’s data model.

  6. The no-code and low-code development capabilities that the Salesforce platform provides means that you, as a developer, can move faster.

    * Salesforce offers a host of tools for point-and-click—or declarative—development. 
      - Most of these tools require little to no understanding of development principles: no code. Someone who thinks JSON is just missing a letter can construct a robust and complex data model.

    * If you’re the only person at your company developing on Salesforce, you can use the platform’s many declarative tools to build more in less time. 
    
    * If you’re working on a team with non-coders, you can leave the declarative development tasks to them while you double down on more code-intensive projects.

# Development with Code 

  1. Lightning Component Framework: A UI development framework similar to AngularJS or React.

  2. Apex: Salesforce’s proprietary programming language with Java-like syntax.

  3. Visualforce: A markup language that lets you create custom Salesforce pages with code that looks a lot like HTML, and optionally can use a powerful combination of Apex and JavaScript.

# Lightning Components

  1. The Lightning Component framework is a user interface development framework for desktop and mobile.

  2. As its name suggests, it’s a component-based approach to UI development. Using prebuilt and custom Lightning components, you can quickly develop sleek and consistent UIs for your apps.

  3. The Developer Console is the Salesforce integrated development environment (IDE) that you can use to develop, debug, and test code in your org.

  4.  It’s XML markup. It contains both Aura-specific and static HTML tags. 

  5. On the right side of the Developer Console, you also see some additional assets that are part of this component’s bundle. If you click on CONTROLLER, for example, you see some JavaScript. 
  
    * Lightning components use client-side JavaScript controllers and server-side Apex controllers. You can create and access those controllers, as well as other assets like component style sheets, from the bundle menu.

  6. Another great thing about Lightning components is that they’re mobile-ready. When you create apps for the Salesforce mobile app, you don’t have to worry about the way Lightning components display. You can just add them to the app and let the platform handle the rest.

# Apex 

  1. Property__c property = [SELECT Name, Price__c from Property__c WHERE Id=:propId];

    * This SQL-like phrase is actually SOQL (Salesforce Object Query Language). You can use SOQL to read records from the database in your code.

# Visualforce 

  1. Visualforce lets you create and customize pages in Salesforce as well as integrate with other standard web technologies, including HTML, CSS, and JavaScript.

  2. With Lightning components, you’re developing components that can be pieced together to create pages. With Visualforce, you’re developing entire pages at once.

  3. Another thing to notice is that Visualforce uses a similar convention to Lightning components with <apex:tagName>

  3. While Lightning components are newer and better for things like mobile development, there are several situations where it can make more sense to use Visualforce.
  
  4. Something that’s not shown in this class is the concept of Apex controllers. Before, we mentioned that Lightning components use JavaScript on the client-side and Apex on the server-side. 
  
  5. Visualforce pages can also use server-side Apex controllers, and most complex pages use quite a bit. As you continue to explore Visualforce, you’ll get very familiar with Apex controllers.

  6. You can also access and preview Visualforce pages by searching Visualforce Pages from the Quick Find bar in Setup.

# Find Lightning Component 

  1. Navigate to Setup by clicking the gear menu The Setup gear icon. and then clicking Setup.

  2. In the Quick Find bar, search for and click Lightning Components.
  
  3. Click Map and then click Developer Console.

# See Apex Code 

  1. From Setup, search Quick Find for Process Builder and open the Process Builder page.
  
  2. Click Price Change Push Notification.
    
  3. Under Immediate Actions, click Push Notification.
    
  4. Notice the value in the Apex Class field. From the gear menu up top, open the Developer Console.
  
  5. Click File | Open and use the Filter bar to find PushPriceChangeNotification. Double-click to open it in the Developer Console.

# Example Visual Force Page

  1. From App Launcher click HeatMap. This page shows all the listed properties and their locations in the city.
    
  2. From the gear menu , launch the Developer Console.
    
  3. Click File | Open | Pages.
    
  4. In the Filter bar, enter HeatMap and double-click it to open.

# Lightning Platform APis 

  1. As you move toward more programmatic development, you find a robust set of APIs that let you access your Salesforce data in a variety of ways. You already saw the API in action when we looked at Lightning components, Apex, and Visualforce.

  2. Property__c property = [SELECT Name, Price__c from Property__c WHERE Id=:propId]; 
    
    * Put simply, every object in your org has an API name that lets you access data for that object.

    * The __c denotes that the object is a custom object or field. This query is using the automatically created API access point for the Property object to retrieve information about properties in your org.

  3. Here’s a brief look at the APIs Salesforce provides and what they’re used for. 

    * SOAP API - Integrate your org’s data with other applications using standard SOAP protocols. 

    * REST API - Access objects in your org using standard REST protocols.

    * Metadata API - Manage customizations in your org and build tools that manage your metadata model.

    * Tooling API - Build custom development tools for platform applications.

    * Marketing Cloud API - Expose Marketing Cloud capabilities with the REST API and get comprehensive access to most email functionality with the SOAP API.

    * Bulk API - Load, delete, and perform asynchronous queries on large data sets.

    * Streaming API - Send and receive notifications securely and efficiently. Notifications can reflect data changes in your org, or custom events.

    * Chatter REST AP - Build UI for Chatter, Communities, Recommendations, Files, Topics, and more. 

    * Mobile SDK - While it’s technically a software development kit, it’s worth including here. Integrate Native or Hybrid mobile apps directly with Salesforce.

# Heroku 

  1. Heroku is all about interacting with the outside world. Heroku is a web development platform that lets you quickly build, deploy, and scale web apps.

  2. One of the great things about Heroku is that you have a lot of flexibility in how you write your app. If you’re a Java nerd, you can write your app in Java. If you’re a diehard Python fan, Heroku won’t get in your way. PHP your jam? PHP to your heart’s content!

  3. Heroku is built on Amazon Web Services (AWS), meaning a lot of infrastructure concerns you might have in standard web app development are taken care of for you. 

  4. On top of that, Heroku Connect unifies your Salesforce data with your Heroku Postgres data so you don’t have to manage moving information across platforms. No worrying about infrastructure or data storage means more time for you to focus on new development.

# IoT

  1. Depending on your industry, integrating Salesforce with the Internet of Things (IoT) may or may not be a necessity.

  2. owever, with smart devices on the rise, it’s not a bad idea to get familiar with developing with IoT in mind.

  3. What if real estate agents could make these preparations on-the-go from their Salesforce mobile app? By connecting smart devices with Salesforce, they can do exactly that. Using a combination of Visualforce or Lightning components, microservices hosted on Heroku, and the IoT interfaces from smart locks, lights, and thermostats, you can build IoT control right on the platform.

  4. Of course, IoT has many other applications. For any company with a connected hardware component, Salesforce’s IoT capabilities give you an easy way to collect, manage, and analyze data about devices. It also helps you do things like monitor the performance status of your customers’ devices and define business logic that supports customer engagemen

# Bots

  1. Chatbots are typically used in external customer service. But you can also build them right into your Salesforce org to help your employees navigate their data.

  2. From the AppLauncher, select DreamHouse. At the bottom of the page, there’s a DreamBot item. Click it, type 3 bedrooms in Boston, and press enter.

# Summary 

  1. Another thing you should take away from this module is that the platform is extremely dynamic. Between the accelerated development capabilities and the many technologies that integrate with Salesforce, you have tons of options for building out your Salesforce org.

  2. Throughout Trailhead, you’ll learn much more about the technology we’ve discussed here. Additionally, the Salesforce Developers portal is your best resource for all things related to developing on the Salesforce platform. It’s full of developer guides, blog posts, forums, and more information to help you as you get started. 

# Multitenancy 

  1. Number one value for Salesforce platform is trust

  2. multitenancy: every customer shares the same infrastructure and runs on the same platform. 
  
    * But, like an apartment building, each unit is unique and accessible only to the owner. 

  3. Having all our customers under one roof allows us to share our investment in trust and innovation with everyone.

    * We can deliver top notch security features wanted by smaller companies, and the flexibility that enterprise companies crave.

# Metadata 

  1. Metadata is widely defined as “data about data”

    * We’re talking about our metadata-driven architecture that allows each customer to customize their own instance of Salesforce

  2. The custom tab, the custom fields, the automatic reminders, even any standard reports and Chatter they might wish to use—all of this is metadata. 

  3. It's the structure of your Salesforce instance, with all of your custom and standard functionality.

  4. Salesforce separates our customers’ customizations into a special metadata layer, so we can update and improve our platform in the background without touching any of their data or customizations.

    * e.g That means that we can give Edgar’s Mission (and all of our other customers) upgrades three times per year with great new features without altering their farm data or breaking their custom “Animals” tab.
  
    * Because their metadata exists in its own layer, Edgar’s mission can customize to their heart’s content. 

    * And instead of devoting a resource to developing an infrastructure and keeping things up and running, they can staff up where it counts for their most important customers... in the paddock.

  5. Fueled by the easy accessibility of the metadata layer, the cloud, and Software as a Service (SaaS), this is, ultimately, the power of the platform.

# Components of Our Metadata-Driven Architecture 

  1. Point-and-Click Configuration for all

    * Configuration allows anyone to quickly and easily configure your applications with a point-and-click interface.

    *  This means you don’t have to rely on a developer to create the ideal apps for whatever business goals you’ve set.

    * It could be as simple as renaming accounts to coincide with your industry, just like Edgar’s Mission did with their “Animals” tab. 80% of all our user customizations are made through these basic point-and-click configurations.

    * IT sees the value in point-and-click too. Opening up simple app development to users gives developers more time to work on custom code for more advanced things like user interfaces and business logic. 

    * There’s no need for IT to build services like workflow, collaboration, dashboards, or mobile interfaces, or worry about managing its own infrastructure. 

    * Salesforce handles the scaling, performance, database configuration, servers, and storage.

  2. Custom Code for developers

    * Creating custom code is slightly more complicated than configuration. When a company decides it needs advanced functionality, they can have a developer write custom code to achieve it.

    * New features, functionality, and user interfaces help a business achieve exactly what it wants. And it’s entirely cloud-based, so your developer will only have to write it once to run it everywhere.

    * Another way to tailor your Salesforce experience is to connect your back-office applications with APIs.

      - API stands for Application Programming Interface, and it’s essentially a bridge between two pieces of software, allowing them to connect to each other and exchange information.

    * Since we made our metadata openly available through APIs, you can connect Salesforce to anything. That includes any of the thousands of our partner apps in the AppExchange.

    