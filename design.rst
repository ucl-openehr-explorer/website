Design
===============

System Architecture
-------------------

We decided to separate out the project into two components to make developing them concurrently easier, to make testing easier 
in isolation, and finish the project with deliverables which are maximally useful to the openEHR ecosystem.

.. image:: images/prototype_system_architecture.png

Page Flow Diagram
-----------------

.. image:: images/page_flow_diagram.png

Design Patterns
---------------
Iterators
~~~~~~~~~
Iteration solves the problem of accessing and traversing objects without exposing the data structure and representation.

In openEHR Explorer, an iterator is used to traverse through the list of CDRs for actions such as displaying the list itself.

Asynchronous Methods
~~~~~~~~~~~~~~~~~~~~
Asynchronous methods solve the problems that could be caused by potentially long-running programs by allowing the next method
in the thread of execution to be invoked.

Promises allows for asynchronous programming to be employed in JavaScript and has therefore been extensively used for the
back-end of openEHR Explorer.

Test-Driven Development
~~~~~~~~~~~~~~~~~~~~~~~
Test-Driven Development (also commonly referred to as TDD) is an increasingly important aspect of programming. TDD ensures that
there is a very high coverage of testing of the code as each functionality has a corresponding test.

The team has followed the TDD methodology to ensure the back-end of the code has been thoroughly tested.

Factory
~~~~~~~
A factory is a that forms the basis of many software design patterns. A factory is an object that is used to create other objects - 
a factory method is a subroutine that returns an object of varying class.

Factories are mainly used in openEHR Explorer to create the CDR objects.

Balking
~~~~~~~
Balking refers to the execution of an action when an object is in a particular state, and the method will not return anything
when the object is in an inappropriate state. For example, if an object needed to access a method in a file but it has been zipped,
an exception would be thrown/the object would 'balk' at the request.

The team has taken a slightly different approach to balking - we were unhappy with the idea of 'no return' defined by balking, so
instead we have decided to ensure that no balking would happen. For example, to avoid AQL queries from being executed on unwanted
CDRs, openEHR Explorer will deselect all CDRs by default upon startup.

Proxy
~~~~~
A proxy is an object serving as an interface to another class. This provides a controlled access to a particular object, and could
additionally provide functionalities when accessing the object.

In openEHR Explorer, all CDRs that have been saved by the users are stored on a configuration file - constantly reading this file
could be very resource-intensive if the file increases in size significantly. Therefore, a proxy has been used to provide access
to the stored values without having to load the configuration file over and over again.

CDR Query Library
-----------------

`Initial prototype source code <https://github.com/ucl-openehr-explorer/openehr-cdr-query/tree/eba929b8cc92a45b6cded642a9457be24b78d95a>`_.

To handle retrieving data from CDRs, federating it, and committing new data to CDRs. In this initial prototype all that the 
library is able to do is send an AQL query to one or multiple CDRs, and concatenate their results.

However it's been built with modern development practices, which makes extending this functionality incredibly simple:

- We followed the test-driven development methodology, so the code is thoroughly tested:

.. image:: images/prototype_travis.png
   :target: https://travis-ci.org/ucl-openehr-explorer/openehr-cdr-query/builds/478416742?utm_source=github_status&utm_medium=notification

- We used JSDoc and documentation.js to generate extensive API documentation for the code:

.. image:: images/prototype_docs.png
   :target: https://github.com/ucl-openehr-explorer/openehr-cdr-query/tree/eba929b8cc92a45b6cded642a9457be24b78d95a#api

- We used the latest and greatest additions to JavaScript (ES6 modules, Promises, the Fetch API, among others), utilising Babel to make them backwards compatible with older JavaScript engines and versions of Node.js

By building this library in isolation from the Electron app, we give developers in the openEHR ecosystem the option of 
incorporating this library into their own projects.

While in its prototype phase it only runs in Node.js, with only a little work it could be made to work in the browser too.

Electron App
------------
Data Storage
~~~~~~~~~~~~
We have decided to use JSON to store the credentials of the CDRS as it is human readable and is widely used as a configuration
file across the industry.

Initial Prototype
~~~~~~~~~~~~~~~~~

`Initial prototype source code <https://github.com/ucl-openehr-explorer/electron-app/tree/aee92465da20285038f4539700db745d0bb454dd>`_.

The Electron app utilises the CDR Query Library to provide a GUI which users can use to query CDRs.

.. image:: images/prototype_gui.png

In this initial prototype, users can add CDRs, send an AQL query to a subset of them, and get the raw data back.

Implementation of Key Functionalities in Deliverable Version
------------------------------------------------------------

- Login system for users with different lists of CDRs
    - Different users will have their own lists of CDRs they wish to query - openEHR Explorer can accommodate this problem.
- AQL querying to multiple CDRs
    - The existing solution only allows the user to query a single CDR - openEHR Explorer allows querying of multiple CDRs at once.
- Return results from multiple CDRs in one federated JSON tree
    - The client and users have expressed that they would like to see all the results combined into one.
- Creating a table from the JSON tree for greater readability
    - While JSON trees are human-readable, a table can be used with ease by users with little previous experience.
- Adding CDRs from multiple vendors with different authentication systems
    - Further strengthens the ability to query multiple CDRs at once.
- Removing saved CDRs from list
    - User can easily remove any unused CDRs or CDRs with incorrect credentials from the list, preventing cluttering.