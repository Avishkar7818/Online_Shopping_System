# Online Shopping Application - Java JDBC

## 1. Project Information
This is a console-based **Online Shopping Application** built with **Java** and **JDBC**. It simulates an e-commerce environment where admins can manage products and customers can browse products, add to cart, and place orders. The system connects to a MySQL database for persistent storage.

**Objective:**  
Design and implement the system using Java that demonstrates Object-Oriented Programming (OOP) concepts, including **inheritance**, **polymorphism**, and **collections**. The application features a menu-driven console interface for both customers and admins, sharing a common service layer to ensure data consistency across operations.

**Features:**
- Admin login to manage product catalog (add, update, remove products).
- Customer registration and login.
- View products, add to cart, place orders.
- View order history.
- Update order statuses: "Completed," "Delivered," or "Cancelled".
- Real-time stock adjustments and order management.
- Database integration via JDBC.

**Technologies Used:**
- Java 8+
- JDBC (Java Database Connectivity)
- MySQL
- Console-based UI

---

## 2. Entities and Attributes

### 1. Product
**Attributes:**
- productId: Unique identifier for the product.
- name: Name of the product.
- price: Price of the product.
- stockQuantity: Available stock quantity of the product.
**Relationships:**
- Many-to-Many with Order.
- Many-to-Many with ShoppingCart.

### 2. User (Base Class)
**Attributes:**
- userId: Unique identifier for the user.
- username: Username of the user.
- email: Email address of the user.
**Relationships:**
- Inherited by Customer and Admin.

### 3. Customer (Inherits from User)
**Attributes:**
- address: Address of the customer.
- shoppingCart: The customer's shopping cart.
- orders: List of orders placed by the customer.
**Relationships:**
- One-to-One with ShoppingCart.
- One-to-Many with Order.

### 4. Admin (Inherits from User)
**Relationships:**
- Manages multiple Products.

### 5. Order
**Attributes:**
- orderId: Unique identifier for the order.
- customer: The customer who placed the order.
- products: List of ProductQuantityPair.
- status: Status of the order.
**Relationships:**
- Many-to-One with Customer.
- Many-to-Many with Product.

### 6. ShoppingCart
**Attributes:**
- items: Map of Product to quantity.
**Relationships:**
- Many-to-One with Customer.
- Many-to-Many with Product.

---

## 3. File Descriptions

**Package: `com.tns.onlineshopping.application`**
- `OnlineShopping.java` → Main class with `main()` method. Displays menus and controls the application flow.

**Package: `com.tns.onlineshopping.entities`**
- `Admin.java` → Entity class representing admin users.
- `Customer.java` → Entity class representing customers.
- `Order.java` → Entity class representing orders.
- `Product.java` → Entity class representing products.
- `ProductQuantityPair.java` → Helper class to store product and quantity.
- `ShoppingCart.java` → Represents a shopping cart for a customer.
- `User.java` → Base class for `Admin` and `Customer`.

**Package: `com.tns.onlineshopping.services`**
- `AdminService.java` → Handles admin operations like adding/removing products.
- `CustomerService.java` → Handles customer operations like browsing products, managing cart, placing orders.
- `OrderService.java` → Handles order placement and retrieval.
- `ProductService.java` → Handles product listing, adding, updating, and deleting.

**Package: `com.tns.onlineshopping.util`**
- `DBConnection.java` → Utility class for establishing database connections.

---

## 4. How to Run the Code

### Prerequisites
1. Install **Java JDK 8+**
2. Install **MySQL Server**
3. Download **MySQL JDBC Driver** (`mysql-connector-j-8.x.x.jar`)

### Steps
1. Create MySQL database and tables using the provided SQL script.
2. Place the JDBC driver JAR inside a `lib/` folder in your project.
3. Update `DBConnection.java` with your MySQL credentials.
4. Compile:
   ```bash
   javac -cp "lib/mysql-connector-j-8.x.x.jar" -d bin src/com/tns/onlineshopping/**/*.java
   ```
5. Run:
   ```bash
   java -cp "bin;lib/mysql-connector-j-8.x.x.jar" com.tns.onlineshopping.application.OnlineShopping
   ```
   *(On Mac/Linux, replace `;` with `:` in the `-cp` path)*

---

## 5. Suggestions
- Convert to a **Maven project** for easier dependency management.
- Add **exception handling** for more robust user input.
- Extend features with product search, payment simulation, and discount codes.
- Migrate to a GUI (JavaFX/Swing) or a web application.

---
**Author:** Saurabh Gunjal

