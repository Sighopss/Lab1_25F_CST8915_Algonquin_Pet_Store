# Algonquin Pet Store - Microservices Project

This project is a microservices-based Pet Store application built as part of CST8915 at Algonquin College.  
It demonstrates how separate services work together to manage products, process orders, and provide a user-facing storefront.

---

## Services Overview

### 1. Product Service
**Role:** Manages all product-related data (create, read, update, delete).  
**Technology:** Node.js with Express  
**Interactions:**  
- Provides REST APIs for the store-front to display products.  
- Supports the order-service by providing product details and availability.  

**Summary:** The product-service is responsible for storing and serving product information to other services and the front-end.

---

### 2. Order Service
**Role:** Receives and processes customer orders.  
**Technology:** Node.js with Express  
**Interactions:**  
- Receives orders from the store-front via HTTP POST requests.  
- Uses RabbitMQ to publish order messages for downstream processing.  
- Checks product availability by interacting with the product-service APIs.  

**Summary:** The order-service ensures orders are received reliably, validated, and sent to the queue for further processing by other services.

---

### 3. Store-Front
**Role:** Provides the user-facing web interface for browsing products and placing orders.  
**Technology:** React (JavaScript)  
**Interactions:**  
- Fetches product data from the product-service via REST APIs.  
- Sends new orders to the order-service via API requests.  
- Updates the UI based on API responses from backend services.  

**Summary:** The store-front is the interface customers interact with. It communicates with backend services to display products and submit orders.

---

## How to Run

### Prerequisites
- Node.js (v18+ recommended)  
- RabbitMQ installed locally or via Docker  

---

### 1. Clone the Repository
```bash
git clone https://github.com/Sighopss/Lab1_25F_CST8915_Algonquin_Pet_Store.git
cd Lab1_25F_CST8915_Algonquin_Pet_Store
rabbitmq-server

Option B: Docker

bash
Copy code
docker run -d --hostname pet-rabbit \
  --name rabbitmq \
  -p 5672:5672 -p 15672:15672 \
  rabbitmq:3-management
RabbitMQ Dashboard: http://localhost:15672 (login: guest / guest)

AMQP URL: amqp://localhost:5672

3. Run Each Service
Product Service

bash
Copy code
cd product-service
npm install
node server.js
Runs at: http://localhost:3001

Order Service

bash
Copy code
cd ../order-service
npm install
node server.js
Runs at: http://localhost:3000

Store-Front

bash
Copy code
cd ../store-front
npm install
npm start
Runs at: http://localhost:3002 (or the port shown in the terminal)

4. Test the System
Open the store-front in your browser at http://localhost:3002

Browse products (retrieved from product-service)

Place an order → order-service receives it and publishes it to RabbitMQ



https://www.youtube.com/watch?v=NfPWB8eDMpY
### How to Submit
- Push your work to a public GitHub repository.
- Include the YouTube demo link and explanations in the `README.md`.
- Submit the link to your GitHub repository as your final lab deliverable in **Brightspace**.
