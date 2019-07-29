# Integrations

  1. Two systems able to communicate with each other programmatically

  2. Indound is the on coming system or integration that we recieve and process

  3. Outbound sending sending out an integration for systems to recieve, and process

  4. Request goes out to system B and response is sent back to system A when system B is done processing request and ready to send out the response which is the second request. It will send a immediate response to validate the requests even if the process will take longer.

    * Timeout in Salesforce is 10 seconds which is the time a system has to generate and send a response before thread dies.

  5. Having logs at every step of the integrations is very important

  6. Salesforce recommends only 3 different systems including Salefsroce for integrations. 

  7. Having middleware with its one single system can handle multiple systems and keeps the interaction to 3 systems max even if there are over 3 system at work in total. 

    * middleware orchestrates all the system interactions 

  8. Requests are made from one system to another and the other system will eventually send a request back the original system once the process made by the other system is complete

# Bulk API 

  1. Rest Api only (no Soap)

    * HTTP requests (GET, POST, PUT, DELETE) for bulk data

    * Restful api also refers to as Restful web service is based on representational state technology

    * Rest is usually referred over SOAP which is Simple object Access Protocol because Rest leverages less bandwidth making more suitable for internet usage. 

    * The Force.com Rest Api lets you integrate with Force.com apps using simple HTTP methods in either XML or JSON formats. 

    * Javascript object notation (JSON) is the most widely used data format for data interchange on the web. 

    * The data interchange can happen between 2 computer apps that are different geolocation



  2. Good for loading, deleting larget sets of data and be used for soql queries

  3. Utilizes standard dml statements like delete, update, insert, upsert etc 

  4. It handles the large data set asyncronously allowing it to be processed in the background allowing for another process to run rather than waiting for a dml operation to complete