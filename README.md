#  Airbnb Clone Project

This project is a full-stack simulation of the Airbnb platform. It allows users to register, list properties, make bookings, write reviews, and handle payments, all within a secure and scalable web application.


##  Project Goals

- Gain hands-on experience in full-stack web development.
- Understand backend systems using Django and PostgreSQL.
- Practice collaborative workflows and Git/GitHub practices.
- Learn to plan and document a software project professionally.
- Simulate industry-level application design with CI/CD and security measures.


##  Technology Stack

- **Django**: A high-level Python web framework used for building the RESTful API.
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL**: A powerful relational database used for data storage.
- **GraphQL**: Allows for flexible and efficient querying of data.
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis**: Used for caching and session management.
- **Docker**: Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.


##  Team Roles

###  Backend Developer  
Responsible for implementing API endpoints, designing and maintaining database schemas, and writing the core business logic of the application. They ensure that all backend services work efficiently and securely.

###  Database Administrator (DBA)  
Manages the structure and performance of the PostgreSQL database. This includes designing schemas, setting up relationships between tables, managing indexing for performance, and ensuring data integrity and backups.

###  DevOps Engineer  
Handles the deployment, monitoring, and scaling of backend services. Sets up Docker containers, CI/CD pipelines (e.g., GitHub Actions), manages environments, and ensures the application runs smoothly across development and production.

###  QA Engineer  
Ensures backend functionalities are properly tested. This includes writing and running unit tests, integration tests, and performance tests to maintain high reliability and prevent regressions.

## Technology Stack

### 🐍 Django  
A high-level Python web framework used to build the backend of the application. Django simplifies API development, handles routing, authentication, and integrates well with relational databases.

### 🐘 PostgreSQL  
An open-source relational database system that stores structured application data like users, listings, bookings, and reviews. It’s known for reliability, performance, and support for complex queries.

### 🔎 GraphQL  
A query language for APIs that allows clients to request exactly the data they need. It replaces traditional REST calls, reduces over-fetching, and improves frontend performance and flexibility.

### 🐳 Docker  
Used to containerize the application, making it easier to develop, deploy, and run consistently across different environments.

### 💻 HTML, CSS, JavaScript  
The core technologies for building the frontend of the application. They provide structure (HTML), styling (CSS), and interactivity (JavaScript) for the user interface.

### 🔧 Git & GitHub  
Used for version control and collaboration. Git tracks code changes, while GitHub hosts the repository and supports workflows like branching, pull requests, and reviews.

### 🚀 GitHub Actions  
A CI/CD tool that automates testing, building, and deploying the application whenever code changes are pushed to the repository.



## 🗃️ DATABASE DESIGN

This section outlines the core data models (entities) of the Airbnb Clone project and how they relate to each other.

### 🔐 Users
Stores data about people using the platform (both hosts and guests).
- `id`: Unique user ID
- `username`: Account handle
- `email`: Contact email
- `password_hash`: Encrypted password
- `created_at`: Account creation timestamp

**Relationships:**  
A user can host multiple properties and make multiple bookings. A user can also write reviews and process payments.

### 🏠 Properties
Represents homes or apartments listed on the platform.
- `id`: Unique property ID
- `user_id`: Foreign key to the host (owner)
- `title`: Listing title
- `description`: Property details
- `location`: City/country info
- `price_per_night`: Cost of staying per night

**Relationships:**  
A property belongs to one host (user). It can have multiple bookings and reviews.

### 📅 Bookings
Captures reservation details made by guests.
- `id`: Unique booking ID
- `user_id`: Foreign key to the guest
- `property_id`: Foreign key to the booked property
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships:**  
A booking links a guest to a specific property. One property can have many bookings.

### 💳 Payments
Handles financial transactions related to bookings.
- `id`: Unique payment ID
- `booking_id`: Linked booking
- `amount`: Total paid
- `payment_method`: e.g., card, PayPal
- `status`: Completed, Failed, etc.

**Relationships:**  
Each payment is tied to a specific booking.
### ✍️ Reviews
Feedback and ratings left by users after a stay.
- `id`: Unique review ID
- `user_id`: Reviewer
- `property_id`: Reviewed listing
- `rating`: Numerical score (e.g. 1–5)
- `comment`: Optional feedback

**Relationships:**  
Each review belongs to one user and one property.

## 🌐 REST API Endpoints (Planned)

### Users
- `GET /users/` — List all users  
- `POST /users/` — Create a new user  
- `GET /users/{user_id}/` — Get a specific user  
- `PUT /users/{user_id}/` — Update user details  
- `DELETE /users/{user_id}/` — Delete user  

### Properties
- `GET /properties/`  
- `POST /properties/`  
- `GET /properties/{property_id}/`  
- `PUT /properties/{property_id}/`  
- `DELETE /properties/{property_id}/`  

### Bookings
- `GET /bookings/`  
- `POST /bookings/`  
- `GET /bookings/{booking_id}/`  
- `PUT /bookings/{booking_id}/`  
- `DELETE /bookings/{booking_id}/`  

### Payments
- `POST /payments/` — Process a payment  

### Reviews
- `GET /reviews/`  
- `POST /reviews/`  
- `GET /reviews/{review_id}/`  
- `PUT /reviews/{review_id}/`  
- `DELETE /reviews/{review_id}/`  

## 🚀 FEATURE BREAKDOWN

The Airbnb Clone project replicates essential features of a real-world rental platform. Each feature is designed to provide a smooth experience for both property owners and guests.

### 👤 User Management  
Allows users to register, log in, and manage their profiles. This feature ensures secure access control and personalized user experiences based on account roles (e.g., host vs guest).

### 🏘️ Property Management  
Enables hosts to list, update, and delete properties. Property details include location, pricing, images, and descriptions. This forms the core inventory of the platform.

### 📅 Booking System  
Allows guests to search for available properties and make reservations for specific dates. The system manages date availability, booking conflicts, and payment integration.

### 💬 Review System  
After completing a stay, users can leave feedback and ratings. Reviews help build trust and transparency between hosts and guests, improving the platform’s credibility.

### 💵 Payment Integration  
Securely handles payments between guests and hosts using preferred payment methods. Ensures successful booking transactions while logging payment details for transparency.

### 🔐 Authentication & Authorization  
Protects access to sensitive resources using token-based authentication. Ensures users only perform actions permitted by their roles (e.g., a guest can’t delete someone else’s property).
