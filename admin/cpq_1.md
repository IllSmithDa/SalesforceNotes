# Salesforce CPQ

  1. CPQ stands for configure, price, and quote.
  2. a native Salesforce app that helps you and your team close deals even faster.
  3. What products does the customer want to buy (configure)? How much do those products cost (price)? How can we give the customer details about the sale (quote)?
    * The C is for configure. You pick out what they’ll buy.
    * The P is for price. We add it up, easy as pie.
    * The Q is for quote: A nice PDF for you.
  4. Potential issues it addresses 
    * You and the other Infinity Solutions sales reps assemble quotes by hand and hope you have the right products and prices.
    * Your customers wait for a quote that may not be accurate when it finally arrives.
    * sales operations staff are always reminding you to update the opportunity and related systems, or fix the data when it’s wrong.

# Qoutes 

  1. Customers asking for qoute are generally asking for details for a potential purchase such as what they will be getting and price 
  2. Salesforce has two definitions for quote 
    *  document that contains information about the products and services your customer wants to buy
      - This might include contact information for you and your customer [1], a table of prices adding up to a grand total [2], and then a few places for dates and signatures [3].
    *  the electronic record of the quote data that’s represented in PDF format. This record includes details such as expiration date and grand total, along with information about each product on the quote, such as discount percent and net amount.
  3. Quotes are created from an existing Opportunity 
  4. However many quotes your opportunity contains, only one can be designated as primary, which means it has a special relationship with the opportunity. For example, the primary quote pushes the total quote amount into the Amount field on your opportunity. IF you later make a different quote primary, your opportunity automatically updates to reflect the new details.

# Bundle 
  1. group products in a set and enforce rules to ensure the set is complete and accurate. These sets are called bundles.
  2. You configure a bundle by choosing a product that’s associated with other products
  3. You can’t select invalid combinations of products when you configure a bundle.

# Product Grouping
  1. This list of products updates whenever new products are created or old products are retired. 
  2. Customizable filters help you find the products you’re looking for. Your Salesforce admin can group products into categories, such as Product Family, for even easier product selection.

# Guided Selling
  1. When you answer a series of questions [1], you get a list of suggested products that fit the bill.
  2. s begins when you start adding products to a quote. Your answers to the guide questions determine which products Salesforce CPQ suggests.

# Salesforce CPQ’s pricing calculator

  1. makes sure pricing is correct at all times and that your quotes don’t include manual calculation errors.
  2. When you add products to a quote, your quote automatically calculates the product prices. After that, any updates to your quote, such as changes in the quantity of the products, are reflected in the quote pricing.
  3. Subscription products and prices are automatically calculated as well, based on the subscription term you defined when you created the quote.
  4. Can apply Discount Schedules to handle tiered discounts for volume-based prices. 
    * Can also apply Discount Schedules to subscription products and automatically discount them based on the overall subscription terms you set for a quote.
    * can manually enter discounts line by line

# The standard Salesforce price book

  1.  price book gives you a list price, or standard price, for all Infinity Solutions products.
  2.  lets you use different pricing methods on a product-by-product basis. This means Infinity Solutions can account for the various ways you need to price your products.

# Quote PDF Generator 

  1. Use cases for Quote PDF Generator
    * Your customers want a summary and details about products and services that they’re considering.
    * Your customers want a breakdown of prices and totals of those items.
    * You want to provide accurate information to your customers, and wants to give them that information quickly in a standard format.
    * You want your customer to sign the quote electronically for a faster sales cycle.

  2. PDF Quote contains
    * list of products and services you’re quoting
    * prices and discounts on those items 
    * If prices and discounts also have totals and subtotals, they display in summary below the list of products and services.
    * Any important terms and conditions  
      - sometimes provide additional specification documents for review.
    * Appropriate signature blocks

  3. Dynamic Quotes 
    * You can hide specific columns in the line items table under certain conditions. Specific pages, sections, and even individual quote terms can appear dynamically as well.
    * You can add to the output by attaching supplemental materials, such as product specification sheets, to get a single, concatenated PDF.

  4. The document is stored on both your quote and your opportunity, so others who have internal access can open and view the quote when they need to.

  5. There are several ways to share the quote with your customer 
    * With the click of a button, email that PDF to your customer like you would any other email attachment
  
# Contracts and Renewals 

  1. Eventually the contract will end, and you’ll have an opportunity to create a quote for a renewal sale. Salesforce CPQ automates this entire process so creating contracts and quoting renewals is seamless for you and your sales team.
  2. Salesforce CPQ uses the standard Salesforce Contract object, which is associated with your customer’s account. 
  3. Salesforce CPQ can automatically create renewal opportunities and quotes for subscription products before your customer’s contract ends. 
  4. Your renewal opportunity contains all subscription items with quantities from the existing contract, and is automatically updated with additional subscription products if an amendment opportunity is marked as contracted.
  5. When you amend your customer’s contract, Salesforce CPQ creates a new quote and opportunity. On your new quote, the subscription products are priced according to how much time is left on the contract.
  6.  your renewal opportunity and quote populate any pipeline reports or forecasts maintained by Seamus on the sales operations side.

# Lead to Cash lifecycle

  1. Important to differentiate between a point tool that just helps your sales team generate more quotes and a solution that enables stronger customer relationships overall.
  2. Tradition CPQ mostly pull prices and products and generate quotes.
  3. Salesforce CPQ or modern CPQ 
    * Provide valuable tracking for campaign performance for marketing and accurate forecasting for sales
    * Provide better understanding what customers want and how you should speak to them.
    * Compile quote and deal data in one place so it becomes easier to deliver on contracts, which affects how your company recognizes revenue
    * See exactly what was sold, how much was sold, and when customers are due for renewals. This empowers them to better prioritize tasks and meet customer expectations (think making your service team happy).
    * improve customer loyalty
  
