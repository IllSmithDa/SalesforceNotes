# Take a Look at Knowledge

  1. Lightning Knowledge isn’t just your average knowledge base.

    *  Sure, it stores information in one place so that agents and customers alike can access it (depending on permissions).

  2. Because Knowledge is integrated with Salesforce rules, permissions, and administration tools, she can manage everything in one place. 

# Installation 

  1. Enter the url for free trial https://www.salesforce.com/form/signup/freetrial-service.jsp?d=70130000lxERAAY

  2. A few minutes later, a trial version displays a list of tours you can use to explore Service Cloud feature
  
  3. Click Share the Knowledge.

  4. Step through the tour. 

  5. In the Knowledge pane, 

    * Search for articles — Type here to find articles in your knowledge base. For example, type password to find articles about resetting a user password. When you start typing in the search field, a menu pops up. Use it to view recent searches or create an advanced search with filters such as language or publication status.\

    * Create an article - If an answer isn’t in your knowledge base, create an article to add it.

    * Sort your search results - Click to sort your results alphabetically from A to Z or by publication date. Suggested articles are already sorted by relevance.

    * View details about each article - See the article’s title, summary, and properties. In this case, the article is titled How to Reset Your Account Password.

    * Work with the article - Click this menu to interact with the article. Depending on the article’s permissions, you can do a lot. You can edit, publish, archive, attach, detach, follow, or insert the article into an email.

# Gather the Information

  1. Here are some questions Maria asks when designing the knowledge base.

    * What kind of information will we publish? 

      - FAQs, procedures, product manuals, guidelines. Ursa Major has these types of information and more. They want to publish and present different types of information in different ways. 

      - Best practice - Create a record type for each different type of information. Record types determine how to structure each type of article and what information to share with different user profiles. Other important features, like workflow and page layouts, are also set on the record type. 

    * Do we have an existing knowledge base or documentation to import? 

      - Ursa Major is starting with Lightning Knowledge and Ada’s notes, so they don’t need to do import anything. 

      - Best Practice - Use the Knowledge import tool to bring articles in from a different Knowledge base. Use the Lightning Knowledge Migration tool to move existing Salesforce Classic Knowledge content into Lightning Knowledge. 

    * Are there fields on our cases we want to use to filter suggested articles? 

      - Product family, product region, type of issue. Ursa Major’s important fields include solar components and collections of components called groups. 

      - Best Practice - Define data category groups for each type of search filter or to determine which user profile sees the articles for each category or group. 

    * Do we need workflow or approval processes to manage article creation and publication? 

      - Some articles require legal approval because they contain sensitive information. Ursa Major’s solar panels have safety requirements, so procedures to install and service them must be carefully reviewed. 

      - Best Practice - Add an approval process to a record type to ensure that required reviewers approve that type of article before it's published. 

    * What type of audience are we sharing our information with? 

      - Different audiences are called channels. Set the channel on an article to determine which type of user can view the article. Once you define that, user can see the content in any Community they have access to. Ursa Major has a few different kinds of users, so Maria must figure out who should see what. 

      - Best Practice - Determine what information to make available to each audience. If necessary, restrict individual fields to keep sensitive information secure or restrict records with a specific category associated to specific user profiles using data categories. 

    * How do we track article feedback? 

      - Let users give articles a thumbs up or thumbs down

      - Best Practice - Create custom reports about article ratings. Review reports and articles regularly to keep your knowledge base accurate and up to date. 

    * How can we see which articles are effective? 

      - Monitor how often an article is attached to cases. At Ursa Major, the most referenced article describes how much money customers save when they install a solar hot water heater. 

      - Best Practice - See how many times an article is attached to a case that solves a customer issue. Articles often linked to cases are good candidates to share with customers or agents during training. If you translate your articles, these are good ones to start with. 

