# Managing Currencies 

  1. In Salesforce, you can specify which currencies your organization uses, and individual users can apply specific currencies to their settings based on where they do business.

  2. By default, Salesforce organizations use a single currency. Once you set the required currency locale in your company settings, all currency values on records display in that currency.

  3. As the admin for your organization, you set that “corporate currency,” which reflects the currency of your corporate headquarters. 

  4. You also maintain the list of active currencies and their conversion rates relative to the corporate currency. 

# Enable Multiple Currencies
 
  1. From Setup search for Company Information in the Quick Find, then select Company Information.

  2. Click Edit.

  3. Check Activate Multiple Currencies.

    * once a multicurrency setup is enabled, it can’t be disabled.

# Multiple Currencies allows you to 

  1. Activate additional currencies and optionally select a new corporate currency.

  2. Ensure users have correct personal currencies.

  3. Make sure users use the correct currency when creating records.

# Activate Currencies - you can specify which currencies are supported by activating or deactivating

  1. From Setup, enter Company Information and click Company Information

  2. Click the Currency Setup button. The Active and Inactive Currencies will be listed out. 

  3. In Active Currencies, click New

  4. Select a Currency Type. Currencies are alphabetized using their ISO currency codes.

  5. Enter the conversion rate relative to your corporate currency. (More on conversion rates coming up.)

  6. Specify the number of decimal places to display for amounts in this currency.

  7. Click Save 

  8. To activate a currency from the list of inactive currencies, click Activate next to the currency. To deactivate one, click Deactivate and then OK. (Note: You can’t deactivate the corporate currency.)

    * Deactivating a currency does not alter amounts in items that use that currency, but your users are no longer able to enter new amounts using the inactive currency. And deactivating a currency that’s set as a user’s personal currency automatically resets the user’s currency to the corporate currency.

# Setting Corporate Currency 

  1. From Setup, enter Company Information and click Company Information.

  2. In the Active Currencies list, click Change Corporate. 

  3. Select your new corporate currency from the dropdown. Only currencies that have been added and are active are available.

  4. Click Save.

# Update Conversion Rates 

  1. Ensure all the secret agents in your global organization use up-to-date currency values for deals by editing conversion rates. 

  2. This lets you manage the static exchange rates between your active and inactive currencies and the corporate currency.

  3. Here are the steps for editing rates:

    * From Setup, enter Company Information and click Company Information.

    * In the Active Currencies or Inactive Currencies list, click Edit Rates.

    * Enter the conversion rate between each currency and your corporate currency.

    * Click Save 

# Advanced Currency Management 

  1. While standard conversion rate control is straightforward, it impacts current and closed deals. 

  2. For accurate historical record keeping, it’s best to avoid impacting the value of completed business. Advanced Currency Management for currency fields on opportunities and opportunity products lets you manage exchange rate start dates.

  3. Once you’re set up for multicurrency, there are few simple steps needed to enable advanced currency management:

    * From Setup, enter Company Information and click Company Information.

    * Under Advanced Currency Management is not enabled, click Enable.
    
    * When prompted, select Yes, I want to enable Advanced Currency Management and click Enable. 

    * If you receive a pop-up message that reads: Navigate to this page? Click the Open button.

  4. Once multicurrency is enabled, currencies are activated, and conversion rates are edited, instruct your users at Mom & Pop’s to add personal currencies to their profiles.

    * Reminder that this is located in the Personal Settings:

      - Click your profile image at the top of the page and click Settings.

      - Enter Language in the Quick Find, then select Language & Time Zone.

      - Update the Currency field, and click Save.

