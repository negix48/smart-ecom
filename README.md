# Smart E-Commerce Microservices Platform

Smart-Ecom is a **microservices-based e-commerce backend system** designed to demonstrate modern cloud-native architecture using **Docker, Kubernetes, gRPC, serverless functions, and multiple programming languages**.

The system separates core e-commerce functionality into independent services such as **cart management, inventory tracking, payments, and discounts**, allowing scalable and maintainable deployment.

---

# Architecture Overview

The platform is composed of several independent services:

* **Cart Service** – manages shopping cart operations
* **Inventory Service** – tracks product stock levels
* **Payment Service** – processes payments and sends notifications
* **Discount Function** – serverless function for promotional discounts
* **gRPC Cart Service** – high-performance communication layer
* **Nginx Gateway** – API routing and reverse proxy

Each service runs in its own container and communicates through **REST APIs or gRPC**.

---

# Project Structure

```
smart-ecom
│
├── cart-service/
│   ├── index.js
│   └── Dockerfile
│
├── inventory-service/
│   ├── consumer.py
│   ├── Dockerfile
│   ├── pom.xml
│   └── src/main/java/com/example/inventory/
│       ├── InventoryController.java
│       ├── StockRepository.java
│       └── Stock.java
│
├── payment-service/
│   ├── app.py
│   ├── notify.py
│   └── Dockerfile
│
├── grpc-cart/
│   ├── cart.proto
│   ├── server.js
│   └── client.py
│
├── discount-function/
│   ├── handler.js
│   └── serverless.yml
│
├── deploy/
│   ├── docker-compose.yml
│   ├── nginx.conf
│   └── k8s-cart.yaml
│
└── kubectl.exe
```

---

# Services

## Cart Service

Handles operations related to the user’s shopping cart.

**Technology**

* Node.js
* Docker

**Features**

* Add products to cart
* Remove products
* Retrieve cart contents
* Communicate with inventory service

---

## Inventory Service

Manages product stock levels and inventory updates.

**Technology**

* Java (Spring Boot)
* Maven
* Docker

**Key Components**

* `InventoryController.java` – REST API for stock management
* `StockRepository.java` – database access layer
* `Stock.java` – product stock model

---

## Payment Service

Handles payment processing and notifications.

**Technology**

* Python
* Flask
* Docker

**Features**

* Payment validation
* Transaction processing
* Payment notification system

Files:

* `app.py` – main API
* `notify.py` – payment event notifications

---

## gRPC Cart Service

High-performance communication service using **gRPC**.

Files:

* `cart.proto` – service definition
* `server.js` – gRPC server
* `client.py` – gRPC client

Used for efficient service-to-service communication.

---

## Discount Function

Serverless function used for applying **dynamic discount logic**.

Technology:

* Node.js
* Serverless Framework

Files:

```
handler.js
serverless.yml
```

This function can be deployed to cloud platforms like:

* AWS Lambda
* Azure Functions
* Google Cloud Functions

---

# Deployment

## Docker Deployment

Run the entire microservices stack using:

```bash
docker-compose up --build
```

This will start:

* Cart service
* Inventory service
* Payment service
* Nginx gateway

---

# Kubernetes Deployment

The project includes Kubernetes configuration:

```
deploy/k8s-cart.yaml
```

Deploy with:

```bash
kubectl apply -f deploy/k8s-cart.yaml
```

---

# API Gateway

The system uses **Nginx as a reverse proxy**.

Configuration file:

```
deploy/nginx.conf
```

Responsibilities:

* Route requests to services
* Load balancing
* Security layer

---

# Communication Methods

The system uses multiple communication approaches:

| Method          | Usage                               |
| --------------- | ----------------------------------- |
| REST APIs       | External client communication       |
| gRPC            | Internal microservice communication |
| Event messaging | Inventory updates                   |

---

# Technologies Used

| Technology           | Purpose               |
| -------------------- | --------------------- |
| Node.js              | Cart service          |
| Java (Spring Boot)   | Inventory service     |
| Python (Flask)       | Payment service       |
| gRPC                 | Service communication |
| Docker               | Containerization      |
| Kubernetes           | Orchestration         |
| Nginx                | API gateway           |
| Serverless Framework | Discount functions    |

---

# Running Individual Services

### Cart Service

```
cd cart-service
npm install
node index.js
```

### Inventory Service

```
cd inventory-service
mvn spring-boot:run
```

### Payment Service

```
cd payment-service
python app.py
```

---

# Future Improvements

Possible enhancements:

* Authentication and authorization
* API rate limiting
* Distributed tracing
* Centralized logging
* Database integration
* CI/CD pipeline

---

# License

MIT License

---

# Author

Smart-Ecom Microservices Architecture Example
Designed to demonstrate **scalable cloud-native e-commerce systems**.
