# Problem Statement

## 1. Title

**Local Farmers Produce Direct-Selling Marketplace**

**Project Name:** FarmDirect

---

## 2. Domain

**Agriculture / E-Commerce / Marketplace**

FarmDirect is a full-stack marketplace platform designed to connect local farmers directly with consumers and reduce unnecessary intermediaries in the agricultural produce supply chain.

---

## 3. Who is the user?

### 3.1 Farmer

Farmers can:

* Create and manage their profile.
* Add agricultural products such as vegetables, fruits, grains, and other local produce.
* Specify product quantity, unit, price, availability, and description.
* Update available stock.
* View incoming customer orders.
* Accept or reject orders.
* Update order fulfillment status.
* View their sales history and earnings.

### 3.2 Buyer

Buyers can:

* Create and manage their profile.
* Browse locally available agricultural products.
* Search and filter products.
* View farmer and product information.
* Add products to a cart.
* Place orders.
* Track order status.
* View previous orders.
* Provide ratings and reviews after receiving an order.

### 3.3 Admin

Administrators can:

* Manage farmers and buyers.
* Verify farmer accounts.
* Monitor product listings.
* Manage reported products or users.
* Monitor orders and marketplace activity.
* View marketplace statistics.
* Disable fraudulent or inappropriate accounts/listings.

---

## 4. What problem are we solving?

Local farmers often depend on multiple intermediaries to sell their agricultural produce to consumers. This can reduce the farmer's profit margin while consumers may pay higher prices because of additional distribution and intermediary costs.

At the same time, consumers may have difficulty finding fresh produce directly from nearby farmers and understanding where the products originated.

For example, a farmer may have a large quantity of tomatoes ready for sale but may not have an efficient digital channel to reach nearby consumers. A buyer in the same locality may be willing to purchase those tomatoes but may not know which farmers currently have them available.

FarmDirect aims to provide a digital marketplace where verified local farmers can directly list their produce and buyers can discover, order, and track locally available products.

---

## 5. Proposed Solution

FarmDirect will provide a web-based marketplace connecting farmers directly with buyers.

### Farmer Features

* Farmer registration and login.
* Farmer profile management.
* Farmer verification workflow.
* Product listing creation.
* Product editing and removal.
* Stock/availability management.
* Price management.
* Incoming order management.
* Order status updates.
* Sales history.

### Buyer Features

* Buyer registration and login.
* Product browsing.
* Search and filtering.
* Product details.
* Farmer details.
* Shopping cart.
* Order placement.
* Order history.
* Order tracking.
* Product ratings and reviews.

### Admin Features

* Admin authentication.
* Farmer verification.
* User management.
* Product/listing moderation.
* Order monitoring.
* Report management.
* Marketplace statistics dashboard.

### Marketplace Business Logic

The system will implement business rules including:

1. A farmer must be verified before listing products for sale.
2. A product cannot be ordered when sufficient stock is unavailable.
3. Stock must be reduced after a successful order.
4. An order cannot be placed with an empty cart.
5. A buyer can review a product only after completing a corresponding purchase.
6. Farmers can manage only their own product listings and orders.
7. Administrators can manage marketplace-wide data.
8. Product availability must be reflected accurately when stock changes.
9. Order status must follow a controlled workflow.
10. The system must prevent duplicate or inconsistent order processing.

### Future Intelligence / AI Feature

During the enhancement phase, the platform can include an AI/data-driven feature such as:

* Demand forecasting for agricultural products.
* Suggested pricing based on historical marketplace data.
* Product demand trends.
* Farmer inventory recommendations.

The initial MVP will focus on building reliable marketplace functionality before implementing the AI enhancement.

---

## 6. Core Entities / Database Tables

The initial database design will contain at least the following entities:

### 1. User

Stores common authentication and account information.

Example fields:

* id
* name
* email
* password
* phone
* role
* account_status
* created_at

### 2. FarmerProfile

Stores farmer-specific information.

Example fields:

* id
* user_id
* farm_name
* farm_location
* verification_status
* description

### 3. Product

Stores agricultural products listed by farmers.

Example fields:

* id
* farmer_id
* name
* category
* description
* price
* unit
* available_quantity
* status
* created_at

### 4. Cart

Stores a buyer's active shopping cart.

Example fields:

* id
* buyer_id
* created_at
* updated_at

