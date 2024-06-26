Workbook_PartA

### **Q1. Describe the architecture of a typical API project, such as a Flask application.**


While building a typical API project, such as a Flask application, the software architechure hinges on several pivotal components to handle the serialization and managament of data, as well as efficient API endpoint handling. The application will be typically involve a central file from which the application is initialised and run, (customarily this will be titled 'run.py' in order to be recognised by Flask). In order to facilitate maintainability and collaboration between developers, the application should be separated into different directories and files. The main `app/` directory will contain an `__init__.py` file and a `config.py` file. This directory should contain subdirectories containing the ORM models, CLI controllers, schemas, API endpoints (routes) and utility functions.


_1. Mapping an ERM (Entity Relationship Model)_

Typically, it is customary for developers to organize the structure of the application using an Entity Relationship Model (ERMs), which serve as a blueprint for how data is stored, organized, and related within a system. ERMs provide the developer with a clear breakdown of the application structure by defining the central entities, their attributes and the relationships between them. By mapping these elements in a visual representation, it provides a clear reference point for the developer to refer back to in order to ultimately ensure data integrity, optimize query performance, and facilitate maintenance and scalability of the database system.

_2. Configuration Settings_

Configuration settings for different environments are managed in separate config files. This allows the application to easily switch between settings for development, testing, and production, ensuring that sensitive information like database credentials is handled securely and appropriately.


_3. Database Management_

- Object-Relational Mapping (SQLAlchemy)
    ORMs are utilised to map database tables to Python objects, allowing developers to interact with relational databases (e.g., SQLite, PostgreSQL, MySQL) using Python code instead of raw SQL. In the context of a flask application, SQLAlchemy is an SQL toolkit and ORM library used as an interface to manage database schema, query execution, and transactions. The ORM models will be sequestered into their own `models/` directory, and each model defined will represent a database table. The database is then configured in the `config.py` file, which is used to specify database URI and SQLAlchemy settings.

- Serialization/Deserialization (Marshmallow)
    The ORM models then require another library in order to serialize and deserialize the data provided. In order to convert complex data structures into a format that can be easily transmitted or stored, a typical APi project such as a Flask application will require the use of a library such as Marshmallow.


_4. Environment Variables_

Environment variables are managed using files like `.env` and `.flaskenv`, which store configuration data such as database URLs, secret keys, and other environment-specific settings; which are loaded into the application at runtime. As the `.env` file contains sensitive information, it is typically placed in a `.gitignore` file in order to avoid exposing sensitive information such as database credentials or API keys. A `.envsample` or `.envexample` file is used to indicate the contents of the `.env` file to fellow developers to provide guidance on configuring the application's environment variables without disclosing sensitive information (e.g. DATABASE_URL=, JWT_SECRET KEY=).


_5. Dependencies_

Dependencies required for the project are listed in `requirements.txt`. This file includes all the libraries and packages that need to be installed for the application to run properly. It ensures that the development environment is consistent and easily replicable.


_6. API Endpoints (Routes)_

API endpoints are defined in the routes directory. Each route corresponds to a specific URL path and HTTP method (GET, POST, PUT, DELETE), and handles requests by interacting with the models and returning responses.


_7. Command Line Interface (CLI) Controllers_

CLI controllers provide commands for administrative tasks, such as creating, deleting or seeding database tables or running background jobs. These commands are defined in the cli directory and can be executed from the command line.


_8. Middleware and Request Handling_
Middleware: Middleware in Flask is employed for cross-cutting concerns such as authentication, logging, and error handling.
Request Handling: Flask’s request/response cycle processes incoming requests by passing them through middleware and directing them to the relevant endpoints.


_9. Testing and Debugging_

Unit Testing: For testing endpoints, models, and schemas, you can use either `unittest` or `pytest`.
Debugging: During development, Flask’s built-in debugger (`app.run(debug=True`)) helps identify and resolve issues.




### **Q2. Identify a database commonly used in an API project (such as a Flask application) and discuss the pros and cons of this database.**


PostgreSQL is an advanced, open-source relational database management system (RDBMS) commonly used in an API project such as a Flask application. It supports SQL for relational queries and JSON for non-relational queries, offering a powerful and flexible platform for a wide range of applications. As a fully ACID-compliant database, PostgreSQL ensures reliable transactions and maintains data integrity. It also boasts advanced features such as complex query capabilities, indexing, full-text search, and support for custom data types and functions.


