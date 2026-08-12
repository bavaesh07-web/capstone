# FarmDirect - Functional Requirements

## 1. Project Overview

FarmDirect is a local farmers produce direct-selling marketplace.

The system connects verified local farmers directly with buyers. Farmers can list agricultural products, manage stock, receive orders, and track sales. Buyers can discover products, add them to a cart, place orders, track order status, and review purchased products.

An administrator manages users, farmer verification, product listings, and marketplace activities.

---

# 2. User Roles

The system has three primary roles:

1. Buyer
2. Farmer
3. Admin

---

# 3. Buyer Requirements

## FR-BUYER-001: Buyer Registration

A buyer shall be able to create an account using:

- Name
- Email
- Password
- Phone number

The system shall validate required registration information.

---

## FR-BUYER-002: Buyer Login

A registered buyer shall be able to log in using valid credentials.

The system shall authenticate the buyer and provide access to buyer-specific functionality.

---

## FR-BUYER-003: Buyer Profile

A buyer shall be able to:

- View profile
- Update name
- Update phone number
- Update delivery address

A buyer shall only be able to modify their own profile.

---

## FR-BUYER-004: Browse Products

A buyer shall be able to view available agricultural products.

Product information shall include:

- Product name
- Category
- Price
- Unit
- Available quantity
- Farmer information
- Product description

---

## FR-BUYER-005: Search Products

A buyer shall be able to search for products by name.

Example:

Searching for:

"Tomato"

should return available tomato products.

---

## FR-BUYER-006: Filter Products

A buyer shall be able to filter products based on relevant attributes such as:

- Category
- Price
- Availability
- Farmer/location

---

## FR-BUYER-007: Product Details

A buyer shall be able to view detailed information about a product.

The product details page shall display:

- Product name
- Description
- Price
- Unit
- Available quantity
- Farmer
- Farmer location
- Average rating
- Reviews

---

## FR-BUYER-008: Shopping Cart

A buyer shall be able to:

- Add a product to cart
- Increase quantity
- Decrease quantity
- Remove a product
- View cart total

The system shall prevent adding a quantity greater than available stock.

---

## FR-BUYER-009: Place Order

A buyer shall be able to place an order using products in the cart.

The system shall:

1. Validate the cart.
2. Validate product availability.
3. Calculate the order total.
4. Create the order.
5. Create order items.
6. Reduce product stock.
7. Clear the purchased items from the cart.

---

## FR-BUYER-010: Order History

A buyer shall be able to view their previous orders.

Each order shall display:

- Order ID
- Order date
- Products
- Quantity
- Total amount
- Order status

---

## FR-BUYER-011: Track Order

A buyer shall be able to track the current status of an order.

Initial order statuses may include:

- PLACED
- ACCEPTED
- PROCESSING
- READY_FOR_DELIVERY
- DELIVERED
- CANCELLED

---

## FR-BUYER-012: Product Review

A buyer shall be able to submit a rating and review for a product after completing a valid purchase.

The system shall prevent users from reviewing products that they have not purchased.

---

# 4. Farmer Requirements

## FR-FARMER-001: Farmer Registration

A farmer shall be able to create an account.

The farmer shall provide information such as:

- Name
- Email
- Password
- Phone number
- Farm name
- Farm location

---

## FR-FARMER-002: Farmer Verification

A newly registered farmer shall initially have a pending verification status.

An administrator shall be able to approve or reject the farmer.

Only verified farmers shall be allowed to publish products for sale.

---

## FR-FARMER-003: Farmer Profile

A farmer shall be able to:

- View profile
- Update farm information
- Update contact information
- View verification status

---

## FR-FARMER-004: Create Product

A verified farmer shall be able to create a product listing.

Product information shall include:

- Product name
- Category
- Description
- Price
- Unit
- Available quantity
- Product image

---

## FR-FARMER-005: Update Product

A farmer shall be able to update their own product information.

A farmer shall not be able to modify another farmer's products.

---

## FR-FARMER-006: Delete Product

A farmer shall be able to remove their own product listing when it is no longer available.

---

## FR-FARMER-007: Manage Stock

A farmer shall be able to update the available quantity of their products.

The system shall maintain accurate stock information.

---

## FR-FARMER-008: View Orders

A farmer shall be able to view orders containing their products.

The farmer shall see relevant information such as:

- Order ID
- Buyer information
- Product
- Quantity
- Order status
- Order date

---

## FR-FARMER-009: Update Order Status

A farmer shall be able to update the fulfillment status of applicable orders.

The system shall prevent invalid order-status transitions.

---

## FR-FARMER-010: Sales History

A farmer shall be able to view historical sales information.

The system shall provide:

