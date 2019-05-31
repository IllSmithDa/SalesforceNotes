# Introduction to Static Resources

  1. Static resources allow you to upload content that you can reference in a Visualforce page. Resources can be archives (such as .zip and .jar files), images, stylesheets, JavaScript, and other files.

  2. Static resources are managed and distributed by Lightning Platform, which acts as a content distribution network (CDN) for the files. Caching and distribution are handled automatically.

  3. Static resources are referenced using the $Resource global variable, which can be used directly by Visualforce, or used as a parameter to functions such as URLFOR().

# Create and Upload a Simple Static 

  1. Download the current version of the jQuery JavaScript library. At this writing it’s jQuery 3.1.0.
If the link doesn’t work, or if you want to make sure you’re downloading the very latest version, go to http://jquery.com/download/ and download the latest version available there.

  2. In the editor, replace any markup with the following.

    * <apex:page>
          
          <!-- Add the static resource to page's <head> -->
          <apex:includeScript value="{! $Resource.jQuery }"/>
          
          <!-- A short bit of jQuery to test it's there -->
          <script type="text/javascript">
              jQuery.noConflict();
              jQuery(document).ready(function() {
                  jQuery("#message").html("Hello from jQuery!");
              });
          </script>
          
          <!-- Where the jQuery message will appear -->
          <h1 id="message"></h1>
          
      </apex:page>
  
  3. Click Preview to open a preview of your page that you can look at while you make changes. A new window should open, showing the standard Salesforce page header and sidebar elements, and a short message from jQuery.
  
    * This page doesn’t do much except illustrate how to include a JavaScript resource on your Visualforce page. The key is the use of the $Resource global variable. Use dot notation to combine it with the name of the resource in an <apex:includeScript> (for JavaScript files), <apex:stylesheet> (for CSS stylesheets), or <apex:image> (for graphics files) tag to add it to your pag

# Create and Upload a Zipped Static Resource

  1. When your static assets are a set of related items—for example, a set of application icons, or a complex JavaScript library—it’s best to create a zipped static resource. Create a zip file containing all of the elements you want to group together, and upload only the one zip file to Lightning Platform.

  2. Download the current version of the jQuery Mobile JavaScript library, in the ZIP format. At this writing it’s jQuery Mobile 1.4.5.
  If the link doesn’t work, or if you want to make sure you’re downloading the very latest version, go to http://jquerymobile.com/download/ and download the  latest version of the ZIP file available there.