# Organize the Information 

  1. Here are some questions to ask when categorizing articles. 

  2. How should information be categorized?

    * Ursa Major groups information by teams, then categorizes it by product types. Other companies group information by geographic area, then categorize it by product. 

    * Best Practice - Data category groups contain data categories. The fewer groups, the better. When defining data category groups and data categories, make sure that classifications are clear to users. They must know which groups and categories to select when searching for existing articles or when creating new ones. 

  3. Does any information need to be restricted? 

    * Ursa Major has different products and support agents in different states. Information about products and sales only available in Arizona shouldn’t be visible to agents in New Mexico. 

    * Best Practice - Set data category visibility on profiles to control which user profile has access to the articles with that data category. 

  4. Does searchability need to be enhanced? 

    * Even in a vast knowledge base, agents and customers must find the articles they need. Ursa Major doesn’t have that problem yet, but Maria wants to avoid it. 

    * Best Practice - Identify synonyms for search terms, for example linking and attaching. Have search results highlight snippets of article text that match the search term. Show a specific article first when a certain search term is used. 

# Determine Who Does What

  1. Here are three common types of users and the permissions they require to do their jobs.

  2. Readers only

    * Relatively new to the company these agents aren’t authorized to create articles yet. They use existing articles to answer questions and attach articles to cases. These articles help them contribute much faster than if they had to solve all the issues themselves.

  3. Contributors

    * Advanced Knowledge users, such as Ada. They have a lot of product knowledge and understand the standards for articles. They create, edit, and publish articles. 

  4. Knowledge admin - Knowledge admins know when to retire or delete articles. 

# Count and Assign Licenses

  1. But Ada and Maria do more than read articles. They create them. What kind of license do they need for that? Ursa Major uses Service Essentials.

    *  Lightning Knowledge User licenses are included in Service Essentials, so Maria doesn’t need to purchase any. 

      - (Check with your Salesforce account executive to determine your licensing needs.) 

# Maria is ready to assign Knowledge User licenses to herself and Ada. Then they can start getting the knowledge base out of the planning stage and into the development stage. Here’s what Maria does.

  1. From the Setup menu (Setup icon), choose Setup.

  2. In the Quick Find box, enter Users.

  3. Click Users. 

  4. Click the username. Maria clicks Jimenez, Maria. 

  5. Click Edit and select Knowledge User. 

  6. Click Save. 

# Enable Knowledge

  1. From the Setup menu (Setup icon), choose Setup.

  2. In the Quick Find box, enter Knowledge Settings and select Knowledge Settings. 

  3. Select Enable Lightning Knowledge. 

  4. From the Setup menu (Setup icon), choose Service Setup.

  5. To open the Lightning Knowledge Setup flow, click the Knowledge Setup tile. 

  6. Click Start. 

  7. In the search box, enter a Lightning Knowledge Author. Maria enters Ada. 

  8. Select the author and click Next. Maria selects Ada Balewa. 

  9. Enter your data group and data categories and click Next. Maria enters Home Solar Installation as the data group and Solar Hot Water Heater Installation as the data category. 

  10. Click Finish. 

# Create Articles 

  1. From the main menu in the Service console, select Knowledge. 

  2. Click New. 

  3. Choose the record type for the article. Ada chooses FAQ. 

  4. Click Next. 

  5. Enter the article title in the Title field. Ada enters How much will I save if I install a solar hot water heater?

  6. Click in the URL name field.

    * Knowledge generates a URL based on the article title. You can change it, but Ada opts not to.

  7. Choose a Validation Status. Ada chooses Work in Progress. 

  8. To show what the article is about, enter a summary. The summary appears in the search results. Ada enters Solar hot water heater savings calculations. Here’s Ada’s screen. 

  9. Click Save.

# Set up Question and Answer 

  1. In the Knowledge tab, click the article name. Ada clicks How much will I save if I install a solar hot water heater?

  2. Click Edit. 

  3. Next to Question, click Edit. 

  4. Enter the question. Ada enters: How much will I save if I install a solar hot water heater? 

  5. Next to Answer, click Edit. 

  6. Enter the answer. Ada enters: Here in the Southwest, we have ample solar energy year-round, except for the few days when it rains. That means your solar hot water heater is always working for you. How much you save depends on how much hot water your household uses. For some households, that's up to 85% of your bill, but the average is around 50%. 

  7. Click Save. 

  8. In the Knowledge tab, click the article. Ada clicks How much will I save if I install a solar hot water heater? 

  9. Click Publish. 

  10. Select when to publish the article. Ada selects Publish Now. 

  11. Click Publish. 
