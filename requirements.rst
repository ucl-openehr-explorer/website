Requirements
============

Background
----------
openEHR - pronounced 'open air' - is an open specification for storing patient data used by clinicans and developers working in clinical contexts. 
However clinical data are often messy and mixed up, and each clinical application had its own models, so moving data was very hard. 
Everyone was building their models over and over again which kept causing problems. A new standard api to send models to but abstract data away from the database layer was needed. 

Gathering Requirements
----------------------
We were able to gather the requirements from the users through direct semi-structured interviews with both our users and our client by using Zoom.

Personas
--------

The system will be used by developers who are working within the clinical field. We therefore created two personas -
an experienced developer who has been working in the clinical field for a long time, and a developer who has recently
transferred to the clinical field. They can be found in more detail in HCI.

Essential Features - Must Haves
-------------------------------
+-----------------------------------------------------------------+----------------+
|Requirements                                                     |Type            |
+=================================================================+================+
|Register CDR environment variables*                              |Functional      |
+-----------------------------------------------------------------+----------------+
|Support different CDR authentication requirements*               |Functional      |
+-----------------------------------------------------------------+----------------+
|Execute AQL on multiple CDRs and display the result              |Functional      |
+-----------------------------------------------------------------+----------------+
|Federate the result of AQL statement from multiple CDRs          |Functional      |
+-----------------------------------------------------------------+----------------+
|Check consistency of result of AQL statement from multiple CDRs  |Functional      |
+-----------------------------------------------------------------+----------------+
|Commit composition to multiple CDRs                              |Functional      |
+-----------------------------------------------------------------+----------------+
|Easy-to-use GUI for new users                                    |Non-Functional  |
+-----------------------------------------------------------------+----------------+
|System must run smoothly without any noticeable lag              |Non-Functional  |
+-----------------------------------------------------------------+----------------+


* Register CDR environment variables

  - Possibly import postman environment files

* Support different CDR authentication requirements

  - Ethercis requires session tokens
  - Marand ThinkEHR supports Basic authentication

Possible Features in the Future - Could Haves
---------------------------------------------

+-----------------------------------------------------------------+----------------+
|Requirements                                                     |Type            |
+=================================================================+================+
|Upload a template to multiple CDRs                               |Functional      |
+-----------------------------------------------------------------+----------------+
|List templates from multiple CDRs                                |Functional      |
+-----------------------------------------------------------------+----------------+
|Visualise tempaltes and archetypes - show data constraints       |Functional      |
+-----------------------------------------------------------------+----------------+
|Generate AQL from interacting with template visualisation        |Functional      |
+-----------------------------------------------------------------+----------------+
|Authentication to support multipler users                        |Non-Functional  |
+-----------------------------------------------------------------+----------------+
|Generation of AQL from interaction with templates                |Functional      |
+-----------------------------------------------------------------+----------------+
Use Cases
---------

+------------------+-------------------------------------------------------------------+
|Use Case          |Logging In (UC1)                                                   |
+------------------+-------------------------------------------------------------------+
|Description       |User enters login details and clicks login button                  |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |None                                                               |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User opens the app                                              |
|                  |                                                                   |
|                  |2. User enters his username                                        |
|                  |                                                                   |
|                  |3. Clicks button to go to main page and display CDRs               |
+------------------+-------------------------------------------------------------------+
|Post-condition    |None                                                               |
+------------------+-------------------------------------------------------------------+
|Alternative Flow  |None                                                               |
+------------------+-------------------------------------------------------------------+

+------------------+-------------------------------------------------------------------+
|Use Case          |Add CDR (UC2)                                                      |
+------------------+-------------------------------------------------------------------+
|Description       |User adds a new CDR from addition page                             |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |User has logged on                                                 |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User enters add CDR page                                        |
|                  |                                                                   |
|                  |2. User enters CDR details                                         |
|                  |                                                                   |
|                  |3. Clicks button to add the CDR                                    |
|                  |                                                                   |
|                  |4. CDR saved to the config file and a confirmation window pops up  |
|                  |                                                                   |
|                  |5. Change is reflected in the main page                            |
+------------------+-------------------------------------------------------------------+
|Post-condition    |None                                                               |
+------------------+-------------------------------------------------------------------+
|Alternative Flow  |None                                                               |
+------------------+-------------------------------------------------------------------+

+------------------+-------------------------------------------------------------------+
|Use Case          |Remove CDR (UC3)                                                   |
+------------------+-------------------------------------------------------------------+
|Description       |User removes a CDR from list by clicking the bin button            |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |User has logged on and one or more CDRs exist in the list          |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User clicks on bin button next to CDR in list                   |
|                  |                                                                   |
|                  |2. The CDR is removed from the configuration file                  |
|                  |                                                                   |
|                  |3. Change is reflected in the main page                            |
+------------------+-------------------------------------------------------------------+
|Post-condition    |None                                                               |
+------------------+-------------------------------------------------------------------+
|Alternative Flow  |None                                                               |
+------------------+-------------------------------------------------------------------+

+------------------+-------------------------------------------------------------------+
|Use Case          |Query AQL (UC4)                                                    |
+------------------+-------------------------------------------------------------------+
|Description       |User inputs an AQL query and clicks on the query button            |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |User has selected CDRs they wish to query from the list            |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User inputs AQL query into text box                             |
|                  |                                                                   |
|                  |2. User clicks on the query button                                 |
|                  |                                                                   |
|                  |3. System processes and interprets the query                       |
|                  |                                                                   |
|                  |4. Query result from the selected CDR(s) is returned as a JSON tree|
+------------------+-------------------------------------------------------------------+
|Post-condition    |None                                                               |
+------------------+-------------------------------------------------------------------+
|Alternative Flow  |Error: 400 Bad Request (i.e. Incorrect AQL query) (UC4.1)          |
+------------------+-------------------------------------------------------------------+
|Description       |AQL query was incorrect and system has failed to process the query |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |User has selected CDRs they wish the query from the list           |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User inputs AQL query into text box                             |
|                  |                                                                   |
|                  |2. User clicks on the query button                                 |
|                  |                                                                   |
|                  |3. System processes and interprets the query                       |
|                  |                                                                   |
|                  |4. System is unable to interpret the query as it is incorrect      |
|                  |                                                                   |
|                  |5. Error: 400 Bad Request is shown in the results box              |
+------------------+-------------------------------------------------------------------+

+------------------+-------------------------------------------------------------------+
|Use Case          |Create JSON Table (UC5)                                            |
+------------------+-------------------------------------------------------------------+
|Description       |User creates a table of results from the given JSON tree           |
+------------------+-------------------------------------------------------------------+
|Primary Actor     |User                                                               |
+------------------+-------------------------------------------------------------------+
|Secondary Actor   |System                                                             |
+------------------+-------------------------------------------------------------------+
|Pre-condition     |User and system has successfully completed a query                 |
+------------------+-------------------------------------------------------------------+
|Main flow         |1. User clicks on Create Table from JSON button                    |
|                  |                                                                   |
|                  |2. System creates a table from the JSON tree                       |
|                  |                                                                   |
|                  |3. The tree is displayed on a pop-up window                        |
+------------------+-------------------------------------------------------------------+
|Post-condition    |None                                                               |
+------------------+-------------------------------------------------------------------+
|Alternative Flow  |None                                                               |
+------------------+-------------------------------------------------------------------+