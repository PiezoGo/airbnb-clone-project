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
        FIELDS - Name- This is the users name
                -booking_id - These are the booking_id that the user has curretly made or have been offered to them
                -user_id - Users special identifier
                -Password - user's PIN
                -property_id - This is a special identifier for the property that the user currently owns(Single user can own multiple properties)
                -PropName - Name of the property that the user currently owns
- **Property**
        FIELDS  -PropName - name of the property
                -booking_id - booking_id made to the property 
                -property_id- Property's special identifier
                -user_id - Owner of the property (But still a user can have many properties)
- **booking_id**
        FIELDS  -property_id - Id of the property that has been booked 
                -user_id - ID of the individual who has mabe the booking
                -Price - The price hat will be charged for the booking
                -booking_id
- **Payments**
        FIELDS  -booking_id - The booking that was made
                -Price - The price that was charged 
                -user_id - ID of the individual to be charged 
                -Password - password of the individualto be charged
- **Reviews**
        FIELDS  -booking_id
                -review_id-
                -user_id
                -Password
                -Price
                -PropName
                -property_id
    