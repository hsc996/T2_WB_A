Workbook_PartA

##### **Q1. Describe the architecture of a typical API project, such as a Flask application.**


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




##### **Q2. Identify a database commonly used in an API project (such as a Flask application) and discuss the pros and cons of this database.**


PostgreSQL is an advanced, open-source relational database management system (RDBMS) commonly used in an API project such as a Flask application. It supports SQL for relational queries and JSON for non-relational queries, offering a powerful and flexible platform for a wide range of applications. As a fully ACID-compliant database, PostgreSQL ensures reliable transactions and maintains data integrity. It also boasts advanced features such as complex query capabilities, indexing, full-text search, and support for custom data types and functions.


**Pros:**


_1. ACID Compliance:_ PostgreSQL is fully ACID-compliant, ensuring data integrity, as well as reliable transactions. This is crucial for applications requiring consistent and accurate data.


_2. Advanced Features:_ PostgreSQL provides advanced features like complex queries, foreign keys, triggers, views, and stored procedures, in order to enable sophisticated data manipulation and the implementation of business logic directly within the database.


_3. Extensibility:_ PostgreSQL's is a highly extensibile system, offering a myriad of customisable options to the user to meet their specific application needs.Users can define their own data types, index types, and functional languages. PostgreSQL is a packaging tool for database add-ons, supporting languages like PL/pgSQL, PL/Python, Java, and even JavaScript: It allows developers to write and run functions in various languages within the database by exposing an interface for language integration. This interface enables seamless execution of functions regardless of their underlying language, thus simplifying complexity by providing an extensible language function. This capability allows larger companies to develop functional packages tailored to their specific business domains.

_4. Performance_

