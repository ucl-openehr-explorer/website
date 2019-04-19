Glossary
========

openEHR
-------
Open source standard for storing and handling EHRs. `Official Website <https://www.openehr.org/>`_, `What is openEHR? <https://www.openehr.org/about/what_is_openehr>`_

EHR
---
Electronic Health Record:
    A collection of digitalised information about a patient(s).

CDR
---
Clinical Data Repository:
    A place where patients' EHRs are stored.

AQL
---
Archetype Query Language:
    The query language used on CDRs.

Archetype
---------
Little chunks of medical record.
    e.g. Medication orders, blood tests, etc.

Templates
---------
Templates are a defined data set created by multiple archetypes as components. They are built independantly of CDRs.

CORS
----
Cross-Platform Resource Sharing:
    a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served.

Federate
--------
Combine data from multiple sources, in this context multiple CDRs.
This is useful for the following requests(situations):

* "I don't care what CDR this data lives in, I just want a list of blood pressures for this patient regardless of whether they were taken at the GP or hospital."
* "Give me every patient with hypothyroidism across 12 London hospitals."

Zoom
----
An online communications and conferencing software that uses cloud computing. Provides services such as video conferencing, online chats, mobile contributions, etc.
