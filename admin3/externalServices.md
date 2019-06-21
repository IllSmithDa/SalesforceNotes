# Why external services?

  1. External Services is a feature within Salesforce that leverages declarative tools to connect to an external endpoint, such as a credit service provider, and bring its logic into Salesforce. 

  2. Make your new Salesforce org users automatic collaborators for external, org-related applications.

    * Maybe you want users to have access to a payroll information app so that they can look up their own timesheet and pay data. 

  3. Connect to a credit service that determines if credit is extended to an account in your org

    * You can register your external service and create a flow that includes inputs like order amount and credit terms. When the flow runs, it updates the credit terms for the order associated with the account.

  4. With External Services, you use declarative tools to import Swagger or Interagent-based API definitions right into Salesforce using a schema. Once you import the definitions, you can create a flow based on the Apex classes generated from your External Services registration...

# What’s a Schema Good For?

  1. Let’s start with the schema specification—the REST-based API that comes from an external service provider, such as a bank. We mentioned in the previous unit that you can think of the specification as a contract: It contains what types of inputs and outputs you can include in the calls, or requests, that your org makes to the external service. 

  2. On the other hand, the schema definition is human-readable, structured data. 

  3. Although a schema is human-readable, it also requires a logical structure that allows External Services to consume it. If a schema isn’t structured correctly, the external service returns error and exception messages

  4. When creating a schema, we must ensure that:

    * Schemas include up to 100,000 characters but no more.

    * Reserved names are not used.

    * Only supported Methods are included.

    * Properties include values.

    * Parameters have names.

    * Response code output doesn’t contain complex objects.

# Pre requisites: Named Credentials and Endpoint Access

  1. A named credential provided by the external service provider specifies the URL of a callout endpoint and its required authentication parameters.

  2. To do so: 

    * From Setup, enter Named Credentials in the Quick Find box, then select Named Credentials.

    * Click New Named Credential.

    * For Label, use Bank.

    * For URL, use https://th-external-services.herokuapp.com.

    * Leave other fields as they are and click Save.

# Registering a External Service 

  1. A named credential provided by the external service provider specifies the URL of a callout endpoint and its required authentication parameters.

  2. From Setup, enter Named Credentials in the Quick Find box, then select Named Credentials.
  
  3. Click New Named Credential.

  4. For Label, use Bank.

  5. For URL, use https://th-external-services.herokuapp.com.

  6. Leave other fields as they are and click Save.

  7. One other item of easy (but important!) housekeeping we need to take care of is to authorize the endpoint access. This is a quick process, but ensures that any callouts made from your org are approved and aren’t blocked.

  8. From Setup, enter Remote Site Settings in the Quick Find box, then select Remote Site Settings.

  9. Click New Remote Site.

  10. For Remote Site Name, use BankService (no space).

  11. Enter the URL https://th-external-services.herokuapp.com.

  12. Click Save to finish.

  13. Use the Wizard to Register Your External Service

    * From Setup, enter External Services in the Quick Find box, then select External Services.

    * Click Add an External Service.

    * For External Service Name, use BankService (no space).

    * For Select a Named Credential, select Bank.

    * Select Service Schema Complete JSON. From https://th-external-services.herokuapp.com/accounts/schema, copy in the schema information:

    * Click Next.

    * These actions are now available to you in Flow. 

      - The getAccount method retrieves account information.

      - The accountName parameter specifies the account.