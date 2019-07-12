# Apex REST Annotations

  1. Six new annotations have been added that enable you to expose an Apex class as a RESTful Web service

# @RestResource annotation

  1. The @RestResource annotation is used at the class level and enables you to expose an Apex class as a REST resource.

  2. The URL mapping is relative to https://instance.salesforce.com/services/apexrest/.

  3. A wildcard character (*) may be used.

  4. The URL mapping is case-sensitive. A URL mapping for my_url will only match a REST resource containing my_url and not My_Url.

  5. To use this annotation, your Apex class must be defined as global.

  6. The path must begin with a '/

  7. If an '*' appears, it must be preceded by '/' and followed by '/', unless the '*' is the last character, in which case it need not be followed by '/'

  8. If no exact match is found, find all the patterns with wildcards that match, and then select the longest (by string length) of those.

  9. If no wildcard match is found, an HTTP response status code 404 is returned.

  10. The URL for a namespaced classes contains the namespace. For example, if your class is in namespace abc and the class is mapped to your_url, then the API URL is modified as follows: https://instance.salesforce.com/services/apexrest/abc/your_url/. In the case of a URL collision, the namespaced class is always used.

# @HttpDelete Annotation

  1. The @HttpDelete annotation is used at the method level and enables you to expose an Apex method as a REST resource.

  2. This method is called when an HTTP DELETE request is sent, and deletes the specified resource.

  3. To use this annotation, your Apex method must be defined as global static.

# @HttpGet Annotation

  1. The @HttpGet annotation is used at the method level and enables you to expose an Apex method as a REST resource. 

  2. This method is called when an HTTP GET request is sent, and returns the specified resource.

  3. To use this annotation, your Apex method must be defined as global static.

  4. Methods annotated with @HttpGet are also called if the HTTP request uses the HEAD request method.

# @HttpPatch Annotation

  1. The @HttpPatch annotation is used at the method level and enables you to expose an Apex method as a REST resource. 

  2. This method is called when an HTTP PATCH request is sent, and updates the specified resource.

  3. To use this annotation, your Apex method must be defined as global static.

# @HttpPost Annotation

  1. The @HttpPost annotation is used at the method level and enables you to expose an Apex method as a REST resource.

  2. This method is called when an HTTP POST request is sent, and creates a new resource.

  3. To use this annotation, your Apex method must be defined as global static.

# @HttpPut Annotation

  1. The @HttpPut annotation is used at the method level and enables you to expose an Apex method as a REST resource. 

  2. This method is called when an HTTP PUT request is sent, and creates or updates the specified resource.

  3. To use this annotation, your Apex method must be defined as global static.

  