Licensed Materials – Property of IBM

© Copyright IBM Corp. 2013

US Government Users Restricted Rights – Use, duplication or disclosure restricted by GSA ADP Schedule Contract with IBM Corp.


0. Introduction

This sample illustrates using the Remote REST APIs to fulfill a use case for anonymous data entry.

- Allows anonymous users to enter in financial losses without logging in to the OpenPages system.
- It is not required to create the users in OpenPages security.
- Users will navigate to a company website or existing web portal infrastructure and fill out the form with details of the loss. 
- Upon submission, the loss may be created in OpenPages using the REST API.

Possible features that could be built on this sample:
- Validate the input data based on OpenPages metadata
- Submit the created loss to a workflow
- Autonaming, default field values, associate to parents, and attachments

Implementation:
External form is hosted on a separate server, outside of OpenPages GRC application servers.
Running in a servlet container (e.g., Apache Tomcat 6).
Web form and integration implemented with Java/JSP.
REST Client code implemented with Apache Wink REST client library.


I. Setup

The sample has been developed using Tomcat integrated with Eclipse. 

To install Tomcat 6.0 Server Runtime in Eclipse:
   1. In Eclipse, go to Window > Server > Runtime Environments
   2. Click Add...
   3. Choose Apache > Apache Tomcat v6.0
   4. Check 'Create new local server'.
   5. Specify a server name, or use the default.
   6. Click Download and Install and follow the steps to install the server runtime.
   7. Select an installation location.
   8. Click Finish.

To create a project in Eclipse:
   1. From the File menu, select Import.
   2. In the filter, type 'war' and select War File.
   3. Browse to samples/AnonLossEventFormREST/LossEventClient.war
   4. For Target runtime, choose the Tomcat v6.0 runtime you installed.
   5. Unckeck 'Add project to an EAR...' for EAR Membership
   6. Ensure you are using a Java 1.6 JRE.
   7. Manually copy the AnonLossEventFormREST/src directory to the LossEventClient project folder in your Eclipse workspace. Overwrite the src directory.
   8. Add the following JAR files to the projects LossEventClient/WebContent/WEB-INF/lib directory:
       * com.ibm.openpages.api.marshalling.jar - from GRC_API/lib
       * jsr311-api-1.1.1 - from GRC_API/lib
       * wink-1.2.1-incubating.jar (or wink-client-1.2.1-incubating.jar, wink-common-1.2.1-incubutating.jar)
       * commons-codec.jar - Apache commons
       * slf4j-api-1.6.1.jar
       * slf4j-simple-1.6.1.jar
       * com.ibm.openpages.api.jar
       * com.ibm.openpages.api.rest.jar
       * juno-5.0.0.31.jar
    9. Modify servlet init-parameters in web.xml to fit your local environment.

   Wink JAR files are Open Source and can be downloaded from http://wink.apache.org/downloads.html
   Commons Codec is Open Source and can be downloaded from http://commons.apache.org/proper/commons-codec/


II. Running the sample

   1. Right-click on the LossEventClient project in Eclipse, and select Run on Server.
   2. If you have not defined an existing server, select Manually define a new server.
   3. Choose Apache > Tomcat v6.0 Server.
   4. Select your server runtime environment.
   5. Select Always use this server when running this project.
   6. Click Finish.

   Open this URL in your browser:
   http://localhost:8080/LossEventClient/lossform
   
   Enter the Loss field values and click Submit when ready.
