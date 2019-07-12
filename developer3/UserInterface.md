# Salesforce UI

  1. Salesforce Classic 

    * Page centric web application model 

    * Great for basic functionality but challenging to deliver new ones

  2. Javascript Client side 

    * App centric model where javascript is used to create, modify, transform and animate the user interface rather than completely replacing the page 

# Visualforce basics

  1. Workflow 
   
    * User requests a page

    * The server executes the page’s underlying code and sends the resulting HTML to the browser

    * The browser displays the HTML

    * When the user interacts with the page, return to step one

  2. Pros

    * Easy to use and model, easy to implement for greater productivity, naturally splits application into smaller manageable pages and has a built in metadata integration

  3. Caveats 

    * Limited interactivity and high latency which degrades mobile performance

# Visual force and React/Angular

  1. Workflow 

    * The user requests "empty" Visualforce page containing a page skeleton and Javascript includes

    * The page is returned to the browser

    * The browser loads the Javascript application

    * The Javascript application generates the UI

    * When user interacts with the application, the Javascript modifies  the user interface as needed

  2. Pros 

    * Enables highly interactive and immersive user experiences

  3. Caveats 

    * Complex

    * No built in meta data integration

    * Lack of an integrated developer experience.

# Lightning Components

  1. Workflow

    * The user requests an application or a component

    * The application or component bundle is returned to the client

    * The browser loads the bundle

    * The Javascript application generates the UI

    * When the user interacts with the page, the Javascript application modifies the user interface as needed(return to previous step)

  2. Pros 

    * Enables highly interactive and immersive user experiences 
 
    * Aligns with Salesforce user interface strategy

    * Built on metadata from the foundation, accelerating development

# Page vs Bundle
  
  1. Visualforce pages (and Visualforce components, but let’s set those aside for now) are stored on Salesforce as a single entity, an ApexPage.

  2. 

