Workbook_PartA

### **Q1. Describe the architecture of a typical API project, such as a Flask application.**


While building a typical API project, such as a Flask application, the software architecture hinges on several pivotal components to handle the serialization and management of data, as well as efficient API endpoint handling. The application will typically involve a central file from which the application is initialized and run, (customarily this will be titled 'run.py' in order to be recognised by Flask). In order to facilitate maintainability and collaboration between developers, the application should be separated into different directories and files. The main `app/` directory will contain an `__init__.py` file and a `config.py` file. This directory should contain subdirectories containing the ORM models, CLI controllers, schemas, API endpoints (routes) and utility functions.


_1. Mapping an ERM (Entity Relationship Model)_

Typically, it is customary for developers to organise the structure of the application using an Entity Relationship Model (ERMs), which serve as a blueprint for how data is stored, organised, and related within a system. ERMs provide the developer with a clear breakdown of the application structure by defining the central entities, their attributes and the relationships between them. By mapping these elements in a visual representation, it provides a clear reference point for the developer to refer back to in order to ultimately ensure data integrity, optimise query performance, and facilitate maintenance and scalability of the database system.

_2. Configuration Settings_

Configuration settings for different environments are managed in separate config files. This allows the application to easily switch between settings for development, testing, and production, ensuring that sensitive information like database credentials is handled securely and appropriately.


_3. Database Management_

- Object-Relational Mapping (SQLAlchemy)
   ORMs are used to map database tables to Python objects, allowing developers to interact with relational databases (e.g., SQLite, PostgreSQL, MySQL) using Python code instead of raw SQL. In the context of a flask application, SQLAlchemy is an SQL toolkit and ORM library used as an interface to manage database schema, query execution, and transactions. The ORM models will be sequestered into their own `models/` directory, and each model defined will represent a database table. The database is then configured in the `config.py` file, which is used to specify database URI and SQLAlchemy settings.

- Serialization/Deserialization (Marshmallow)
   The ORM models then require another library in order to serialise and deserialize the data provided. In order to convert complex data structures into a format that can be easily transmitted or stored, a typical APi project such as a Flask application will require the use of a library such as Marshmallow.


_4. Environment Variables_

Environment variables are managed using files like `.env` and `.flaskenv`, which store configuration data such as database URLs, secret keys, and other environment-specific settings; which are loaded into the application at runtime. As the `.env` file contains sensitive information, it is typically placed in a `.gitignore` file in order to avoid exposing sensitive information such as database credentials or API keys. A `.envsample` or `.envexample` file is used to indicate the contents of the `.env` file to fellow developers to provide guidance on configuring the application's environment variables without disclosing sensitive information (e.g. DATABASE_URL=, JWT_SECRET KEY=).


_5. Dependencies_

Dependencies required for the project are listed in `requirements.txt`. This file includes all the libraries and packages that need to be installed for the application to run properly. It ensures that the development environment is consistent and easily replicable.


_6. API Endpoints (Routes)_

API endpoints are defined in the route directory, with each route corresponding to a specific URL path and HTTP method (GET, POST PUT DELETE). Each path handles requests by interacting with the models and returning responses.



_7. Command Line Interface (CLI) Controllers_

Command Line Interface (CLI) controllers provide commands for administrative tasks such as creating, deleting or seeding database tables or running background jobs. These commands are defined in the CLI directory and can be executed from the terminal.



_8. Middleware and Request Handling_

Flask's request and response cycle processes incoming requests by passing them through middleware and directing them to their relevant endpoints (routes). Middlewear may include authentication, authorisation and error handling is employed for cross-cutting concerns.



_9. Testing and Debugging_


Unit Testing: For testing endpoints individually, models, and schemas, you can use either `unittest` or `pytest`. Please see Q5 for the end-to-end testing process for an API.
Debugging: During development, Flask’s built-in debugger (`app.run(debug=True`)) helps identify and resolve issues.



### **Q2. Identify a database commonly used in an API project (such as a Flask application) and discuss the pros and cons of this database.**


PostgreSQL is an advanced, open-source relational database management system (RDBMS) commonly used in an API project such as a Flask application. It supports SQL for relational queries and JSON for non-relational queries, creating a powerful and flexible data framework for a wide range of applications. As a fully ACID-compliant database, PostgreSQL not only ensures reliable transactions and data integrity, but also boasts advanced features; such as complex query capabilities, indexing, full-text search, and support for custom data types and functions.


**Pros:**


_1. ACID Compliance:_ PostgreSQL is fully ACID-compliant, ensuring data integrity, as well as reliable transactions. This is crucial for applications requiring consistent and accurate data.


_2. Advanced Features:_ PostgreSQL provides advance features like complex queries, foreign keys, triggers, views and stored procedures, in order to enable sophisticated data manipulation and the implementation of business logic directly within the database.


_3. Extensibility:_ PostgreSQL's is a highly extensible system, offering a myriad of customisable options to the user to meet their specific application needs. Users can define their own data types, index types, and functional languages. It is also a packaging tool for database add-ons, supporting languages like PL/pgSQL, PL/Python, Java, and even JavaScript; allowing developers to write and run functions in various languages within the database by exposing an interface for language integration. This interface enables seamless execution of functions regardless of their underlying language, thus simplifying complexity by providing an extensible language function. This capability allows larger companies to develop functional packages tailored to their specific business domains.


