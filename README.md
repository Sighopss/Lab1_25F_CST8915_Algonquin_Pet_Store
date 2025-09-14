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


2. **Brief Technical Explanation**
   - Spend some time examining the source code of each service:
     - **Order Service (Node.js)**
     - **Product Service (Rust)**
     - **Store Front (Vue.js)**
   - For each service, write a **short technical explanation** (1–2 paragraphs each):
     - What the service is responsible for.
     - Which language/framework it uses.
     - How it interacts with the other services (e.g., RabbitMQ, APIs, or front-end).
   - Keep it simple but show that you understand the role of each service.

3. **GitHub Repository**
   - Create a **GitHub repository** for your submission.
   - Your repository must include:
     - A `README.md` file with:
       - The YouTube video link.
       - Your written technical explanations for the three services.
     - (Optional) Any notes you want to share about setup challenges or learnings.

### How to Submit
- Push your work to a public GitHub repository.
- Include the YouTube demo link and explanations in the `README.md`.
- Submit the link to your GitHub repository as your final lab deliverable in **Brightspace**.