**Pros:**


_1. ACID Compliance:_ PostgreSQL is fully ACID-compliant, ensuring data integrity, as well as reliable transactions. This is crucial for applications requiring consistent and accurate data.


_2. Advanced Features:_ PostgreSQL provides advanced features like complex queries, foreign keys, triggers, views, and stored procedures, in order to enable sophisticated data manipulation and the implementation of business logic directly within the database.


_3. Extensibility:_ PostgreSQL's is a highly extensibile system, offering a myriad of customisable options to the user to meet their specific application needs. Users can define their own data types, index types, and functional languages. It is also a packaging tool for database add-ons, supporting languages like PL/pgSQL, PL/Python, Java, and even JavaScript; allowing developers to write and run functions in various languages within the database by exposing an interface for language integration. This interface enables seamless execution of functions regardless of their underlying language, thus simplifying complexity by providing an extensible language function. This capability allows larger companies to develop functional packages tailored to their specific business domains.

_4. Performance:_ PostgreSQL supports complex queries, foreign keys, triggers, views, and stored procedures, enabling sophisticated data manipulation and business logic directly within the database. Its powerful indexing and optimization techniques make it suitable for managing large datasets and high-concurrency environments efficiently. Additionally, it uses Multi-Version Concurrency Control (MVCC) to handle concurrent processing and maintain high transaction rates with minimal risk of deadlocks, as well as ensuring high availability and provides server failure recovery mechanisms (https://cloud.google.com/learn/postgresql-vs-sql#section-8).

_5. Open Source:_ PostgreSQL being open source is highly beneficial as it is cost-effective, reducing database management expenses since it is free to use. It enjoys strong community support, with a large and active developer base ensuring rapid bug fixes, regular updates, and abundant resources. The open-source nature allows for high flexibility and customization, enabling users to modify the source code to meet specific needs. Additionally, it offers transparency for inspecting code security and reliability, fosters innovation through global collaboration, and avoids vendor lock-in, providing freedom in choosing support and services.

_6. Security:_ While it has internally integrated security features such as data encryption, SSL certificates, and advanced authentication methods, it also has secuirty extension available to further enhance the security of the application (https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/). Regarding parameter security, PostgreSQL offers configurations at the operating system level to secure the environment surrounding your database. For application security, it provides user privilege management by categorizing accounts into roles such as read-only, read/write, and others. Beyond granting specific permissions to users, you can also establish ongoing permissions for various actions or resources (https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/).



**Cons:**



_1. Complexity:_ Due to its advanced features and extensive configuration options, PostgreSQL can be more complex to set up and maintain compared to simpler databases like SQLite.

_2. Resource Intensive:_ PostgreSQL can be more resource-intensive, requiring more memory and CPU, which might be a concern for smaller applications or those running on limited hardware.

_4. Learning Curve:_ The richness of features means there is a steeper learning curve for new users or developers who are not familiar with its capabilities and configuration options. It has also been noted that the initial installation may also be dififcult for beginners.
- Installation can be difficult for beginners (https://cloud.google.com/learn/postgresql-vs-sql).

_5. Scaling Write Operations:_ While PostgreSQL handles read operations very efficiently, scaling write operations across multiple servers can be challenging and may require additional tools and configurations (e.g., sharding, replication).

_6. Slower performance:_ As this database has a stronger focus on delivering compatibility, the speed of peformance has been impacted when compared to other RDBMS like SQL Server and MySQL ((https://cloud.google.com/learn/postgresql-vs-sql)). It has also been noted that some SELECT queries may be slower than their counterparts. 



### _Q3. Discuss an implementation of an Agile project management methodology for an API project._

https://www.atlassian.com/agile/product-management

Agile Product Management hinges on consistently garnering user feedback and incorporating it into updates. This iterative approach involves a series of steps that integrate multiple feedback intervals to promote adaptability and ensure the delivery of the best possible version of the product. After deciding on the steps to be taken, the project is divided into several segments, commonly known as user stories, which are distributed among the team of developers.

_Define API Objectives & Roles:_ The purpose and vision of the API will be discussed in detail with the entire cross-functional team; including developers, QA engineers, product owners, UX/UI designers, and possibly stakeholders. Once the objectives and key features of the API project have been established, clear roles should be defined among members of the team; including Scrum Master, Product Owner, and Development Team members.

_Developing a Roadmap:_ Typically, an API project under APM will involve the construction of a product roadmap, outlining a timeline for how the product is intended to develop over time. This involves delineating large areas of functionality from which initiatives are composed (https://www.atlassian.com/agile/product-management). Roadmaps are designed to be flexible and are likely to change over the course of the project. Each initiative in the roadmap is broken down into a set of requirements, tailored throughout the process based on the team's collective understanding of the desired outcomes (https://www.atlassian.com/agile/product-management).

_Sprint Planning:_ After deciding on the steps to be taken, the API project will be divided into several segments, commonly known as user stories, which are distributed among the team of developers. From the broader intiatives, the work will be broken down in to "Epics". The epics are larger bodies of work that will then be broken down further into "Stories". In this step, the stories will be assigned to the developers and can typically be compelted in 1-2 week sprints until the entire epic is completed (https://www.atlassian.com/agile/product-management). The user stories should be ranked based on business value, complexity, and dependencies. At this step, the team will also devise story point estimations to provide the team and product owner with an achievable timeline. Scrum teams structure development into time-boxed sprints. At the beginning of each sprint, the team estimates the amount of work they can accomplish. A sprint burndown report subsequently monitors the progress of work throughout the sprint.

_Personal Planning & Execution:_ The developers will then work on their stories, while having daily stand-ups with the rest of the cross-functional to discuss any blockers, progress and next steps. This promotes expectation and gola alignment withint the team and allows for early identification of issues. Before commencing their stories, the developers will independently map their own story tasks using  APM tools like Jira, Trello, or Asana to track tasks and progress. For a software team working on an API project, the overall workflow would be decided, likely mirroring something like this: To-Do (Work that has not yet been started), In Progress (work that is currently being developed), Code Review (work that is completed and awaiting review), Done (work that has been completed and reviewed). The sprint burndown report of the API project will be repeatedly referenced to track team progress.

_Metrics:_ Review of Metrics will remain ongoing during and after the API project execution. This will require collecting and anaylsing relevant data along the way. Work in progress (WIP) limits ensure that both the team and the business focus on delivering the most critical tasks. Tools such as burndown charts and control charts help the team forecast their delivery pace, while continuous flow diagrams help identify bottlenecks (https://www.atlassian.com/agile/product-management). Other APM tools that may be used to track metrics include sprint burndown chart, epic burdown charts, velocity charts, control charts, culmunitive flow diagrams.A Gantt chart is also another APM tool that may prove useful to illustrate work completed over a period of time in relation to the time planned.

_Continuous Integration & Testing:_ During the development of this API project, the team must remain flexible to flutuations. Continuous inegretion and continous deployment pipelines (CI/CD Pipelines) will be implemented to automate testing and deployment processes. Similarly, unit, integration and performance texting for the API will be executed via automated tests: E.g. developers may use `unittest` or `pytest` to test the code in their stories. The team will ensure continuous improvement using APM tools such as resprospectives, Plan-Do-Check-Act (PDCA) Principle, Kanban method/metrics (https://www.atlassian.com/agile/product-management). Overall, this will require constant and efficient collaboration and communication between all members of the team.

_Review:_ At the conclusion of each sprint, a review of the finished work will be conducted with stakeholders and showcase new API functionalities; these are aptly named "Sprint Reviews". The sprint review will evaluate the sprint to determine successes, challenges, and opportunities for process enhancement. Retrospectives will be orchestrated at regular intervals for team reflection (https://www.atlassian.com/agile/product-management).


_Post Execution Monitoring:_ Feedback will then be collected from the early adopters or stakeholders and integrated into the product backlog. This API project will then be adapted backed on this feedback to coninously enhance the API. The aforementioned APM metrics tools will be continously reviewed and considered during this process to improve the project.


_Documentation & Versioning:_ Throughout production, it will be crucial for all members of the team to maintain up-to-date documentation for the API. For software developers, this means regularly committing their code to Version Control Systems such as Git to maanage changes and releases.




### _Q4. Provide an overview and description of a standard source control process for an API project._




### _Q5. Provide an overview and description of a standard testing process for an API project._




### _Q6. Explain the three principles of information system security._




### _Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6._




### _Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. (12 PTS)_




### _Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure._




### _Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database._





### _Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database._




### _Q12. Conduct research into a web application (app) and answer each of the following sub-questions: (42 PTS)_



#### _List and describe the software (tech stack) used by the app._



_* Programming languages_

**Frontend:** Airbnb utilizes both JavaScript and React for its frontend development. JavaScript is extensively used for creating dynamic user interfaces and responsive web applications. React, a JavaScript library, facilitates creation of reusable UI components, making it a flexible and efficient solution for constructing a steamlined user interfaces.

**Backend:** Airbnb employs both Java and Ruby on Rails for its backend operations. Java, a robust backend language, is widely regarded for its scalability and performance. Ruby on Rails is a web application framework, providing accelerated development capabilities and subsquently reducing costs and time to market.

_* Databases_

Airbnb manages its data using MySQL and Amazon RDS. While MySQL is utilized for data storage, Amazon RDS offers database management services using the cloud. Amazon RDS simplifies general administration and routine tasks required when dealing with relational databases; thus, providing a scalable solution for Airbnb's database needs.

_* Cloud services_

Airbnb utilizes Amazon S3 for storing static assets like property images and user profile pictures securely, ensuring scalable access. Amazon EC2 provides computational resources for running dynamic app components such as backend server logic and application servers, interacting with S3 for retrieving and serving static assets. Amazon CloudFront enhances performance by caching content globally, reducing latency and improving user experience through faster load times. This integrated use of S3, EC2, and CloudFront forms a scalable infrastructure that supports Airbnb's operations, optimizing content delivery and enhancing user interactions globally.

_* Webserver_

Nginx serves dual roles as both a high-performance web server and a reliable reverse proxy within the Airbnb app. It efficiently delivers static content such as HTML, CSS, and JavaScript files to users, enhancing frontend performance by reducing backend server load. As a reverse proxy, Nginx distributes incoming requests across multiple backend servers, including those on Amazon EC2, optimizing resource use and response times. Nginx ensures security with SSL/TLS management and HTTPS encryption, while its flexible configuration supports caching strategies and performance adjustments for scalability. Its high availability features maintain seamless service uptime by routing traffic to healthy servers, managing failures, and ensuring a resilient user experience worldwide.

_* Caching and key-value storage_

In Airbnb's tech stack, Redis is essential for caching frequently accessed data such as user sessions and database queries, which improves application performance by reducing latency. It serves as a fast and efficient key-value store for managing real-time analytics, user preferences, and temporary data. Redis also supports pub/sub messaging for asynchronous communication and acts as a secure session store, ensuring seamless user interactions across the platform.

_* Query Tool_

Airpal allows Airbnb's data analysts and engineers to query and interact with large datasets stored in their data infrastructure, typically based on Apache Hive. This tool provides a user-friendly interface for writing and executing SQL queries against Airbnb's data warehouse, facilitating tasks such as generating reports, conducting ad-hoc analyses, and extracting insights to support decision-making across various business functions.

_* Analytics and Utility Tools_

Airbnb utilizes tools like Google Analytics and Mixpanel to analyze user behavior and evaluate website performance. Google Analytics provides comprehensive metrics on user interactions, traffic sources, and conversion rates, while Mixpanel offers detailed insights into user engagement and product usage patterns. These analytics tools enable Airbnb to gain valuable insights that inform strategic decisions, optimize service offerings, and continually enhance the overall user experience.

_* Communication and Messaging Tools_

Airbnb relies on Twilio and SendGrid for its communication services. Twilio provides APIs for SMS, voice, and messaging, enabling Airbnb to send notifications, alerts, and support messages to users. SendGrid specializes in email delivery and marketing campaigns, allowing Airbnb to efficiently manage transactional emails, marketing communications, and newsletters. These platforms play a crucial role in enhancing user engagement by ensuring reliable and effective communication channels within the Airbnb ecosystem.

_* Monitoring and Logging_

Airbnb utilizes a robust suite of monitoring and logging tools such as New Relic, Kibana, Sentry, and Datadog. These tools play crucial roles in monitoring system performance, detecting issues in real-time, and providing detailed logs for troubleshooting. New Relic offers performance metrics and application monitoring, while Kibana facilitates log analysis and visualization. Sentry specializes in error tracking and reporting, enhancing Airbnb's ability to quickly identify and resolve issues. Datadog provides comprehensive monitoring across infrastructure and applications, ensuring high reliability and performance of Airbnb's systems through proactive monitoring and responsive incident management.

_* DevOps and Deployment_

In DevOps and deployment, Airbnb uses GitHub for version control, Webpack for frontend asset bundling, and tools like Vagrant and Chef for automated infrastructure management. These tools streamline development processes and ensure efficient deployment of updates and features.

_* Business Tools_

Airbnb uses collaboration tools like Slack, G Suite, Asana, and InVision for efficient communication, project management, and collaboration across teams. Slack fosters real-time communication, G Suite supports document and InVision aids in design collaboration and prototyping. These tools collectively enhance productivity by fostering seamless coordination and effective communication within Airbnb's operations, enabling teams to collaborate efficiently and achieve their goals more effectively.




#### _Describe or make educated guesses about the hardware used to host the app._


1. Cloud Infrastructure:
Cloud Provider: Airbnb uses Amazon Web Services (AWS) for its cloud infrastructure.
Global Distribution: AWS's global network of data centers and Content Delivery Networks (CDNs) helps ensure low latency and high availability for Airbnb's services.

2. Servers and Compute Power:
Virtual Machines (VMs) and Containers: Airbnb uses Amazon EC2 (Elastic Compute Cloud) instances for scalable compute power. They also use Docker containers for application deployment.
Auto-scaling: AWS Auto Scaling is used to automatically adjust the number of EC2 instances based on demand.

3. Databases and Storage:
Relational Databases: Airbnb uses Amazon RDS (Relational Database Service) with PostgreSQL for structured data storage .
NoSQL Databases: They also use Amazon DynamoDB for some of their NoSQL database needs .
Data Warehousing: Airbnb employs Amazon Redshift for data warehousing and large-scale data analysis .
Object Storage: Amazon S3 (Simple Storage Service) is used for storing images, videos, and other media files .

4. Networking:
Load Balancers: Airbnb uses AWS Elastic Load Balancing to distribute incoming traffic across multiple EC2 instances .
CDN: Amazon CloudFront is used as their CDN to deliver content quickly to users around the world .

5. Security:
Firewalls and Security Groups: AWS security groups and network ACLs (Access Control Lists) are used to control network traffic and protect against unauthorized access .
Encryption: Data is encrypted at rest and in transit using AWS Key Management Service (KMS) and other encryption tools .

6. Monitoring and Management:
Monitoring Tools: Airbnb uses Amazon CloudWatch for monitoring the health and performance of their infrastructure .
Logging: Centralized logging is managed through tools like CloudWatch Logs and the ELK stack (Elasticsearch, Logstash, Kibana) .

7. Development and Deployment:
CI/CD Pipelines: Airbnb uses Jenkins for Continuous Integration and Continuous Deployment (CI/CD) to automate testing and deployment of code .
Version Control: GitHub is used for source code management and version control .

8. APIs and Microservices:
Microservices Architecture: Airbnb has adopted a microservices architecture where the application is divided into smaller, loosely coupled services .
API Gateway: They might use AWS API Gateway to manage API traffic, although specific details are not publicly confirmed.


Airbnb's app is hosted on AWS, utilizing a robust, scalable, and secure cloud infrastructure. They leverage a combination of AWS services, such as EC2, S3, RDS, DynamoDB, CloudFront, and CloudWatch, to handle millions of users globally, ensure high availability, and provide a seamless user experience. This setup allows them to scale efficiently, maintain security, and support continuous development and deployment.

These details are based on known information about Airbnb's technology stack, supplemented with educated guesses where specific details are not publicly available.



#### _Describe the interaction of technologies within the app._



Airbnb’s app leverages various technologies to provide a seamless user experience. Users access the app through smartphones, tablets, and desktop browsers, with the frontend built using frameworks like React or React Native for a responsive interface. When a user makes a request, it first hits an API Gateway, which routes it through an AWS Elastic Load Balancer (ELB) to distribute traffic across multiple EC2 instances. The app employs a microservices architecture, with each service (e.g., search, booking, user management) communicating via APIs, typically using REST or gRPC protocols.

Data processing and storage involve multiple systems: structured data (user profiles, bookings, reviews) is handled by Amazon RDS, unstructured data (session caching, dynamic content) by Amazon DynamoDB, and media files (photos, videos) by Amazon S3. Data warehousing is managed by Amazon Redshift, with ETL processes transferring data for reporting and analytics.

Scalability is ensured through AWS Auto Scaling, adjusting the number of EC2 instances based on demand, and Docker containers orchestrated by Kubernetes for efficient resource utilization. Security is maintained with AWS security groups, network ACLs, and data encryption via AWS KMS and TLS.

Monitoring and logging are conducted using Amazon CloudWatch for real-time metrics and the ELK stack (Elasticsearch, Logstash, Kibana) for centralized log management. Continuous integration and deployment are managed by Jenkins and GitHub, facilitating code changes, testing, and deployment.

The interaction flow begins with user requests processed through the API Gateway and ELB, handled by microservices querying databases and retrieving media files from S3. The processed data is returned to the frontend, which displays the information. CloudWatch and ELK monitor performance, auto-scaling adjusts resources, and Jenkins and GitHub manage ongoing development and deployment. This integration ensures efficient traffic handling, quick responses, and robust security.



#### _Describe the way data is structured within the app’s database(s)._

Airbnb’s data infrastructure combines relational, NoSQL, and object storage databases to efficiently manage and utilize vast amounts of data. Relational databases (Amazon RDS with PostgreSQL) store structured data requiring complex queries, such as user profiles, listings, bookings, and reviews. NoSQL databases (Amazon DynamoDB) handle high-speed access to unstructured data, such as session management and activity logs. Media files like images and videos are stored in Amazon S3. Analytical data and large-scale processing are managed through Amazon Redshift, which aggregates data from various sources for reporting and insights. This hybrid approach ensures transactional consistency, quick access to data, and efficient large-scale analytics, providing a seamless user experience.



#### _Identify the entities/tables that are tracked within the app’s database(s)._


Airbnb’s databases track various entities to manage user interactions, listings, transactions, and activities. In relational databases (Amazon RDS with PostgreSQL), key tables include Users (user information), Listings (property details), Bookings (transaction records), and Reviews (user feedback). NoSQL databases (Amazon DynamoDB) manage Sessions (user session data) and Activity Logs (user activities). Object storage (Amazon S3) holds media files for listings and user documents. Data warehousing (Amazon Redshift) aggregates data in tables like Bookings Summary (booking analytics) and User Activity (user interaction summaries). These entities ensure efficient management of user data, property listings, transactions, and analytics.



#### _Identify the relationships and associations between the entities/tables identified in sub-question E._


Users (user_id)
├── Listings (listing_id, host_id)
│   └── Users (host_id) [Many-to-One]
├── Bookings (booking_id, user_id, listing_id)
│   ├── Users (user_id) [Many-to-One]
│   ├── Listings (listing_id) [Many-to-One]
│   └── Reviews (review_id, booking_id) [One-to-One]
├── Reviews (review_id, booking_id)
│   └── Bookings (booking_id) [One-to-One]
├── Sessions (session_id, user_id)
│   └── Users (user_id) [Many-to-One]
└── Activity Logs (log_id, user_id)
    └── Users (user_id) [Many-to-One]



#### _Design an entity relationship diagram (ERD) based on the answers provided to sub-questions E and F. This must represent a relational database model, even if the app itself uses something other than a relational database model._



      +-----------------+
      |      Users      |
      +-----------------+
      | user_id (PK)    |
      +-----------------+
             ^|            ^|                      ^|
             ||            ||                      ||
       +------------+     +------------+           +------------+
       |  Listings  |     |  Bookings  |           | Sessions   |
       +------------+     +------------+           +------------+
       | listing_id (PK)  | booking_id (PK)        | session_id (PK) |
       | host_id (FK)     | user_id (FK)           | user_id (FK) |
       +------------+     | listing_id (FK)        +------------+
             |            +------------+                  |
             |                                          +------------+
             |                                          |Activity Logs|
             |                                          +------------+
             +------------+                             | log_id (PK) |
                          |                             | user_id (FK)|
                          |                             +------------+
                          |
                   +------------+
                   |  Reviews   |
                   +------------+
                   | review_id (PK) |
                   | booking_id (FK)|
                   +------------+







**REFERENCES**

https://intuji.com/airbnb-tech-stack-explained-airbnb-app/

https://stackshare.io/airbnb/airbnb

https://cloud.google.com/learn/postgresql-vs-sql

https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/

https://www.atlassian.com/agile/product-management

