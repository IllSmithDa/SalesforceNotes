# Web service definition language (WSDL)

  1. Rest Basics

    * HTTP requests (GET, POST, PUT, DELETE) for bulk data

    * Restful api also refers to as Restful web service is based on representational state technology

    * Rest is usually referred over SOAP which is Simple object Access Protocol because Rest leverages less bandwidth making more suitable for internet usage. 

    * The Force.com Rest Api lets you integrate with Force.com apps using simple HTTP methods in either XML or JSON formats. 

    * Javascript object notation (JSON) is the most widely used data format for data interchange on the web. 

    * The data interchange can happen between 2 computer apps that are different geolocation but same h/w mc

    * Signature - what are the input values required and what output is given to you.

  2. SOAP 

    * THe soap api lets you integrate FORCE.com that can create, delete, update and retrieve records managed by SFDC, FORCE.com and DB.com 

    * includes standard objects like Accounts and Contacts as well as custom objects  

# with sharing in API classes 

  1. Basic Syntax

    * public with sharing class thundercats {

    }

    * without sharing is default which will execute classin system mode and won't provide any required security

    * with sharing will execute the class in user mode and provide the required security

    * The default sharing mode of an apex class is without sharing 

    * It allows you to access some records to which you do not originally have access to 