- Number of orders
- Products sold
- Quantity sold
- Sales amount

---

# 5. Admin Requirements

## FR-ADMIN-001: Admin Login

An administrator shall be able to securely log in.

---

## FR-ADMIN-002: User Management

An administrator shall be able to:

- View users
- View farmers
- View buyers
- Activate accounts
- Deactivate accounts

---

## FR-ADMIN-003: Farmer Verification

An administrator shall be able to:

- View pending farmers
- Approve farmers
- Reject farmers

---

## FR-ADMIN-004: Product Moderation

An administrator shall be able to:

- View product listings
- Remove inappropriate listings
- Disable problematic listings

---

## FR-ADMIN-005: Order Monitoring

An administrator shall be able to view marketplace orders.

The administrator shall be able to monitor:

- Order count
- Order status
- Order value
- Order activity

---

## FR-ADMIN-006: Marketplace Dashboard

The administrator dashboard shall provide marketplace statistics such as:

- Total buyers
- Total farmers
- Verified farmers
- Total products
- Total orders
- Total sales

---

# 6. Authentication Requirements

## FR-AUTH-001

Users shall authenticate using email and password.

## FR-AUTH-002

Passwords shall not be stored as plain text.

## FR-AUTH-003

The system shall use token-based authentication.

## FR-AUTH-004

Authenticated users shall only access functionality permitted for their role.

## FR-AUTH-005

A buyer shall not access farmer-only functionality.

## FR-AUTH-006

A farmer shall not access admin-only functionality.

## FR-AUTH-007

An administrator shall have access to administrative functionality.

---

# 7. Marketplace Business Rules

## BR-001: Farmer Verification

Only verified farmers can publish products.

---

## BR-002: Product Ownership

A farmer can modify only products created by that farmer.

---

## BR-003: Stock Validation

A buyer cannot order more quantity than the available product stock.

---

## BR-004: Empty Cart

A buyer cannot place an order when the cart is empty.

---

## BR-005: Order Stock Update

After successful order creation, the purchased product quantity shall be deducted from available stock.

---

## BR-006: Review Eligibility

A buyer can review a product only if the buyer has completed a valid purchase containing that product.

---

## BR-007: Role Authorization

Users can access only the resources permitted by their assigned role.

---

## BR-008: Order Ownership

A buyer can view only their own orders.

---

## BR-009: Farmer Order Access

A farmer can view only orders containing products belonging to that farmer.

---

## BR-010: Product Availability

Products with zero available quantity shall not be orderable.

---

## BR-011: Order Status

Order status changes shall follow valid business transitions.

---

## BR-012: Account Status

Deactivated users shall not be allowed to perform normal marketplace operations.

---

# 8. Non-Functional Requirements

## NFR-001: Security

The application shall protect user credentials and restrict unauthorized access.

---

## NFR-002: Performance

Common operations such as product browsing and product searching should respond quickly under normal expected load.

---

## NFR-003: Scalability

The backend should be designed so that additional marketplace functionality can be added without major restructuring.

---

## NFR-004: Maintainability

The backend shall use a clear separation between:

- Controller
- Service
- Repository
- Entity

---

## NFR-005: API Design

The backend shall expose REST APIs for communication between the frontend and backend.

---

## NFR-006: Validation

The backend shall validate user input before processing requests.

---

## NFR-007: Error Handling

The application shall return meaningful error responses when operations fail.

---

## NFR-008: Testing

Important business logic shall have automated tests.

---

## NFR-009: Documentation

The project shall contain appropriate technical documentation.

---

## NFR-010: Deployment

The completed application shall be deployable to a cloud environment.

---

# 9. Future AI/Data Enhancement

The initial MVP will not depend on AI.

After the core marketplace is stable, the project may introduce one intelligent feature.

Potential enhancement:

## Demand Forecasting

The system can analyze historical order information to estimate future demand for agricultural products.

Example:

If tomato orders increase consistently during certain weeks, the system could estimate higher future demand.

Possible output:

- Product
- Current stock
- Historical demand
- Predicted demand
- Suggested stock level

Alternative future enhancement:

## Intelligent Price Recommendation

The system could use historical marketplace information to provide a suggested price range for farmers.

---

# 10. Third-Party Integration Scope

A third-party service may be integrated during later development.

Possible integrations include:

- Email notification service
- Cloud image storage
- Payment sandbox
- Maps/location service

The exact integration will be selected after the core architecture is established.

---

# 11. MVP Scope

The Minimum Viable Product shall focus on the following end-to-end flow:

## Flow 1: Farmer Product Listing

```text
Farmer Registration
        ↓
Admin Verification
        ↓
Farmer Login
        ↓
Create Product
        ↓
Product Becomes Available