PostgreSQL supports complex queries, foreign keys, triggers, views, and stored procedures, enabling sophisticated data manipulation and business logic directly within the database. Its powerful indexing and optimization techniques make it suitable for managing large datasets and high-concurrency environments efficiently. Additionally, it uses Multi-Version Concurrency Control (MVCC) to handle concurrent processing and maintain high transaction rates with minimal risk of deadlocks (https://cloud.google.com/learn/postgresql-vs-sql#section-8). Additionally, it ensures high availability and provides server failure recovery mechanisms.

_5. Open Source_

PostgreSQL being open source is highly beneficial as it is cost-effective, reducing database management expenses since it is free to use. It enjoys strong community support, with a large and active developer base ensuring rapid bug fixes, regular updates, and abundant resources. The open-source nature allows for high flexibility and customization, enabling users to modify the source code to meet specific needs. Additionally, it offers transparency for inspecting code security and reliability, fosters innovation through global collaboration, and avoids vendor lock-in, providing freedom in choosing support and services.

_6. Security_

PostgreSQL has established international recognition in regards to it's security. While it has internally integrated security features such as data encryption, SSL certificates, and advanced authentication methods, it also has secuirty extension available to further enhance the security of the application (https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/). Regarding parameter security, PostgreSQL offers configurations at the operating system level to secure the environment surrounding your database. For application security, it provides user privilege management by categorizing accounts into roles such as read-only, read/write, and others. Beyond granting specific permissions to users, you can also establish ongoing permissions for various actions or resources (https://www.aalpha.net/blog/pros-and-cons-of-using-postgresql-for-application-development/).

_7. Transactions_



**Cons:**



_1. Complexity:_ Due to its advanced features and extensive configuration options, PostgreSQL can be more complex to set up and maintain compared to simpler databases like SQLite.

_2. Resource Intensive:_

PostgreSQL can be more resource-intensive, requiring more memory and CPU, which might be a concern for smaller applications or those running on limited hardware.

_4. Learning Curve_

The richness of features means there is a steeper learning curve for new users or developers who are not familiar with its capabilities and configuration options.
- Installation can be difficult for beginners

_Scaling Write Operations_

While PostgreSQL handles read operations very efficiently, scaling write operations across multiple servers can be challenging and may require additional tools and configurations (e.g., sharding, replication).

- Slower performance compared to other RDBMS like SQL Server and MySQL
- Stronger focus on compatibility, speed improvements require extra work

Postgres Cons:
* Somewhat slow for inserts and updates when compared to mysql ( due to
  pgsql having to check for triggers and such )
* Some SELECT queries may be slower than their counterparts in MySQL.

Use in Flask Applications
In a Flask application, PostgreSQL can be integrated using libraries like psycopg2 for direct database interactions or SQLAlchemy for ORM (Object-Relational Mapping) capabilities. This combination provides a powerful and flexible backend for API projects, leveraging PostgreSQL’s robustness and Flask’s simplicity.



##### _Q3. Discuss an implementation of an Agile project management methodology for an API project._




##### _Q4. Provide an overview and description of a standard source control process for an API project._




##### _Q5. Provide an overview and description of a standard testing process for an API project._




##### _Q6. Explain the three principles of information system security._




##### _Q7. Provide an overview of what would need to be done within an API project to implement at least one of the principles explained in Question 6._




##### _Q8. Explain the legal obligations that developers of a social media website or social media application would have in regards to handling user data, with reference to any applicable laws or acts. (12 PTS)_




##### _Q9. Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure._




##### _Q10. Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database._





##### _Q11. Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database._




##### _Q12. Conduct research into a web application (app) and answer each of the following sub-questions: (42 PTS)_



##### _List and describe the software (tech stack) used by the app._

_1. Programming languages_:

**Frontend:** JavaScript and React (JS UI library)
JavaScript is a widely used programming language for creating dynamic user interfaces and building responsive web applications.
React, a JavaScript library, enhances the development of reusable UI components. A flexible and efficient solution for building sleek user interfaces.

**Backend:** Java, Ruby on Rails (framework)
Java is a robust backend language known for its scalability and performance.
Ruby on Rails, a web application framework, provides a rapid development environment. Known for its impressive capabilities that speed up development and, as a result, reduce costs and TTM (time to market).


_2. Databases:_ MySQL, Amazon RDS
- MySQL handles data storage, and Amazon RDS offers managed database services in the cloud.
- (Cloud database) -- Amazon keeps its data in an Amazon’s cloud relational database. Earlier, Amazon used MySQL databases, but switched to Amazon RDS to simplify administration and other routine tasks.


_3. Cloud services:_ Amazon S3, EC2, CloudFront
**Cloud Storage:** Amazon S3 for scalable object storage. To store user data including millions of user pictures, Amazon resorts to Amazon services.
**Cloud hosting:** Amazon EC2 for virtual servers, and CloudFront for content delivery. Amazon EC2 is an efficient tool that distributes the incoming traffic and doesn’t let Airbnb’s system go down during sudden traffic spikes or any unexpected traffic fluctuations.


_4. Webserver:_ Nginx
Nginx is a powerful HTTP and proxy server that speeds up content delivery, ensures Airbnb’s security and scalability. This server is popular among other leading tech companies such as Netflix, Instagram and Zappos use NGinx too.


_5. Caching and key-value storage:_
- Redis. Redis provides a scalable cache infrastructure and a key/value database.


_8. Query Tool: Airpal_
Airpal is Airbnb's SQL-based query tool for data exploration.

_9. Analytics and Utility Tools:_ Google Analytics, Mixpanel
Tools like Google Analytics and Mixpanel provide insights into user behavior and website performance.

_10. Communication and Messaging Tools:_ Twilio, SendGrid
Twilio and SendGrid handle communication, ensuring seamless messaging services.

_11. Monitoring and Logging:_ New Relic, Kibana, Sentry, Datadog
Monitoring tools like New Relic and Datadog, along with logging tools like Kibana and Sentry, ensure system reliability.

_12. DevOps and Deployment:_
 GitHub, Webpack, Vagrant, Chef - GitHub for version control, Webpack for bundling, and tools like Vagrant and Chef for DevOps and deployment.

_13. Business Tools:_ Slack, G Suite, Asana, InVision - Collaboration tools like Slack, G Suite, Asana, and InVision streamline communication and project management.




##### _Describe or make educated guesses about the hardware used to host the app._



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



##### _Describe the interaction of technologies within the app._



Airbnb’s app leverages various technologies to provide a seamless user experience. Users access the app through smartphones, tablets, and desktop browsers, with the frontend built using frameworks like React or React Native for a responsive interface. When a user makes a request, it first hits an API Gateway, which routes it through an AWS Elastic Load Balancer (ELB) to distribute traffic across multiple EC2 instances. The app employs a microservices architecture, with each service (e.g., search, booking, user management) communicating via APIs, typically using REST or gRPC protocols.

Data processing and storage involve multiple systems: structured data (user profiles, bookings, reviews) is handled by Amazon RDS, unstructured data (session caching, dynamic content) by Amazon DynamoDB, and media files (photos, videos) by Amazon S3. Data warehousing is managed by Amazon Redshift, with ETL processes transferring data for reporting and analytics.

Scalability is ensured through AWS Auto Scaling, adjusting the number of EC2 instances based on demand, and Docker containers orchestrated by Kubernetes for efficient resource utilization. Security is maintained with AWS security groups, network ACLs, and data encryption via AWS KMS and TLS.

Monitoring and logging are conducted using Amazon CloudWatch for real-time metrics and the ELK stack (Elasticsearch, Logstash, Kibana) for centralized log management. Continuous integration and deployment are managed by Jenkins and GitHub, facilitating code changes, testing, and deployment.

The interaction flow begins with user requests processed through the API Gateway and ELB, handled by microservices querying databases and retrieving media files from S3. The processed data is returned to the frontend, which displays the information. CloudWatch and ELK monitor performance, auto-scaling adjusts resources, and Jenkins and GitHub manage ongoing development and deployment. This integration ensures efficient traffic handling, quick responses, and robust security.



##### _Describe the way data is structured within the app’s database(s)._

Airbnb’s data infrastructure combines relational, NoSQL, and object storage databases to efficiently manage and utilize vast amounts of data. Relational databases (Amazon RDS with PostgreSQL) store structured data requiring complex queries, such as user profiles, listings, bookings, and reviews. NoSQL databases (Amazon DynamoDB) handle high-speed access to unstructured data, such as session management and activity logs. Media files like images and videos are stored in Amazon S3. Analytical data and large-scale processing are managed through Amazon Redshift, which aggregates data from various sources for reporting and insights. This hybrid approach ensures transactional consistency, quick access to data, and efficient large-scale analytics, providing a seamless user experience.



##### _Identify the entities/tables that are tracked within the app’s database(s)._


Airbnb’s databases track various entities to manage user interactions, listings, transactions, and activities. In relational databases (Amazon RDS with PostgreSQL), key tables include Users (user information), Listings (property details), Bookings (transaction records), and Reviews (user feedback). NoSQL databases (Amazon DynamoDB) manage Sessions (user session data) and Activity Logs (user activities). Object storage (Amazon S3) holds media files for listings and user documents. Data warehousing (Amazon Redshift) aggregates data in tables like Bookings Summary (booking analytics) and User Activity (user interaction summaries). These entities ensure efficient management of user data, property listings, transactions, and analytics.



##### _Identify the relationships and associations between the entities/tables identified in sub-question E._


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



##### _Design an entity relationship diagram (ERD) based on the answers provided to sub-questions E and F. This must represent a relational database model, even if the app itself uses something other than a relational database model._

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

