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

Essential Features
------------------

* Upload a template to multiple CDRs
* List templates from multiple CDRs
* Register CDR environment variables

  - Possibly import postman environment files

* Support different CDR authentication requirements

  - Ethercis requires session tokens
  - Marand ThinkEHR supports Basic authentication

* Execute AQL on multiple CDRs and display the result
* Federate the result of AQL statement from multiple CDRs
* Check consistency of result of AQL statement from multiple CDRs
* Commit composition to multiple CDRs

Possible Features in the Future
-------------------------------

* Visualise templates and archetypes

  - Show what the constraints are on data

* Generate AQL from interacting with template visualisation
