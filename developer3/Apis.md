# Aplication Programming interface (API)

  1. Client is sending request and server is recieving request and sends back to the client a response 

# Advantages of Integration

  1. Increased mobility and location idenpendence. Less servers to move and maintain making it easier to 

  2. Abstraction - it hides all the complex logic and programming and it makes our code easier to maintain and reducing complexity as well as making the code more readable. 
  
  3. Overall increased productivity

  3. Different methods include GET, POST, PUT, DELETE, PATCH, HEAD

# When to use which API?

  1. REST API-Uses HTTP, jSON, HTML

  2. Typically web application made from REACT, Angular utilize REST Api

  3. REST is preferred over SOAP because it is more lightweight leveraging less making it suitable for internet and mobile requests 

    * also handles soql queries/CRUD/Limits/Meta data 

  4. The Force.com REST Api lets you integrate Force.com apps using simple HTML methods in either XMl or JSON notation, making it ideal for developing mobile apps. 

  5. SOAP API - uses WSDL and XML format only

    * It can retrieve, create, update and delete records managed by SFDC

    * ideal for server to server integrations and run synchronously only. 

    * It is more secure and much more difficult to hack compared to REST api and bulk api

    * Enterprise WSDL can only handle your one salesforce org

    * Parnter WSDL is loosley coupled and can handle multiple salesforce org

  6. Async allows another system to run a process while your system runs another process in the meantime. The result or response will be sent to in a callback function when it is finished. 

  7. Streaming APIs - based on the publish/subscribe model. Whenever there is a need for fequent polling. Changes are broadcasted over a period of time. Examples include field history tracking.

  8. Metadata APIs - they are data about data and ideal if changes are to the meta data. 
  
  9. Query in REST workbench /v45.0/query/?q=SELECT+Id+From+Account

  10. /jobs/ingest/ - we are placing a jobs in a queue. 