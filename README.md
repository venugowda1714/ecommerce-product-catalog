# 🛒 ShopEase - E-Commerce Product Catalog

A full-stack e-commerce web application built with **Spring Boot**, **Hibernate/JPA**, **MySQL**, and **Thymeleaf**.

---

## 🧱 Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Frontend   | HTML, CSS, JavaScript, Thymeleaf |
| Backend    | Spring Boot 3.2, Spring Security |
| ORM        | Hibernate (JPA)         |
| Database   | MySQL 8+                |
| API Style  | MVC (REST-ready)        |
| Build Tool | Maven                   |

---

## ✅ Features

### User Features
- 🔐 Register & Login (Spring Security + BCrypt)
- 🛍️ Browse all products with images, prices, categories
- 🔍 Search by name, filter by category & price range
- 📄 Product detail page
- 🛒 Add to Cart, update quantity, remove items (uses `ArrayList`)
- 💳 Place orders (checkout)
- 📦 View order history & order details

### Admin Features
- 📊 Dashboard with stats (products, users, orders)
- ➕ Add / ✏️ Edit / 🚫 Deactivate products
- 👥 View all users, change user roles
- 📋 View all orders, update order status

---

## 🗃️ Database Tables

| Table        | Columns |
|--------------|---------|
| `users`      | id, name, email, password, role |
| `products`   | id, name, description, price, category, stock, image_url, active |
| `cart`       | id, user_id, product_id, quantity |
| `orders`     | id, user_id, total_amount, date, status |
| `order_items`| id, order_id, product_id, quantity, price |

---

## 🚀 Setup & Run

### Prerequisites
- Java 17+
- Maven 3.8+
- MySQL 8+

### Steps

1. **Clone / Extract the project**

2. **Configure MySQL** in `src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_db?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
   spring.datasource.username=root
   spring.datasource.password=YOUR_PASSWORD
   ```

3. **Build & Run**:
   ```bash
   cd ecommerce
   mvn spring-boot:run
   ```

4. **Open browser**: [http://localhost:8080](http://localhost:8080)

---

## 🔑 Default Credentials (auto-seeded)

| Role  | Email                   | Password  |
|-------|-------------------------|-----------|
| Admin | admin@ecommerce.com     | admin123  |
| User  | user@ecommerce.com      | user123   |

---

## 📁 Project Structure

```
src/
├── main/
│   ├── java/com/ecommerce/
│   │   ├── EcommerceApplication.java
│   │   ├── config/
│   │   │   ├── SecurityConfig.java
│   │   │   └── DataInitializer.java
│   │   ├── controller/
│   │   │   ├── HomeController.java
│   │   │   ├── AuthController.java
│   │   │   ├── ProductController.java
│   │   │   ├── CartController.java
│   │   │   ├── OrderController.java
│   │   │   └── AdminController.java
│   │   ├── dto/
│   │   │   └── RegisterDTO.java
│   │   ├── model/
│   │   │   ├── User.java
│   │   │   ├── Product.java
│   │   │   ├── CartItem.java
│   │   │   ├── Order.java
│   │   │   └── OrderItem.java
│   │   ├── repository/
│   │   │   ├── UserRepository.java
│   │   │   ├── ProductRepository.java
│   │   │   ├── CartRepository.java
│   │   │   ├── OrderRepository.java
│   │   │   └── OrderItemRepository.java
│   │   └── service/
│   │       ├── CustomUserDetailsService.java
│   │       ├── UserService.java
│   │       ├── ProductService.java
│   │       ├── CartService.java
│   │       └── OrderService.java
│   └── resources/
│       ├── application.properties
│       ├── static/
│       │   ├── css/style.css
│       │   └── js/main.js
│       └── templates/
│           ├── layout.html
│           ├── auth/
│           │   ├── login.html
│           │   └── register.html
│           ├── user/
│           │   ├── products.html
│           │   ├── product-detail.html
│           │   ├── cart.html
│           │   ├── orders.html
│           │   └── order-detail.html
│           └── admin/
│               ├── dashboard.html
│               ├── products.html
│               ├── product-form.html
│               ├── users.html
│               └── orders.html
└── schema.sql (reference only)
```

---

## 📝 Resume Highlights

- **Spring Boot 3.2** full-stack MVC web application
- **Hibernate JPA** with custom JPQL search queries
- **Spring Security** with BCrypt password hashing and role-based access control (USER / ADMIN)
- **Session management** via Spring Security's session registry
- **ArrayList** used for in-memory cart operations (`CartService.getCartItems()`)
- **Soft delete** for products (deactivate without data loss)
- **MySQL** database with 5 relational tables and foreign key constraints
- Responsive UI with Thymeleaf templates and FontAwesome icons
