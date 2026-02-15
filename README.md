# Product Service - Spring Boot REST API

This project is a Spring Boot application that provides a REST API for managing products. It was developed as part of Lab Sheet 03 for learning Spring Boot fundamentals, REST API development, and JPA/Hibernate integration.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
- [Database Configuration](#database-configuration)
- [Testing the API](#testing-the-api)
- [Lab Requirements](#lab-requirements)
- [Contributing](#contributing)

## 🎯 Overview

The Product Service is a microservice that handles CRUD (Create, Read, Update, Delete) operations for products. It demonstrates:

- RESTful API design principles
- Spring Boot framework usage
- JPA/Hibernate for data persistence
- H2 in-memory database integration
- Dependency injection and IoC containers

## ✨ Features

- **Create Product**: Add new products to the system
- **Get All Products**: Retrieve a list of all products
- **Get Product by ID**: Fetch specific product details
- **Update Product**: Modify existing product information
- **Delete Product**: Remove products from the system
- **H2 Database Console**: Built-in database management interface

## 🛠️ Technologies Used

- **Java 17**: Programming language
- **Spring Boot 3.5.10**: Application framework
- **Spring Data JPA**: Data persistence layer
- **H2 Database**: In-memory database for development
- **Maven**: Dependency management and build tool
- **Spring Web**: RESTful web services

## 📁 Project Structure

```
product-service/
├── src/
│   ├── main/
│   │   ├── java/com/sliit/product_service/
│   │   │   ├── ProductServiceApplication.java    # Main application class
│   │   │   ├── controller/
│   │   │   │   └── ProductController.java        # REST controller
│   │   │   ├── entity/
│   │   │   │   └── Product.java                  # JPA entity
│   │   │   └── repository/
│   │   │       └── ProductRepository.java        # JPA repository
│   │   └── resources/
│   │       └── application.properties            # Application configuration
│   └── test/
│       └── java/com/sliit/product_service/
│           └── ProductServiceApplicationTests.java
├── pom.xml                                       # Maven configuration
├── mvnw & mvnw.cmd                              # Maven wrapper
└── README.md                                     # This file
```

## 🚀 Getting Started

### Prerequisites

- Java 17 or higher
- Maven 3.6+ (or use the included Maven wrapper)

### Installation & Running

1. **Clone the repository**:

   ```bash
   git clone <repository-url>
   cd product-service
   ```

2. **Run the application** using Maven wrapper:

   ```bash
   # On Windows
   ./mvnw.cmd spring-boot:run

   # On Unix/Linux/Mac
   ./mvnw spring-boot:run
   ```

3. **Alternative**: Run with Maven (if installed):

   ```bash
   mvn spring-boot:run
   ```

4. **Access the application**:
   - API Base URL: `http://localhost:8081`
   - H2 Database Console: `http://localhost:8081/h2-console`

### H2 Database Console Access

- **URL**: `http://localhost:8081/h2-console`
- **JDBC URL**: `jdbc:h2:mem:testdb`
- **Username**: `sa`
- **Password**: (leave empty)

## 🔗 API Endpoints

| Method   | Endpoint         | Description             | Request Body |
| -------- | ---------------- | ----------------------- | ------------ |
| `GET`    | `/products`      | Get all products        | None         |
| `GET`    | `/products/{id}` | Get product by ID       | None         |
| `POST`   | `/products`      | Create new product      | Product JSON |
| `PUT`    | `/products/{id}` | Update existing product | Product JSON |
| `DELETE` | `/products/{id}` | Delete product          | None         |

### Product JSON Structure

```json
{
  "name": "Product Name",
  "price": 99.99
}
```

### Response Format

```json
{
  "id": 1,
  "name": "Sample Product",
  "price": 29.99
}
```

## 🗄️ Database Configuration

The application uses H2 in-memory database with the following configuration:

```properties
# Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver

# JPA Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

# H2 Console
spring.h2.console.enabled=true
```

## 🧪 Testing the API

### Using curl

1. **Create a product**:

   ```bash
   curl -X POST http://localhost:8081/products \
        -H "Content-Type: application/json" \
        -d '{"name": "Laptop", "price": 999.99}'
   ```

2. **Get all products**:

   ```bash
   curl http://localhost:8081/products
   ```

3. **Get product by ID**:

   ```bash
   curl http://localhost:8081/products/1
   ```

4. **Update a product**:

   ```bash
   curl -X PUT http://localhost:8081/products/1 \
        -H "Content-Type: application/json" \
        -d '{"name": "Gaming Laptop", "price": 1299.99}'
   ```

5. **Delete a product**:
   ```bash
   curl -X DELETE http://localhost:8081/products/1
   ```

### Using Postman

1. Import the API endpoints into Postman
2. Set the base URL to `http://localhost:8081`
3. Use the endpoints as described in the API table above

## 📚 Lab Requirements

This project fulfills the following lab objectives:

- ✅ Create a Spring Boot application with proper project structure
- ✅ Implement a REST controller with CRUD operations
- ✅ Create a JPA entity with appropriate annotations
- ✅ Use Spring Data JPA repository for data access
- ✅ Configure H2 database for development
- ✅ Test API endpoints using HTTP client tools
- ✅ Demonstrate dependency injection in Spring Boot
- ✅ Follow RESTful API design principles

### Key Learning Outcomes

- Understanding Spring Boot auto-configuration
- Working with Spring Data JPA repositories
- Creating RESTful web services
- Database integration and configuration
- HTTP methods and status codes
- JSON data manipulation
- Application property management

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## 📝 Notes

- This is a learning project designed for educational purposes
- The H2 database is in-memory, so data will be lost when the application stops
- For production use, consider switching to a persistent database like MySQL or PostgreSQL
- The application runs on port 8081 to avoid conflicts with other services

## 🔧 Troubleshooting

### Common Issues

1. **Port already in use**: Change the port in `application.properties`:

   ```properties
   server.port=8082
   ```

2. **Java version issues**: Ensure you're using Java 17 or higher:

   ```bash
   java -version
   ```

3. **Maven wrapper permissions** (Unix/Linux):
   ```bash
   chmod +x mvnw
   ```

## 📖 Additional Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA Reference](https://spring.io/projects/spring-data-jpa)
- [H2 Database Documentation](http://www.h2database.com/html/main.html)
- [REST API Best Practices](https://restfulapi.net/)

---

**Author**: Hasindu Koshitha Ranaweera  
**Course**: Lab Sheet 03 - Spring Boot Fundamentals  
**Last Updated**: February 2026