# Product and Price Rules 

  1. Product Rules
    * CPQ product rules help ensure sales reps are putting together the right products and bundles every single time
    * Whether products are compatible with one another is handled by Salesforce 
    * Four Type of Product Rules 
      - Validation Rules - confirm that a quote’s product combinations or quote line field values match predetermined conditions. 
      - Selection Rules - Set up rules to automatically add, remove, hide, enable, or disable options in a bundle. 
      - Filter Rules - Prefilter the products that are available to add to a bundle. 
      - Alert Rules - Guide and inform through messages during configuration or pricing. 
      - You can combine these product rules to improve the selling experience while increasing quote accuracy. 

  2. Price Rules 
    * Salesforce CPQ price rules help control quoting and optimize sales
    * Price rules automate price calculations and update quote line fields
      - Useful if your business contains products that change in response to the presence of other products on your quote.
    * Price rules inject a static value, field value, or summary variable into a quote or quote line field
      - You can also set up price rules to target either the configurator or the calculator on the quote line editor.
    * Price rules will also contain price conditions
      - e.g if you wanted to sell 2 ink cartridges with each printer, a price rule can ensure that if you increase the quantity of printers to 3, it will also increase the quantity of ink cartridges to 6. 
    * Multi-dimensional quoting (MDQ)
      - You can declaratively set up these line items with blocks of time (for example, days, months, years, and so on) with quantity and discounts separate from one another
      - You can control quantity and discounts over time without having to add new line items.
    * Overall goal to create much more accurate and faster quotes 

# Advanced Approvals 

  1. Useful for business with more involved workflows

  2. Key Features of Advanced Approvals
    * Smart Approvals - If an approver or approval group has already approved a quote and it gets rejected in a higher tier, the same approver or approval group isn't required to reapprove when the quote is resubmitted. Salesforce CPQ remembers the sequence.
    * Requiring Approvals - Reps get notified while building quotes when approvals are necessary. This is useful if certain discount levels must be approved before being completed.
    * Delegated Approvers - Used for assigning an approver to take over for someone while they are out of the office. 
    * Replacing Approvers - If a certain approver is no longer required to approve quotes, they can be replaced with clicks. This eliminates the need to delve into every single approval process the old approver was a part of to manually replace them. 

  3. Putting strong checks and balances in place with the right approval processes ensures a few things.
    * Reps are making appropriate commitments
    * There are no surprises down the line for Legal or Service teams.
    * Customers will always have the right level of expectation—expectation that you can always deliver on.
    
  4. AOM
    * For businesses that need to place multiple orders against a single quote, CPQ offers advanced order management (AOM).
    * With AOM, you can split orders to create multiple orders from a single quote, letting you send products to multiple locations or at different times
    * Key Features of AOM: 
      - Fulfill Orders Faster - Seamlessly generate orders from quotes to quickly get products and services delivered to your customers. 
      - Flexible for Evolving Customer Needs - Split quotes into multiple orders, manage future dated orders, and modify with point- and-click. 
      - 360-Degree View of the Customer - Quickly generate contracts with all contract term, pricing, asset, and subscription details. 
      - Connect to Back Office - Sync order details to ERP for order fulfillment. 
    * When it comes to your products and services, customers just want them to arrive on time and work. AOM helps you deliver on that promise. 
    * It also has the intrinsic benefit of helping your operations team recognize revenue properly with a clear view into what was delivered when. 
    * Service teams know what entitlements are in place for each customer at any given time, even if they get adjusted over time due to split orders. They are able to deliver against the right SLAs with minimal effort.

# Salesforce CPQ and time 
  1. In the Product and Price Rules  unit,you learned how our multi-dimensional quoting feature lets reps apply different quantities and discounts over time to ramp the deal
  2. In the Advanced Approvals and Advanced Order Management unit, you learned how Salesforce CPQ allows you to split orders off of a single quote so products and services are delivered across that same time period you set up.
  3. When renewals are in play, Salesforce CPQ automatically creates a renewal opportunity and quote so reps don't have to
    * Salesforce sends the team a reminder when the renewal is coming up. All they have to do is jump into the new opportunity, ensure the data is correct (data is carried over from the original opportunity and quote), and then execute. 
  4. This can very well be the most critical part of the customer relationship: understanding when and how to engage.
    * With an automated solution that delivers service on time and knows when contracts are up for renewal, all of a sudden reps can pinpoint these exact times in the customer journey for ideal engagement.
    * This insight is not just important for sales, but also for marketing, which may be launching new relevant products or add-ons, as well as for post-sales teams such as service. Service teams can now focus their energy on keeping their relationships warm with the right customers at the right time.
  5. Summary     
    * Product and pricing rules help product and pricing teams establish value and determine how to better package what you’re selling.
    * Advanced approvals enable sales, operations, and legal teams to work better together to ensure there are appropriate checks and balances.
    * Advanced order management helps post-sales teams (think services and partners) deliver as expected and on time.
    * With all this data centralized, and with how Salesforce CPQ treats time, these teams can keep a better eye on the customer and iterate for better execution and delivery.
    * What we really need to ask is, What can we do differently, and how can this tool help us? Or better yet, How do we better put our customer in the center of everything we do?