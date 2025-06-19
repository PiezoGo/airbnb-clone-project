# AirBnB Clone Project

## Overview

This is a clone of the AirBnB web application. The goal of this project is to build a simplified version of the AirBnB platform, implementing core features such as user authentication, property listings, booking functionality, and more.

## Objectives

- Understand the fundamental concepts behind web application architecture.
- Practice building a full-stack application from scratch.
- Gain experience in collaborative software development using Git and GitHub.
- Understand the roles and responsibilities in a software development team.

## Team Roles

Below are the key roles involved in this project and their responsibilities:

### 1. Backend Developer
Responsible for building and maintaining the core application logic, server-side APIs, and integration with the database. Uses Python (Flask/Django) to manage the business logic of the platform.

### 2. Database Administrator (DBA)
Designs and manages the database schema, ensures data integrity, optimizes queries, and handles migrations and backups. Works closely with backend developers.

### 3. DevOps Engineer
Focuses on deployment, CI/CD pipelines, infrastructure automation, and server monitoring. Ensures that the development and production environments are stable and scalable.

### 4. QA Engineer
Tests the application for bugs, usability, performance, and security. Ensures a reliable and smooth user experience before deployment.


## Technology Stack

- **Django** : A high-level Python web framework used for building the RESTful API.
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL**: A powerful relational database used for data storage.
- **GraphQL**: Allows for flexible and efficient querying of data.
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis**: Used for caching and session management.
- **Docker**: Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.


## Database Design
### key entities required for the projectkey entities required for the project
- **Users**
        FIELDS  -user_id (Primary Key): Unique identifier for each user
                -name: This is the users name
                -email: User's email address
                -password: user's PIN
                -is_host:if the user can list properties

- **Property**
        FIELDS  -property_id (Primary Key): Property's special identifier
                -user_id (Foreign Key): Owner of the property (But still a user can have many properties)
                -PropName - name of the property
                -location: Address or general location of the property
                -price_per_night: Cost to rent per night(of course)
- **booking**
        FIELDS  -booking_id (Primary Key): Unique ID for the booking
                -user_id (Foreign Key):  ID of the individual who has mabe the booking(Guest)
                -property_id (Foreign Key): Id of the property that has been booked
                -check_in: Start date of the booking
                -check_out: End date of the booking
                -total_price: The price hat will be charged for the booking
- **Payments**
        FIELDS  -payment_id (Primary Key): Unique payment record
                -booking_id (Foreign Key): The booking that was made, being paid for
                -user_id (Foreign Key): User making the payment
                -amount: Amount that was paid
                -payment_method: e.g, Card, PayPal, etc.
                -status: Payment status (e.g, successful, pending, failed)
- **Reviews**
        FIELDS  -review_id (Primary Key): Unique identifier for the review
                -user_id (Foreign Key): User who wrote the review
                -property_id (Foreign Key): Property being reviewed
                -rating: Numeric rating (e.g., 1 to 5)
                -comment: Written feedback

   Entity Relationships
A User can own many Properties (One-to-Many)
A User can make many Bookings (One-to-Many)
A Property can have many Bookings (One-to-Many)
A Booking has one Payment (One-to-One)
A Property can have many Reviews, each written by a different User (Many-to-Many via Reviews)
    
## Feature Breakdown

### API Documentation
- The Backend API's will be documented using the OpenAPI standard toensure that there is clarity and ease of intergration of the API's.
- GraphQL will be used to offer reliable query meachanism forinteracting with the backend. 
- CRUD operations on user and property data will be handled by the Django Rest Framework.

### User Authentication
- The admins and users will be able to do operations such as Register new users, authenticate, and manage user profiles.
- Endpoints - /users/, /users/{user_id}/

### Property Management
- The users will be able to do operations such as to Create, update, retrieve, and delete property listings. admins will also be able to assist the users if therebe any malfunctiioning in the system!
- Endpoints: /properties/, /properties/{property_id}/

### Booking System
- The users will be able to do operations such as to  Make, update, and manage bookings, including check-in and check-out details. Admins will also be able to connect the booking details with the database to ensure that there is no clash in the bookings.
- Endpoints: /bookings/, /bookings/{booking_id}/

### Payment Processing
- Here payments and transactions related to booking will be managed. It will organise and facilitate operationsregarding how the user will pay for booking and also connecting to the API's associated to payment.
 - Endpoints: /payments/

### Review System
- Post and manage reviews for properties. The user will be able to access reviews of teir properties and all the processes that it has been involved in.
- Endpoints: /reviews/, /reviews/{review_id}/

### Database Optimizations
- **Indexing**: Implement indexes for fast retrieval of frequently accessed data.
- **Caching**: Use caching strategies to reduce database load and improve performance.


## API Security
Security is essential in the Airbnb Clone project to protect user data, secure financial transactions, and ensure platform trustworthiness. Below are key measures implemented:

### Authentication
Ensures only registered users can access protected resources.
How: JWT tokens, secure password hashing (PBKDF2, bcrypt).
Why: Protects personal data like user profiles and booking info.

### Authorization
Controls what actions users can perform based on roles.
How: Role-Based Access Control (RBAC), custom DRF permissions.
Why: Prevents unauthorized users from modifying or accessing other users' data.

### Data Encryption
Secures data in transit and sensitive credentials.
How: HTTPS (TLS), environment variables for secrets.
Why: Prevents data interception during communication.

### Payment Security
Secures all transactions and payment data.
How: Use of PCI-compliant services like Stripe or PayPal.
Why: Ensures secure handling of financial data and protects against fraud.

### Input Validation
Guards against malicious inputs and data corruption.
How: DRF serializers, Django ORM, HTML escaping.
Why: Prevents SQL injection, XSS, and other injection attacks.

### Monitoring & Logging
Tracks system activity and errors to detect threats.
How: Django logging, optional integration with Sentry.
Why: Enables quick response to abnormal or suspicious behavior.




## CI/CD Pipeline
CI/CD (Continuous Integration and Continuous Deployment) pipelines are automated workflows that help streamline the process of building, testing, and deploying code. In the Airbnb Clone project, CI/CD ensures that changes made to the backend are automatically tested and deployed without manual intervention, enhancing both development speed and deployment reliability.

### Why CI/CD is Important for This Project
 **Automated Testing**: Ensures each code change (e.g., booking system update, new user feature) is automatically tested to prevent bugs.
**Rapid Deployment**: Speeds up the release of new features like payment integration or review system updates.
**Improved Collaboration**: Multiple team members (backend developers, QA, DevOps) can push code without fear of conflicts or breaking the app.
**Reliable Rollbacks**: In case of issues, previous working versions can be restored quickly.

Tools Used for CI/CD
**GitHub Actions**: Automates tasks such as testing and deployment each time code is pushed to the repository.
**Docker**: Packages the backend and its dependencies into containers, ensuring consistent environments across development, staging, and production.
**Docker Compose**: Helps run multi-container services such as Django + PostgreSQL + Redis during integration testing.
**Render / Heroku / AWS / DigitalOcean** (optional): Platforms where the app can be deployed automatically from the GitHub repository.

 
