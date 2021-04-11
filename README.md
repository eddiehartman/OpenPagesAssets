#POC_MVP
Integration framework for IBM Global GTS SR&RM OpenPages.

There are currently three solutions built on this framework:

1. Risk Export (`Risk_2_csv` AL)
2. ePolicy Migration (`Migrate_ePolicy_Service` AL)
3. OpenPages Template Migration (`Migrate_opPolicy_Template` AL)

All the support files are placed into a single *solution folder* named `POC_MVP` in the SDI Solution Directory.

On OpenPages Servers SDI is installed as follows:

* /local/IBM/TDI/V7.2 - is the Installation Directory
* /local/IBM/TDI/soldir - is the Solution Directory

The keystore use for all SSL communications is located under the *Solution Directory*: `serverapi/testadmin.jks`.

##`Migrate_ePolicy_Service`
This AL is kept alive by the `Migrate ePolicy Service` Scheduler in SDI. It provides a REST service that supports the following endpoints:

####GET /
A GET call to the root folder (no path) returns a JSON payload indicating that the service is working and which version it is. For example, this commandline call run locally:

`curl http://localhost:8042`

Will return a message like the following:

`{"status": "Migrate ePolicy Service is running", "version": "20201214 1131"}`

>**NOTE** The port number used by the service is determined by the `POC_MVP.property` setting `service.port`.

####POST /validate
This is the call made by the UI that lets you load an Excel spreadsheet with the list of Accounts to validate.

####POST /migrate
This is where the UI with the `migrate` button makes the call to migrate a successfully validated Request.