### 5. CartItem

Stores products added to a cart.

Example fields:

* id
* cart_id
* product_id
* quantity
* price_at_addition

### 6. Order

Stores buyer orders.

Example fields:

* id
* buyer_id
* total_amount
* order_status
* delivery_address
* created_at

### 7. OrderItem

Stores individual products belonging to an order.

Example fields:

* id
* order_id
* product_id
* farmer_id
* quantity
* unit_price
* subtotal

### 8. Review

Stores buyer ratings and reviews for purchased products.

Example fields:

* id
* buyer_id
* product_id
* order_id
* rating
* comment
* created_at

### 9. Category

Stores agricultural product categories.

Example fields:

* id
* name
* description

### 10. Notification

Stores important marketplace notifications.

Example fields:

* id
* user_id
* message
* notification_type
* is_read
* created_at

The final database schema may be refined during the architecture and ER-diagram phase.

---

## 7. User Roles & Permissions

### Buyer

Can:

* Register/login.
* Manage own profile.
* Browse products.
* Search/filter products.
* Manage own cart.
* Place orders.
* View own orders.
* Track own orders.
* Review purchased products.

Cannot:

* Create farmer products.
* Modify another buyer's account.
* Modify another user's order.
* Access admin functionality.

### Farmer

Can:

* Register/login.
* Manage own farmer profile.
* Manage own product listings.
* Update own product stock.
* View relevant orders.
* Update fulfillment status.
* View own sales information.

Cannot:

* Modify another farmer's products.
* Access admin functionality.
* Modify buyer accounts.

### Admin

Can:

* Manage users.
* Verify farmers.
* Moderate product listings.
* Monitor orders.
* Manage reported content.
* View marketplace analytics.

---

## 8. Success Criteria

The project will be considered successful when:

1. A new farmer can register and submit a profile for verification.
2. An administrator can verify the farmer.
3. A verified farmer can create an agricultural product listing.
4. A buyer can register and log in securely.
5. A buyer can search and filter available products.
6. A buyer can add products to a cart.
7. A buyer can place an order successfully.
8. The system correctly validates product availability before placing an order.
9. Product stock is updated after a successful order.
10. The farmer can view and process incoming orders.
11. The buyer can track the order status.
12. A buyer can submit a review only for an eligible purchased product.
13. Different user roles receive different permissions.
14. The application provides REST APIs for frontend-backend communication.
15. The application can be deployed to a public cloud environment by Day 41.
16. The application has automated tests for important business logic.
17. The application has a CI/CD pipeline using GitHub Actions.
18. The final enhancement introduces a useful demand forecasting, pricing, or recommendation capability.

---

## 9. Out of Scope

To keep the 60-day project achievable, the following features are initially out of scope:

* Physical warehouse management.
* Large-scale logistics/fleet management.
* International shipping.
* Advanced payment settlement between banks.
* Real-world government subsidy processing.
* Agricultural IoT sensor integration.
* Automated physical delivery robots.
* Full-scale accounting/ERP functionality.
* Complex tax/GST accounting.
* Production-grade financial payment processing.
* Native Android/iOS applications.
* Advanced computer vision for crop disease detection.

A payment sandbox or external notification service may be considered as a third-party integration if it fits the implementation schedule.

---

## 10. Chosen Track

**Java Track**

### Frontend

* React.js
* JavaScript
* Tailwind CSS
* Axios

### Backend

* Java 17
* Spring Boot 3.x
* Spring Security
* JWT Authentication

### Data Layer

* Spring Data JPA
* Hibernate

### Database

* PostgreSQL

### API

* REST API
* OpenAPI / Swagger

### Testing

* JUnit 5

### CI/CD

* GitHub Actions

### Deployment

* Frontend: Vercel
* Backend: Render or Railway
* Database: Cloud-hosted PostgreSQL

### Future AI / Data Feature

* Demand forecasting and/or intelligent product pricing recommendation.

---

## Project Objective

The primary objective of FarmDirect is to build a secure, scalable, and user-friendly marketplace that enables local farmers to sell agricultural produce directly to consumers while providing buyers with a convenient way to discover and purchase locally available products.

The project will demonstrate practical full-stack engineering skills including authentication, role-based authorization, relational database design, REST API development, business logic, frontend integration, automated testing, CI/CD, cloud deployment, and an intelligent enhancement.
