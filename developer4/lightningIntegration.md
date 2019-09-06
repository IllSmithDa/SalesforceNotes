#Integrations
 
  1. WHen using another services external to Salesforce, we make a callout to request for a resoure or web service

  2. ERP is product centric whatever is needed

  3. CRM is always revolves around the customer 

  4. When a external system makes a request back to Salesforce, we have to make a web service or resource that will be able to respond to the external request

    * We have REST or SOAP to make a response back the original requester

# Making Callout 

  1. We have to make a request to external service

  2. The external service provides client Id and client secret as well as a endpoint and user Id and password.

  3. Auth and Credentials

    * credential system on its own is not very secure as it is just a username and password

    * Auth 2.0 grants limited permission to a particular section of API providing increased secrutiy 

    * External systems like Google will use both for a more secure system even with single sign on implementation ( using Google to sign into a app)

    * Single sign on uses Auth as it only provides limited information enough to be able to sign up or sign into a web application

    * overall better security structure
 
  3. Go to Auth Providers and Named Credentials in Setup to get Auth working and credentials working respectively

    * Thanks to these credentials methods, you no longer have to set up this in code as you would in Node or Django

    * In code, you also have to do all of the exception handling by yourself in code but it is taken care for you in Salesforce so you can focus on actually using your integration

    * You can use code but Salesforce provided a non programming way to set up integration

# Json2Apex

  1. Every Json on its own cannot be read by Apex classes unless it has been parsed into Apex classes and properties

  2. Composed = true means if A triggers a event, B an C will be able to subscribe. False means only B will be able to subscribe or the direct child. 