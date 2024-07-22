# Product Service (Main service)

This repository contains the Product Service, which is built using the following technologies:

- **Spring Boot 3**
- **Java 17**
- **MySQL Server 8**
- **Spring Security**
- **JWT authentication**
- **Docker**
- **Docker Compose**
- **Spring Data ORM**
- **RSA Certificates for Security**

## Overview

The Product Service is responsible for maintaining product data. The main attributes of a product are:

- `Long companyId`
- `String name`
- `String description`
- `Long amount`
- `BigDecimal price`

## Functionality

### Getting Data

- **`GET /products`**
    - Retrieves all products with pagination.

- **`GET /products/{id}`**
    - Retrieves a single product by its ID.

- **`GET /products/company/{companyId}`**
    - Retrieves all products associated with a specific company seller. This endpoint is primarily used by another service.

### Authentication

- We are using Spring Security to secure all endpoints.
- Authentication is required via Basic Auth. Upon successful authentication, a JWT (JSON Web Token) is returned.
- The JWT is valid for 1 hour and is self-signed.
- With the JWT, other services can access all endpoints to retrieve data.

## Containerization

- We are using Docker to containerize the service.
- To start the service, use the standard `docker-compose up --build` command.
    - This will create the necessary network and volumes, create the container, and run the application.

## Setup Instructions

### Prerequisites

- Ensure you have Docker and Docker Compose installed.

### Running the Application

1. Clone the repository:
    ```bash
    git clone <repository-url>
    ```
2. Navigate to the project directory:
    ```bash
    cd product-service
    ```
3. Start the application using Docker Compose:
    ```bash
    docker-compose up --build
    ```

This will set up the network, create the necessary volumes, build the Docker image, and start the container running the application.

## Security

- The application uses RSA certificates for securing communications.
- All endpoints are secured using Spring Security.
- Authentication is handled via Basic Auth, with JWTs issued for subsequent requests.