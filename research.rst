Research
========

openEHR
-------

openEHR is a technology for e-health, consisting of open specifications, clinical models and software that can be used to 
create standards, and build information and interoperability solutions for healthcare.[1]

Much of our research centred around understanding the openEHR ecosystem. Our client was an invaluable resource in this, 
taking the time to explain its concepts and elements to us. We also did some research of our own, from information 
avaiable online[1][2].

Existing solutions
------------------

Our client gave us access to a similar proprietary tool to the one we'd be building, Think!EHR Explorer.

.. image:: images/thinkehr_explorer.png

We tested the tool to get a feel what what potential users would be used to. Naturally, our aim was to go beyond what this tool 
did, and make a tool capable of querying multiple CDRs concurrently.

Technologies
------------

Languages
~~~~~~~~~

We settled upon JavaScript since all members of our team had used it in the past or were familiar with it, and our client 
had recommended doing it this way.

We chose against making a browser-based webapp because CORS (Cross-Origin Resource Sharing) could have posed a problem with some 
CDRs not being configured correctly to be queried from a browser. 
So instead we decided to use Electron[3] to create a desktop application where this would not be a problem. 
Creating a desktop application also means that we can create executable files which can be easily distributed to users. 

We have also decided to incorporate elements of modern JavaScript such as ES6 modules, 
Promises and the Fetch API, to build our project in a forward-thinking way and produce a future-proof solution.
While some of these features aren't implemented in Node.js today, it is very likely that they will be in the very near future[4].
However for now, we can convert code written using them into JavaScript which current versions of Node.js can run using tools 
like Babel[5].

Test Frameworks
~~~~~~~~~~~~~~~

While researching on modern, up-to-standard and effective ways of JavaScript unit testing, we found an article on the Internet
by Welldone Software[6] that had clearly laid out various information about testing on JavaScript. We therefore took the advices
found on the article and looked into using Jest for the openEHR Explorer.

Its documentation showed it to be a powerful testing framework, and when using it we found it very pleasant and straightforward.

For mocking HTTP requests and responses in our tests we found Nock[7]. 
Nock is particularly powerful because it allows one to run a real HTTP request in a test, save the response, and then 
use those saved values in tests going forward. This is especially useful given our need to test querying against a complex 
external API, where manually running the queries and copying the result over would be too tedious and error prone.

Documentation Generators
~~~~~~~~~~~~~~~~~~~~~~~~

JSDoc[8] is the standard for annotating JavaScript code with documentation, and we decided on using documentation.js[9] to
turn that into readable documentation given its ease of use with minimal configuration.

Summary of Final Decision
-------------------------

Electron will allow us to create a multi-platform application and allow us to focus on the development of the system by
removing the chance of CORS causing a problem. A desktop application means that the system can also be distributed easily with
executable files to the users.

We will be using a multitude of modern tools such as Nock, Jest, etc. to effectively test our code as much as possible.

JSDoc will provide clear annotations and documentation for any future programmers who wish to contribute to in the development of
the openEHR Explorer.

All of the above come together to reach our goal - creating a smooth, forward-minded system that is able to match the needs
of the users.

References
----------
- [1] https://www.openehr.org/about/what_is_openehr
- [2] https://specifications.openehr.org/

  - https://specifications.openehr.org/releases/QUERY/latest/AQL.html
  - https://openehr.github.io/specifications-ITS-REST/
  - https://www.ehrscape.com/api-explorer.html

- [3] https://electronjs.org/
- [4] https://medium.com/@giltayar/native-es-modules-in-nodejs-status-and-future-directions-part-i-ee5ea3001f71
- [5] https://hackernoon.com/7-different-ways-to-use-es-modules-today-fc552254ebf4
- [6] Vitali Zaidman, "An Overview of JavaScript Testing in 2018", 9th February 2018 [Online] https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2018-f68950900bc3
- [7] https://github.com/nock/nock#readme
- [8] http://usejsdoc.org/
- [9] https://documentation.js.org/