_4. Performance:_ PostgreSQL supports complex queries, foreign keys, triggers, views, and stored procedures, enabling sophisticated data manipulation and business logic directly within the database. Its powerful indexing and optimization techniques make it suitable for managing large datasets and high-concurrency environments efficiently. Additionally, it uses Multi-Version Concurrency Control (MVCC) to handle concurrent processing and maintain high transaction rates with minimal risk of deadlocks, as well as ensuring high availability and provides server failure recovery mechanisms (https://cloud.google.com/learn/postgresql-vs-sql#section-8).


_5. Open Source:_ PostgreSQL being open source is highly beneficial as it is cost-effective, reducing database management expenses since it is free to use. It enjoys strong community support, with a large and active developer base ensuring rapid bug fixes, regular updates, and abundant resources. The open-source nature allows for high flexibility and customization, enabling users to modify the source code to meet specific needs. Additionally, it offers transparency for inspecting code security and reliability, fosters innovation through global collaboration, and avoids vendor lock-in, providing freedom in choosing support and services.

**Cons:**


_1. Complexity:_ Due to its advanced features and extensive configuration options, PostgreSQL can be more complex to set up and maintain compared to simpler databases like SQLite.

_2. Resource Intensive:_ PostgreSQL can be more resource-intensive, requiring more memory and CPU than other databases, which might be a concern for smaller applications or those running on limited hardware.

_4. Learning Curve:_ The richness of features means there is a steeper learning curve for new users or developers who are not familiar with its capabilities and configuration options. It has also been noted that the initial installation may also be dififcult for beginners.
- Installation can be difficult for beginners (https://cloud.google.com/learn/postgresql-vs-sql).

_5. Scaling Write Operations:_ While PostgreSQL handles read operations very efficiently, scaling write operations across multiple servers can be challenging and may require additional tools and configurations (e.g., sharding, replication).

_6. Slower performance:_ As this database has a stronger focus on delivering compatibility, the speed of performance has been impacted when compared to other RDBMS like SQL Server and MySQL (https://cloud.google.com/learn/postgresql-vs-sql). It has also been noted that some SELECT queries may be slower than their counterparts. 



### _Q3. Discuss an implementation of an Agile project management methodology for an API project._

https://www.atlassian.com/agile/product-management

Agile Product Management hinges on consistently garnering user feedback and incorporating it into updates. This iterative approach involves a series of steps that integrate multiple feedback intervals to promote adaptability and ensure the delivery of the best possible version of the product. After deciding on the steps to be taken, the project is divided into several segments, commonly known as user stories, which are distributed among the team of developers.

__Define API Objectives & Roles:__ The purpose and vision of the API will be discussed in detail with the entire cross-functional team; including developers, QA engineers, product owners, UX/UI designers, and possibly stakeholders. Once the objectives and key features of the API project have been established, clear roles should be defined among members of the team; including Scrum Master, Product Owner, and Development Team members.

__Developing a Roadmap:__ Typically, an API project under APM will involve the construction of a product roadmap, outlining a timeline for how the product is intended to develop over time. This involves delineating large areas of functionality from which initiatives are composed (https://www.atlassian.com/agile/product-management). Roadmaps are designed to be flexible and are likely to change over the course of the project. Each initiative in the roadmap is broken down into a set of requirements, tailored throughout the process based on the team's collective understanding of the desired outcomes (https://www.atlassian.com/agile/product-management).

__Sprint Planning:__ After deciding on the steps to be taken, the API project will be divided into several segments, commonly known as user stories, which are distributed among the team of developers. From the broader initiatives, the work will be broken down into "Epics". The epics are larger bodies of work that will then be broken down further into "Stories". In this step, the stories will be assigned to the developers and can typically be completed in 1-2 week sprints until the entire epic is completed (https://www.atlassian.com/agile/product-management). The user stories should be ranked based on business value, complexity, and dependencies. At this step, the team will also devise story point estimations to provide the team and product owner with an achievable timeline. Scrum teams structure development into time-boxed sprints. At the beginning of each sprint, the team estimates the amount of work they can accomplish. A sprint burndown report subsequently monitors the progress of work throughout the sprint.

__Personal Planning & Execution:__ The developers will then work on their stories, while having daily stand-ups with the rest of the cross-functional to discuss any blockers, progress and next steps. This promotes expectation and goal alignment within the team and allows for early identification of issues. Before commencing their stories, the developers will independently map their own story tasks using  APM tools like Jira, Trello, or Asana to track tasks and progress. For a software team working on an API project, the overall workflow would be decided, likely mirroring something like this: To-Do (Work that has not yet been started), In Progress (work that is currently being developed), Code Review (work that is completed and awaiting review), Done (work that has been completed and reviewed). The sprint burndown report of the API project will be repeatedly referenced to track team progress.

__Metrics:__ Review of Metrics will remain ongoing during and after the API project execution. This will require collecting and analysing relevant data along the way. Work in progress (WIP) limits ensure that both the team and the business focus on delivering the most critical tasks. Tools such as burndown charts and control charts help the team forecast their delivery pace, while continuous flow diagrams help identify bottlenecks (https://www.atlassian.com/agile/product-management). Other APM tools that may be used to track metrics include sprint burndown chart, epic burndown charts, velocity charts, control charts, cumulative flow diagrams.A Gantt chart is also another APM tool that may prove useful to illustrate work completed over a period of time in relation to the time planned.

__Continuous Integration & Testing:__ During the development of this API project, the team must remain flexible to fluctuations. Continuous integration and continuous deployment pipelines (CI/CD Pipelines) will be implemented to automate testing and deployment processes. Similarly, unit, integration and performance texting for the API will be executed via automated tests: E.g. developers may use `unittest` or `pytest` to test the code in their stories. The team will ensure continuous improvement using APM tools such as resprospectives, Plan-Do-Check-Act (PDCA) Principle, Kanban method/metrics (https://www.atlassian.com/agile/product-management). Overall, this will require constant and efficient collaboration and communication between all members of the team.

__Review:__ At the conclusion of each sprint, a review of the finished work will be conducted with stakeholders and showcase new API functionalities; these are aptly named "Sprint Reviews". The sprint review will evaluate the sprint to determine successes, challenges, and opportunities for process enhancement. Retrospectives will be orchestrated at regular intervals for team reflection (https://www.atlassian.com/agile/product-management).


__Post Execution Monitoring:__ Feedback will then be collected from the early adopters or stakeholders and integrated into the product backlog. This API project will then be adapted backed on this feedback to continuously enhance the API. The aforementioned APM metrics tools will be continuously reviewed and considered during this process to improve the project.


__Documentation & Versioning:__ Throughout production, it will be crucial for all members of the team to maintain up-to-date documentation for the API. For software developers, this means regularly committing their code to Version Control Systems such as Git, Mercurial, or SVN to manage changes and releases.




### _Q4. Provide an overview and description of a standard source control process for an API project._

https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.


Implementing a source control process begins with selecting a suitable Version Control System (VCS) like Git, Mercurial, or SVN, enabling the team to track changes, collaborate efficiently, and manage code versions (https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.). The project repository is structured with main branches such as "master" or "main” for stable production code and "develop" for ongoing development. Developers create feature branches from "develop" to isolate their work on specific features or fixes, providing clarity and enabling efficient editing and debugging.

During development, developers regularly commit changes to their feature branches, accompanied by descriptive messages that clarify the purpose of each change. Once a feature or fix is complete, developers initiate a Pull Request (PR) from their feature branch to develop. This PR serves as a platform for code review and collaboration, where peers provide feedback and suggestions directly within the PR interface. Developers address feedback, make necessary adjustments, and ensure their code meets the team's standards and requirements (https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.).

After all discussions are resolved and the PR is approved, it is merged into the develop branch using GitHub’s merge functionality. This seamless integration process ensures that changes are smoothly incorporated into the main development branch. Throughout this workflow, GitHub’s features such as pull requests, code reviews, and branching strategies support effective collaboration, maintain code quality, and facilitate transparent project management.

Additionally, Continuous Integration (CI) tools like GitHub Actions automate builds and run tests with each commit, identifying integration issues early in the development cycle (https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.). Completed features undergo rigorous testing, including unit tests, integration tests, and API tests, to validate functionality and ensure performance standards are met. Release branches, created from develop, undergo further testing and validation in staging environments before merging into master or main for production release. Semantic versioning practices ensure clear tracking of API versions and compatibility across releases.

Documentation plays a critical role, with detailed specifications and usage guidelines maintained within the repository. Collaboration tools integrated with the VCS, such as issue trackers and project boards (like Git Projects), facilitate task management and progress tracking throughout the development lifecycle (https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.). This structured approach ensures API projects achieve enhanced code quality, accelerate delivery cycles, and foster improved collaboration among team members, ultimately supporting the reliable and scalable deployment of APIs in production environments.



### _Q5. Provide an overview and description of a standard testing process for an API project._


Testing of an API is crucial in ensuring a smooth execution in the transmission of data and processes. There are several types of software testing involved when building an API. Testing can be done both manually and via automated testing tools. The standard testing process involves testing the functionality, performance, security, integrity and usability of the application. Some of the most commonly encountered issues during API testing typically involve ensuring data accuracy, valid HTTP status codes, error codes, response times and security (https://caisy.io/blog/api-testing-for-developers). In order to optimise the testing outcomes, it is recommended to first devise a testing strategy plan before commencing.


**Validation & Contract Testing**

An API contract is a comprehensive human and machine readable document outlining the intended functionality of the API. The contract will serve as a definitive reference for the structure of each request and response, forming the foundation of service-level agreements (SLAs) between the developers and users of the API. API contract testing verifies that newly released features of the API adhere to this contract by validating the content and format of requests and responses.
Focus areas should include:

1. API definition validation
2. Industry standards validation
3. End-user schema validation
4. Governance validation

https://blog.postman.com/api-contract-testing-4-things-to-validate/?_gl=1*hb94is*_ga*MjM4NzcxNTM3LjE3MjAwODEwOTQ.*_ga_CX7P9K6W67*MTcyMDA4MTA5My4xLjAuMTcyMDA4MTA5Ny41Ni4wLjA.

Functional testing can also be carried out to ensure the API is behaving according to it's defined contract and meets expected functional requirements. Automated testing tools like Postman or Insomnia can ensure that the API endpoints perform as expected based on their specifications. These tools are designed to mimic real-world responses to their code in order to validate endpoints, check response formats, and ensure compliance with expected behaviours as defined in the API contract. They help validate API functions without delving into the implementation details of individual components (like unit testing) or the overall workflow (and end-to-end testing). Other automated testing tools such as cURL, SoapUI, Swagger or OpenAPI tools are commonly used for this purpose too.


**Unit Testing**

Unit tests are designed to sequester key components of the code and test them in isolation. The process consolidates the knowledge that a single endpoint will be able to return the intended result to a given request. For example, the developer may use a framework such as `pytest` or `unittest` to run tests on particular functions within the code to ensure it handles option parameters correctly.
https://www.postman.com/api-platform/api-testing/#:~:text=API%20unit%20testing%20is%20the,when%20sent%20an%20invalid%20request.


**End-to-End Testing**

In contrast to unit tests, end-to-end testing extends this verification to encompass entire user workflows, often spanning multiple endpoints and integrated APIs. This more comprehensive testing approach involves simulating real-world scenarios by sequencing requests and verifying the seamless operation of each component.
https://www.postman.com/api-platform/api-testing/#:~:text=API%20unit%20testing%20is%20the,when%20sent%20an%20invalid%20request.


**Load Testing**

API load testing allows developers to verify the reliability of their API under high traffic conditions. It entails employing specialised testing tools to mimic substantial request volumes, assessing how the API handles these loads in terms of response times and error rates. This crucial testing phase is commonly conducted in preparation for anticipated spikes in usage, such as prior to product launches; ensuring that the API performs optimally even under peak demand.

https://www.postman.com/api-platform/api-testing/#:~:text=API%20unit%20testing%20is%20the,when%20sent%20an%20invalid%20request.




### _Q6. Explain the three principles of information system security._


There are 3 overarching principles that dictate information system (IT) security. They are as follows:


1) __Confidentiality__

If successful in executing this principle, the information is only being accessed by individuals who are authorised to do so (https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). Furthermore, appropriate security measures must be implemented to ensure private or sensitive information remains inaccessible to the public (https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). Such measures involve implementing security measures such as encryption, access controls, and authentication mechanisms to protect private data from unauthorised access. For example, using strong passwords, two-factor authentication, and secure communication channels will help maintain confidentiality. By successfully executing this principle, organisations can prevent data breaches by malicious hackers and subsequently protect sensitive information from being exposed to unauthorised parties.

2) __Integrity__

This principle seeks to ensure the integrity and accuracy of the data and protects it against modifications by unauthorised individuals (https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). In the best case scenario, this will mean that unauthorised users will be blocked from making modifications to the data. At the very least, any changes made by unsanctioned users will not go undetected (https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). Measures such as checksums, digital signatures, and data validation are employed to ensure that any modifications to data are detected and authorised. For instance, if unauthorised users attempt to modify data, these security measures will either block the changes or flag them for review. Maintaining data integrity is crucial for ensuring that the information used remains accurate and trustworthy.

3) __Availability__

This principle outlines that the information provided should be readily accessible to authorised users (e.g. a password manager) (https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). Ideally, all systems involved in accessing, processing and storing the relevant data must be functioning correctly at all times. ((https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security). Implementing redundancy, load balancing, and disaster recovery plans helps maintain system availability. For example, a password manager should be readily accessible to users at all times, and measures such as regular backups and failover systems should be in place to prevent downtime. Ensuring availability means that users can rely on uninterrupted access to critical information and services.



https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security



### _Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6._


Focusing on the principle of confidentiality, there are several measures that can be taken to enforce this; namely, authentication, authorisation and password encryption. Authentication refers to the verification of the identity of a user attempting to access or interact with the API, while authorization refers to the verification that the authenticated user has permission to access the resource requested. There are several mechanisms that can be integrated into an API to enforce user authorization.

#### Using HTTPS

The most basic, standard step that can be taken in order to ensure confidentiality is by ensuring all API endpoints are sent over HTTPS. It is a secure layer within the server that is required in order to encrypt the incoming and outgoing data, thus preventing exposure to eavesdropping or communication interception. A TLS/SSL certificate is required before one is able to install and configure this encryption layer within the server. 
https://www.linkedin.com/advice/1/how-can-you-ensure-api-data-confidentiality-a3hne


#### Authentication

    * Basic: One of the most simple authentication methods involves sending and username and password with each request. These credentials are generally encoded using Base64 and included in the HTTP header. Despite its simplicity, Basic Authentication is limited in that it leaves the program vulnerable to interception if not used over HTTPS.
    https://medium.com/@namanoli/exploring-popular-authentication-methods-for-rest-apis-a-comprehensive-guide-9c68002210e2


    * Digest: Unlike basic authentication, digest authentication does not require the password to be transmitted. Initially, the client requests access and the server responds with a 401 Unauthorised status, a nonce, a realm value. The client uses the MD5 hashing algorithm to create a response digest, which is sent in the second request. The server then performs the same hashing and compares the results. If they match, access will be granted to the user. This method enhances security by using hashed values and unique single-use nonces to prevent unintentional exposure of user credentials.
    https://learning.postman.com/docs/sending-requests/authorization/digest-auth/
    https://www.sciencedirect.com/topics/computer-science/digest-authentication


    * Token-based Authentication: One of the most commonly used API authentication are token-based systems; generating access tokens which are then issued to the client upon successful authentication and can be used to access requested resources within a limited expiry period. JWTs also play a role in authorization: After ensuring the token's validity and expiry, it will then use the embedded information to determine if the user has the necessary permissions to access the requested resource. This dual functionality of JWTs ensures secure and efficient user identity verification and access control:

        * OAuth (Open Authourisations) tokens are commonly used and work by allowing third-party services to exchange access tokens in lieu of their credentials. OAuth employs a system of access tokens and refresh tokens; whereby the access tokens grants the user permissions and refresh tokens allow the user to acquire new access tokens (https://medium.com/@namanoli/exploring-popular-authentication-methods-for-rest-apis-a-comprehensive-guide-9c68002210e2).


        * JSON Web Tokens (JWT) are compact, URL-safe tokens that can be delivered to a user after successful authentication of their identity. The user agent can then send the token to access a protected route or resource to the Authorization header using the Bearer schema. This is where we see the dual functionality of JWTs, allowing the developer to orchestrate both authentication and authorisation.


        * API Key Authentication involves generating a unique API key for each client, which is then included in the request header. While API keys also grant access via a string of text, they differ from token authentication in one essential way. Unlike token authentication, API keys are able to identify the application making the request without providing any information specific to the user.
        https://www.netlify.com/blog/api-authentication-methods/
        

#### Authorisation

Authorisation, on the other hand, determines what the authenticated user is allowed to access or interact with in the API. Besides JWTs, which facilitate both authentication and authorisation, there are a myriad of other measures that can be taken to ensure sensitive data remains intact. These include:

    * Using strong hashing algorithms such as Bcrypt, Argon2 or PBKDF
    * Adding unique salt to each password before hashing in order to prevent "rainbow table attacks"
    * Employing Role-Based Access Control (RBAC) in assigning permissions to roles rather than directly to users
    * Attribute-Based Access Control (ABAC) for using attributes (such as user, recourse, environment) to make authorisation decisions
    * OAuth 2.0 Scopes can be used in order to specify the levels of access the token holder has to resources





### _Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. (12 PTS)_


When developing the software for a social media platform, developers are faced with navigating a legal minefield in order to appropriately handle and protect user data. These various laws and acts demand certain security priorities be accounted for at every step of the development, and are strictly adhered to before the launch of the product. The legislation will vary based on the region in which you are practising. For the sake of clarity, I will mainly be referring to the European Union's General Data Protection Regulation ("GDPR"), which is the most common overarching legislation that has set a global standard for data protection. Despite varying legislations in different countries and regions, there are several key legal principles that are universally shared and crucial for all software developers to abide by.

Data minimization refers to the principle of only collecting personal data that is considered paramount for your app's functionality. The principle has become a part of data protection law when it was included in Article 5(1)(c) of Europe’s General Data Protection Regulation (GDPR), stating that personal data must be “adequate, relevant and limited to what is necessary in relation to the purposes for which they are processed” (https://privacy108.com.au/insights/data-minimisation-in-practice/). Similarly, Article 25 of the GDPR states that social media platforms must implement data protection principles by design and ensure only necessary personal data is processed by default. Furthermore, in the case of collecting any additional personal data, the app developers must obtain consent from users under the guidelines of the GDPR. These terms and conditions must be disclosed in explicit, unambiguous detail to the user within the consent form, prior to the processing of this data. For example, if it transpired that a social media application like Instagram has been collecting additional, irrelevant data from the user's phones (such as sensitive health or contact information) without proper disclosure, it would leave the company liable to legal action. As a general rule for developers, if the application can function without the data in question, it is likely additional consent will be required in order for it to be retrieved from the user. Developers can enforce data minimisation by only collecting necessary data, establishing data retention policies, anonymising data, implementing access controls, allowing granular user consent and using data aggregation.
https://www.lexr.com/en-ch/blog/data-protection-and-gdpr-for-app-developers/


Two of the most paramount principles of ethical data handling are that of transparency and obtaining consent; the user must be notified about what data is being collected, for what purpose, their-party transfers and their rights. This is generally done via a privacy policy. Any company which owns a social media platform must emphasise their transparency and accountability to users, and the jurisdictions of which must be subsequently drilled into their software development team. The specifics of transparency jurisdiction is delved into further Article 12 of the GDPR, which mandates that information provided to individuals about the processing of their personal data must be "concise, transparent, intelligible and easily accessible, using clear and plain language" (https://gdprhub.eu/Article_12_GDPR#:~:text=Article%2012(1)%20GDPR%20requires,using%20clear%20and%20plain%20language.). Similarly, in order to maintain transparency, integrity and accountability, developer of a social media platform must also abide by Article 33 of the GDPR, which mandates that social media platforms notify supervisory authorities and affected users without delay in the event of a data breach.


In regards to consent practices, Article 7 outlines the legal conditions that must be undertaken when obtaining consent from a user, while Article 6 provides more specific conditions regarding lawful data processing; both of which should be regularly referenced when developing a social media application (https://gdpr-info.eu/art-7-gdpr/). Furthermore, as social media apps generally involve the exchange of media, practices regarding children's safety must also be considered and enforced. Article 8 of the GDPR provides special protections for children's personal data, forcing social media platforms to obtain parental consent for minors under the age of 16 (or lower) before offering them online services. Platforms of this maturity must also ensure that the language used to communicate with children is clear and palatable (https://gdpr-info.eu/art-8-gdpr/). In order to build user trust and deliver ethical data handling, users should be required to provide consent, remain informed about data collection practices, be provided with accessible privacy policies and receive real-time notifications about data usage and/or changes in handling practices.


Data encryption and anonymisation are critical practices for software developers aiming to protect personal data and ensure privacy compliance. Encryption involves converting sensitive information into a secure format during storage and transmission, using robust algorithms and secure key management to prevent unauthorised access (as outlined in Q7). This is mandated under regulations like GDPR, which requires encryption to safeguard personal data and mitigate risks of data breaches. Anonymisation techniques, such as data masking and pseudonymisation, are commonly employed to anonymise data sets, subsequently reducing the risk of identifying individuals while enabling data usability. The GDPR defines anonymous data as information that “does not relate to an identified or identifiable natural person or to personal data rendered anonymous”, thus making the data subject unidentifiable (https://usercentrics.com/knowledge-hub/data-anonymization/#:~:text=The%20GDPR%20defines%20anonymous%20data,encryption%20or%20removal%20of%20personally): This implies that if data has been anonymised, the GDPR does not govern that data. However, while anonymisation is referred to in Recital 26 of the GDPR, there is no explicit definition as to what qualifies as effective anonymisation in real-world instances (https://usercentrics.com/knowledge-hub/data-anonymization/#:~:text=The%20GDPR%20defines%20anonymous%20data,encryption%20or%20removal%20of%20personally). This lack of clarity can lead to issues for organisations seeking absolute compliance with the GDPR, but can be mitigated by adhering to transparency, documentation and disclosure of your company's specific privacy policies. Developers must adhere to these principles to uphold user privacy rights, build trust, and comply with stringent data protection laws worldwide, including CCPA and HIPAA, which also emphasise the importance of securing personal information through encryption and anonymisation measures.

Lastly, developing a social media platform entails navigating complex copyright issues and legal obligations pertaining to intellectual property rights. Within this context, it is critical that developers ensure that the platform's codebase, user-generated content and media assets do not infringe upon existing copyrights. This includes respecting the ownership rights for original content posted by users and implementing appropriate mechanisms to address any copyright claims that may arise. Similarly, compliance with open-source licences such as GPL or Apache is crucial when integrating third-party software components or libraries. Understanding fair use principles is also paramount, particularly when users share copyrighted content within the platform for purposes like commentary or criticism. Laws such as the Digital Millennium Copyright Act (DMCA) outline the procedures taken in responding appropriately to copyright infringement claims. Incorporation of such copyright notices and maintaining vigilance surrounding these licensing terms will ensure software developers of social media platforms respect intellectual property rights while also fostering a creative and legally compliant environment.
https://www.yorku.ca/osgoode/iposgoode/2021/04/05/social-media-privacy-legalities-of-personal-data-collection/




### _Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure._

https://myscale.com/blog/essential-components-relational-database-structure/#the-logical-structure-tables-keys-and-relationships

"Normalisation" is the structural technique used within the relational database model to organise the data into logical structures and thus minimise redundancy/duplication. It ensures that each segment of data is stored in a manner that maintains integrity and facilitates efficient querying and manipulation. While normalisation aids in maintaining data integrity, its primary focus is on structuring the database schema effectively.

The Entity Relationship Diagram (ERD) is a conceptual, visual model used in designing a database. The relational schema is a logical model that is then used to establish the framework outlined in the ERD; including the tables, columns, data types, constraints and relationships between each of the tables. The database schema behaves as a specific blueprint for how the data will be organised and managed. This information is often then stored in a special part of the database called the "data dictionary" or "system catalogue".

The structure of a relational database model (RDBMS) revolves around objects often referred to as 'relations'. These relations are the fundamental units of data storage in a relational database and are represented as tables. Each table consists of rows and columns, not unlike a spreadsheet. Much like a standard table format, every row represents a single record or tuple and contains data corresponding to attributes defined by the column titles. Whereas the columns, also known as attributes, represent a specific data field within a table. Each column will be defined by their distinct names and data types (e.g. integer, varchar, string, etc).

Keys are then used as unique identifiers that distinguish the roles and structure of entities within the table. The primary key (PK) ensures each row in a table has a unique identifier. The primary keys ensure that no two rows have the same primary key value and enforce entity integrity. Conversely, a foreign key is a column or set of columns in one table that makes reference to the primary key of another table. These keys delineate the relationships between tables, enabling the linking of related data across two or more tables.




### _Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database._

https://www.knowledgehut.com/blog/database/integrity-constraints-in-dbms

The relational database model (RDBMS) places a strong emphasis on ensuring the integrity of stored data in order to guarantee accuracy, reliability and consistency throughout the database's lifecycle. There are 3 primary types of data integrity within the RDBMS: entity integrity, referential integrity and domain integrity. Each type is enforced via specific constraints and mechanisms.


_1. Entity Integrity_

Entity integrity ensures that each row within the table is uniquely identifiable, which is typically achieved by assigning a primary key (PK) to one or more columns. A PK constraint mandates that these columns are not-null and contains unique values, thereby preventing duplicate entries and ensuring every entry is distinct. For example, in a "students”  table, a PK like `student_id` would ensure that each student is uniquely identifiable (as in theory, two students could share the same name, making `student_name` an invalid PK).


_2. Referential Integrity_

Referential integrity focuses on maintaining consistent relationships between tables. This is enforced using foreign keys; where a foreign key in one table references the primary key of another table. These constraints will guarantee that every foreign key value corresponds to a valid primary key value in its referenced table, or is null where applicable. Cascading actions such as `ON UPDATE CASCADE` or `ON DELETE CASCADE` can be specified to automatically update or delete related records when changes occur. For instance, in an "orders" table, a `customer_id` foreign key would reference the `customer_id` primary key within the "customers” table. In this example, the use of referential integrity will ensure each order is associated with a valid customer via checking for an existing customer id.


_3. Domain Integrity_

The domain integrity refers to an array of procedures that seek to ensure that data values adhere to defined constraints within each column's data domain. The "domain" in question is defined as a "set of suitable values that a column is permitted to enclose" (https://www.astera.com/type/blog/data-integrity-in-a-database/#:~:text=Domain%20Integrity&text=Here%2C%20a%20domain%20is%20defined,is%20in%20a%20defined%20domain.): This includes specification of data types (e.g. varchar, integer, date, boolean, etc.) to ensure consistency in data storage. By enforcing `NOT NULL` constraints, the presence of valid data will be mandated. Furthermore, `UNIQUE` constraints can be applied to prevent duplicate values within a column. `CHECK` constraints allow for custom validation rules, for example, ensuring a price column in a "products" table remains positive. `DEFAULT` constraints can also be used to set a default value when no explicit value is disclosed.


Additionally, other mechanisms such as "triggers" and stored procedures are used to further galvanise data integrity by  automating actions in response to specific database events. Triggers are employed to execute procedural code upon insert, update or delete operations and facilitate complex integrity measures that extend beyond standard constraints. Stored procedures, which consist of precompiled SQL statements, can also provide assistance in consolidating data integrity logic during database operations.




### _Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database._

https://www.dremio.com/wiki/crud-operations/#:~:text=CRUD%20Operations%2C%20an%20acronym%20for,modifying%20data%2C%20and%20deleting%20data.
https://satoricyber.com/glossary/dml-data-manipulation-language/


Database languages like Structured Query Language (SQL) languages used for database creation and manipulation. Data Manipulation Language is a sublanguage of SQL that is explicitly used to make changes to the database. The acronym "CRUD" stands for Create, Read, Update, Delete and outlines what the DML is used for:


**CREATE** (`INSERT`) -> The `INSERT` statement is used to add data to the database. The operation involved establishing values for each column in a table or using default values where applicable. For example, if I wanted to add a new employee record to an "employees" table, I would insert a new row with all relevant details such as name, department and hire date.


**READ** (`SELECT`) -> Data retrieval is executed using `SELECT` statements. These statements allow users to query the database to retrieve specific information based on particular conditions and criteria. For instance, the command `SELECT * FROM employees;` can be used to retrieve all data from the table titled "employees". While 'read' operations do not alter the data, they are often included in discussions of data manipulation as they are essential for accessing and utilising the data.


**UPDATE** (`UPDATE`) -> Data modification is achieved using `UPDATE` statements. This operation allows the user to change the existing data within a table. For example, updating an employee's department from 'Sales' to 'Marketing' involves specifying the new value and the conditions under which the update should occur.
The command would look something like this:
```
UPDATE Employees
SET department = 'Marketing'
WHERE department = 'Sales' AND name = 'John Doe';
```


**DELETE** (`DELETE`) -> Removing data is executed via `DELETE` statements. This operation removes specific rows or entire sets of data from a table based on specified conditions. Deleting an employee record from the Employees table would involve identifying the record by its unique identifier (e.g. employee ID).


When creating an API using Flask, SQLalchemy can be used to create CLI commands to execute these commands via the terminal (e.g. flask create, flask seed, flask drop).






### _Q12. Conduct research into a web application (app) and answer each of the following sub-questions: (42 PTS)_


#### _List and describe the software (tech stack) used by the app._


_* Programming languages_

**Frontend:** Airbnb utilises both JavaScript and React for its frontend development. JavaScript is extensively used for creating dynamic user interfaces and responsive web applications. React, a JavaScript library, facilitates creation of reusable UI components, making it a flexible and efficient solution for constructing a streamlined user interfaces.

**Backend:** Airbnb employs both Java and Ruby on Rails for its backend operations. Java, a robust backend language, is widely regarded for its scalability and performance. Ruby on Rails is a web application framework, providing accelerated development capabilities and subsequently reducing costs and time to market.

_* Databases_

Airbnb manages its data using MySQL and Amazon RDS. While MySQL is utilised for data storage, Amazon RDS offers database management services using the cloud. Amazon RDS simplifies general administration and routine tasks required when dealing with relational databases; thus, providing a scalable solution for Airbnb's database needs. The application also uses engines like Presto, Airpal and Druid for data processing and management.

_* Cloud services_

Airbnb utilises Amazon S3 for storing static assets like property images and user profile pictures securely to ensure scalable access. They also use Amazon EC2, which provides computational resources for running dynamic app components such as backend server logic; this service interacts with S3 in facilitating the retrieval and serving of static assets. Airbnb also uses Amazon CloudFront to enhance their performance by caching content globally, reducing latency and improving the overall user experience through faster load times. The interplay of S3, EC2 and CloudFront forms a scalable infrastructure to support Airbnb's operations, optimise their content delivery and enhance user interactions globally.


_* Webserver_

Nginx serves dual roles as both a high-performance HTTP web server and a reliable reverse proxy tool within the Airbnb app. It's ability to efficiently deliver static content such as HTML, CSS and Javascript files to users accelerate frontend performance by reducing backend server load. As a reverse proxy, Nginx distributed incoming requests across multiple backend servers (including those on Amazon EC2) in order to optimise resource use and response times. It ensures security with SSL/TLS management and HTTPS encryption, while its flexible configuration supports caching strategies and performance adjustments for scalability. This plethora of features maintain seamless service uptime by routing traffic to healthy servers, managing failures, and ensuring a resilient user experience globally.

_* Caching and key-value storage_

In Airbnb's tech stack, Redis is essential for caching frequently accessed data such as user sessions and database queries to reduce latency and subsequently improve performance. It serves as an efficient key-value store for managing real-time analytics, use preferences, and temporary data. Redis also supports pub/sub messaging for asynchronous communication and acts as a secure session store, ensuring seamless user interactions across the platform.


_* Queries & Analytics_

Airbnb collaborated with Facebook's PrestoDB to launch Airpal, a web-based query tool which allows their data analysts and engineers to interact with large datasets stored in their data infrastructure. This tool provides a user-friendly UI for writing and executing SQL queries against Airbnb's data warehouse; facilitating tasks such as generating reports, conducting as-hoc analyses, and extracting insights to support decision-making across various business functions.
https://airbnb.io/projects/airpal/

Airbnb also utilises tools like Google Analytics and Mixpanel to analyse user behaviour and evaluate website performance. Google Analytics provides comprehensive metrics on user interactions, traffic sources and conversion rates, while Mixpanel offers detailed insights into user engagement and product usage trends.
https://www.airbnb.com/help/article/2866#:~:text=For%20example%2C%20to%20help%20us,Out%20Browser%20by%20clicking%20here.
https://stackshare.io/airbnb/airbnb


_* Communication and Messaging Tools_

Airbnb has collaborated with Twilio to facilitate user communication services. Twilio provides APIs from SMS, voice and messaging, which enables Airbnb users to exchange notifications, alerts and support messages. Twilios's v3 Web API, SendGrid, provides a REST-like interface that specialises in email delivery and marketing campaigns. This tool allows the Airbnb platform to efficiently manage transactional emails, marketing communications and newsletters at a large scale. These platforms play a critical role in enhancing user engagement by ensuring reliable and effective communication channels. 
https://www.twilio.com/en-us/blog/airbnb-click-to-call-twilio-html
https://www.twilio.com/docs/sendgrid/api-reference


_* Monitoring and Logging_

Airbnb utilises a robust suit of monitoring and logging tools such as New Relic, Kibana,  Sentry and Datalog. These tools play crucial roles in monitoring system performance, detecting issues in real-time, and providing detailed logs for troubleshooting. New Relic offers performance metrics and application monitoring, while Kibana facilitates log analysis and visualisation. Furthermore, Sentry specialises in error tracking and reporting, thus streamlining Airbnb's ability to quickly identify and resolve issues that arise. Lastly, Datalog provides comprehensive monitoring across all platforms, ensuring reliability and efficient performance via proactive monitoring and responsive incident management.
https://www.linkedin.com/pulse/deciphering-airbnb-tech-stack-replicating-python-fiona-githaiga-6j7cf/


_* DevOps and Deployment_

Airbnb uses GitHub for version control, Webpack for frontend asset bundling, and tools like Vagrant and Chef for automated infrastructure management. These tools streamline development processes and ensure efficient deployment of updates and features.
https://www.linkedin.com/pulse/deciphering-airbnb-tech-stack-replicating-python-fiona-githaiga-6j7cf/


_* Business Tools_

Airbnb uses collaboration tools like Slack, G Suite, Asana and InVision for efficient communication, project management and collaboration across all teams. 
https://www.linkedin.com/pulse/deciphering-airbnb-tech-stack-replicating-python-fiona-githaiga-6j7cf/


_* Google Maps API Inegration_

Airbnb has integrated the Google Maps API in order to enable accurate location services. This feature allows users to easily locate their accommodation via accurate directions and map visualisation.
https://intuji.com/airbnb-tech-stack-explained-airbnb-app/


_* Payment Gateways_

Airbnb utilises Braintree, a payment processing platform owned by Paypal, as its payment gateway. This allows Airbnb to process payments on its own platform, ensuring security and reliability for its users. Braintree supports a wide range of payment methods, including credit cards, Paypal, Apply Pay and Google Pay.
https://intuji.com/airbnb-tech-stack-explained-airbnb-app/
https://www.airbnb.com/help/article/126



#### _Describe or make educated guesses about the hardware used to host the app._

https://aws.amazon.com/intel/

Like many other tech magnates, Airbnb has not disclosed detailed specifics regarding the hardware infrastructure used to host its application. However, based on industry practices, trends and other information we have already covered about the Airbnb tech stack, here are some inferences that can be made about the hardware used:

Firstly, Airbnb has disclosed that they use Ngnix HTTP web server in enhancing performance, scalability and security across their web services and applications.

Another thing we're already aware of is that Airbnb heavily relies on the AWS cloud infrastructure. Amazon has provided information regarding their longstanding and collaborative partnership with Intel. From the information provided by AWS regarding their processors, we are able to infer that this hardware plays a role in the structural framework of Airbnb. For example, the array of EC2 instances offered by Amazon are powered by Intel Xeon processors. These processors boast their high performance, advanced security features and energy efficiency (https://aws.amazon.com/intel/). Given that we're aware Airbnb utilises Amazon EC2 for their web hosting, scaling and backend server logic, we can subsequently infer these Intel processors are also potentially involved in hosting software within the Airbnb application. Furthermore, AWS has developed some custom hardware, such as the AWS Nitro System: This system includes custom-designed hardware, such as Nitro cards and Nitro Security Chips, which offload virtualisation functions and enhance security and performance in EC2 instances.

Similarly, it's been established that Airbnb uses Amazon S3 to manage and store various media assets. Amazon has disclosed that they use various storage options such as SSDs (Solid State Drives) and HHDs (Hard Disk Drives) across various services; of which Amazon S3 is included (https://aws.amazon.com/compare/the-difference-between-ssd-hard-drive/).

Unfortunately, the amount of information disclosed about the hardware used in Airbnb is understandably limited. Given their gold standard status in efficiency and performance, it's most likely that Airbnb would utilise Intel Xeon Processors, either first-hand or passively via AWS services. Furthermore, we know that they utilise Amazon S3 for storage of various assets, however, I believe it is likely that Airbnb would opt to use SSDs due their superior performance; either for other assets or as a means of backing up their data. I'm making this prediction based on the fact that SSDs generally offer faster data access speeds and lower latency in comparison to other storage drive options. Furthermore, as discussed, it is highly likely to use AWS Nitro System, as well as Amazon's custom hardware as a result of utilising their various cloud services.




#### _Describe the interaction of technologies within the app._


The Airbnb application leverages various technologies in order to provide a seamless user experience. The frontend framework is developed using React and React Native for a responsive and dynamic user interface. When a user makes a request, it will first encounter an API Gateway, which then directs it through an AWs Elastic Load Balancer (ELB) in order to distribute traffic across multiple EC2 instances. The app then employs a microservices architecture, with each service (e.g. search, booking, user management) communicating via APIs; typically using REST or gRPC protocols.

The data processing and storage will then involve the interplay of multiple systems: structured data (user profiles, bookings, reviews) is handled by Amazon RDS, while unstructured data (session caching, dynamic content) by Amazon DynamoDB, and lastly media files (photos, videos) by Amazon S3. Data warehousing is managed by Redshift, with ETL processes transferring data for reporting and analytics.

AWS Auto-scaling is then used to ensure scalability by adjusting the number of EC2 instances depending on the demand. Furthermore, Docker containers by Kunernetes are used to orchestrate efficient resource utilisation. Security is maintained with AWS security groups, network ACLs, and data encryption via AWs KMS and TLS.

Monitoring and logging of data are conducted using Amazon CloudWatch from real-time metrics and the ELK stack (Elasticsearch, Logstash, Kibana) for centralised log management. Continuous integration and deployment are managed by Skinnaker and Github to facilitate code changes, texting and deployment of code.

The interaction of these technologies begins with user requests, which are processed through the API Gateway and ELB, handled by microservices querying databases and retrieving media files from S3. The processed data is returned to the frontend, which displays the information. CloudWatch and ELK monitor performance, while auto-scaling adjusts resources and Skinnaker and Github manage ongoing development and deployment.

Lastly, Airbnb employs machine learning algorithms to improve the search process, prevent fraud and help hosts to optimise their pricing based on the current economic climate.


https://news.airbnb.com/sharing-more-about-the-technology-that-powers-airbnb/#:~:text=You%20may%20not%20realize%2C%20but,to%20helping%20hosts%20optimize%20pricing.


#### _Describe the way data is structured within the app’s database(s)._


As the Airbnb application has transitioned from a monolithic to microservices architecture, the application's data infrastructure has directed its focus to becoming scalable and highly adaptable. The data framework combines relational, NoSQL, and object storage databases to efficiently manage and utilise vast amounts of data. Relational databases (Amazon RDA with PostgreSQL) store structured data requiring complex queries, such as user profiles, accommodation listings, bookings and reviews. NoSWL databases, such as Amazon Dynamo DB) handle high-speed access to unstructured data, such as session management and activity logs. Similarly, as previously discussed, static media files like images and videos are stored in Amazon S3. Analytical data and large-scale processing are managed through Amazon Redshift, which aggregates data from various sources for reporting and various user insights. The hybrid approach ensures transactional consistency, quick access to data, and efficient large-scale analytics, providing a seamless user experience.



#### _Identify the entities/tables that are tracked within the app’s database(s)._

According to my understanding of Airbnb's tech stack, architecture and business logic, these are the entities/tables that can be tracked within the database:

```
Users
├── user_id (PK) (Integer)
├── username (VARCHAR/String, UNIQUE, NOT NULLABLE)
├── password (VARCHAR/String, NOT NULLABLE)
├── email (VARCHAR/String, NOT NULLABLE, UNIQUE)
├── updated_at (Date/Current Timestamp)
├── created_at (Date/Current Timestamp)
└── is_admin (BOOLEAN, DEFAULT=FALSE)

Orders
├── order_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── user_id (FK, ref: Users) (Integer, NOT NULLABLE)
├── order_date (Date/Timestamp, NOT NULLABLE)
├── total_amount (Decimal, NOT NULLABLE)
└── order_status (VARCHAR/String, NOT NULLABLE)

Order_Product
├── order_items_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── order_id (FK, ref: Orders) (Integer, NOT NULLABLE)
├── product_id (FK, ref: Products) (Integer, NOT NULLABLE)
├── order_quantity (Integer, NOT NULLABLE)
└── order_price (Decimal, NOT NULLABLE)

Reviews
├── review_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── user_id (FK, ref: Users) (Integer, NOT NULLABLE)
├── product_id (FK, ref: Products) (Integer, NOT NULLABLE)
├── rating (Integer, NOT NULLABLE)
├── comment (VARCHAR, NOT NULLABLE)
└── created_at (Date/Timestamp, NOT NULLABLE)
```
```
Products
├── product_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── name (VARCHAR, NOT NULLABLE)
├── description (VARCHAR, NOT NULLABLE)
├── price (Decimal, NOT NULLABLE)
├── stock_quantity (Integer, NOT NULLABLE)
├── created_at (Date/Current Timestamp)
└── updated_at (Date/Current Timestamp)


Product_Categories
├── product_id (Composite PK) (FK, ref: Products)
└── category_id (Composite PK) (FK, ref: Categories)

Inventory
├── product_id (Composite PK) (FK, ref: Products) (Integer, NOT NULLABLE)
├── location_id (Composite PK) (FK, ref: Locations) (Integer, NOT NULLABLE)
└── stock_quantity (Integer, NOT NULLABLE)
```
```
Categories
├── category_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── name (VARCHAR, NOT NULLABLE)
└── description (VARCHAR, NOT NULLABLE)
```
```
Locations
├── location_id (PK) (Integer, UNIQUE, NOT NULLABLE)
├── name (VARCHAR, NOT NULLABLE)
└── address (VARCHAR, NOT NULLABLE)
```


Airbnb’s databases track various entities to manage user interactions, listings, transactions, and activities. In relational databases (Amazon RDS with PostgreSQL), key tables include Users (user information), Listings (property details), Bookings (transaction records), and Reviews (user feedback). NoSQL databases (Amazon DynamoDB) manage Sessions (user session data) and Activity Logs (user activities). Object storage (Amazon S3) holds media files for listings and user documents. Data warehousing (Amazon Redshift) aggregates data in tables like Bookings Summary (booking analytics) and User Activity (user interaction summaries). These entities ensure efficient management of user data, property listings, transactions, and analytics.



#### _Identify the relationships and associations between the entities/tables identified in sub-question E._

```
Users (PK: user_id)
│
│   * [Users -> Orders: One-to-Many]
│
├── Orders (PK: order_id)
│   └── Users (FK: user_id) * [Many-to-One]
│
│
Products (PK: product_id)
├── Order_Product (PK: order_item_id) * [One-to-Many]
│   ├── Orders (FK: order_id) * [Many-to-One]
│   └── Products (FK: product_id) * [Many-to-One]
│
│   * [Products -> Product Categories: Many-to-Many]
│
├── Product_Categories (Composite PK, FK: product_id + category_id) * [Many-to-Many]
│   ├── Products (PK, FK: product_id)
│   └── Categories (PK, FK: category_id) * [Many-to-One]
│
│   * [Products -> Reviews: One-to-Many]
│   * [Users -> Reviews: One-to-Many]
│
├── Reviews (PK: review_id), (FK: user_id, product_id)
│   ├── Users (FK: user_id) * [Many-to-One]
│   └── Products (FK: product_id) * [Many-to-One]
│
│   * [Products -> Inventory: One-to-Many]
│
└── Inventory (Composite PK, FK: product_id + location_id)
    ├── Products (product_id) * [Many-to-One]
    └── Locations (location_id) * [Many-to-One]
│
Categories (PK: category_id)
├── Product_Categories (Composite PK, FK: product_id + category_id) * [One-to-Many]
│  ├── Products (PK, FK: product_id) * [Many-to-One]
│  └── Categories (PK, FK: category_id) * [Many-to-One]
│
Locations (PK: location_id)
└── Inventory (PK, FK: product_id + location_id) * [One-to-Many]
    ├── Products (PK, FK: product_id) * [Many-to-One]
    └── Locations (PK, FK: location_id) * [Many-to-One]
```


#### _Design an entity relationship diagram (ERD) based on the answers provided to sub-questions E and F. This must represent a relational database model, even if the app itself uses something other than a relational database model._



![Airbnb](/Airbnb_ERD.drawio.png)



**REFERENCES**


Wallis, J. (2023) Airbnb Tech Stack explained: The Tech behind the Airbnb app, Intuji. Available at: https://intuji.com/airbnb-tech-stack-explained-airbnb-app/ (Accessed: 21 June 2024).

https://stackshare.io/airbnb/airbnb

https://cloud.google.com/learn/postgresql-vs-sql

https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/

https://www.atlassian.com/agile/product-management

https://www.atlassian.com/git/tutorials/what-is-version-control#:~:text=Version%20control%2C%20also%20known%20as,to%20source%20code%20over%20time.

https://www.techopedia.com/2/27825/security/the-basic-principles-of-it-security


