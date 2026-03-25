# 🛒 E-Commerce Web Application

A full-stack e-commerce web application built with **Spring Boot**, **Thymeleaf**, **Spring Security**, and an **H2 in-memory database**. It supports user registration/login, product browsing, cart management, order placement, and a complete admin dashboard.

---

## 🚀 Tech Stack

| Layer | Technology |
|---|---|
| Backend | Java 17, Spring Boot 3.4.4 |
| Frontend | Thymeleaf, Bootstrap 5, Bootstrap Icons |
| Database | H2 (in-memory) |
| Security | Spring Security, BCrypt |
| Email | Spring Mail (Gmail SMTP) |
| Build Tool | Maven |

---

## ✨ Features

### 👤 User
- Register and log in with email & password
- Browse and search products by name/category
- View product details
- Add to cart and manage cart items
- Checkout and place orders
- View order confirmation
- Forgot password / reset password via email OTP

### 🛠️ Admin
- Secure admin login
- Dashboard with overview
- Add, edit, and delete products
- Manage all orders
- Manage registered users

---

## 📁 Project Structure

```
E-Commerce-main/
├── src/
│   ├── main/
│   │   ├── java/com/e_commerce/e_commerce/
│   │   │   ├── ECommerceApplication.java       # Entry point
│   │   │   ├── EmailSenderService.java          # Email service
│   │   │   ├── MainController.java              # Page routing
│   │   │   ├── Response.java                    # API response model
│   │   │   ├── config/
│   │   │   │   └── SecurityConfig.java          # Spring Security config
│   │   │   ├── controller/api/
│   │   │   │   ├── UserController.java          # User REST API
│   │   │   │   ├── ProductController.java       # Product REST API
│   │   │   │   ├── OrderController.java         # Order REST API
│   │   │   │   ├── AdminLoginController.java    # Admin login
│   │   │   │   └── ForgotPasswordController.java
│   │   │   ├── entity/
│   │   │   │   ├── User.java
│   │   │   │   ├── Product.java
│   │   │   │   ├── Order.java
│   │   │   │   ├── UserOrderItem.java
│   │   │   │   └── VerifyUser.java
│   │   │   └── repository/
│   │   │       ├── UserRepository.java
│   │   │       ├── ProductRepository.java
│   │   │       ├── OrderRepository.java
│   │   │       ├── UserOrderRepository.java
│   │   │       └── VerifyUserRepository.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── templates/                       # Thymeleaf HTML templates
│   │           ├── main-page.html
│   │           ├── user-login-page.html
│   │           ├── user-register-page.html
│   │           ├── user-dashboard-page.html
│   │           ├── product-list-page.html
│   │           ├── product-details-page.html
│   │           ├── cart-page.html
│   │           ├── checkout-page.html
│   │           ├── payment-page.html
│   │           ├── order-confirmation-page.html
│   │           ├── search-page.html
│   │           ├── admin-login-page.html
│   │           ├── admin-dashboard-page.html
│   │           ├── add-product-page.html
│   │           ├── edit-product-page.html
│   │           ├── delete-product-page.html
│   │           ├── manage-orders-page.html
│   │           ├── manage-users-page.html
│   │           └── forgot-password-page.html
└── pom.xml
```

---

## ⚙️ Getting Started

### Prerequisites

- Java 17+
- Maven 3.6+

### Installation & Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/E-Commerce.git
cd E-Commerce

# 2. Build the project
./mvnw clean install

# 3. Run the application
./mvnw spring-boot:run
```

The app will start at: **http://localhost:8080**

---

## 🗄️ Database

This project uses **H2 in-memory database** — no external database setup is needed.

Access the H2 console at: **http://localhost:8080/h2-console**

| Field | Value |
|---|---|
| JDBC URL | `jdbc:h2:mem:ecommerce` |
| Username | `root` |
| Password | *(see application.properties)* |

> ⚠️ Data is reset every time the application restarts (in-memory).

---

## 🔑 API Endpoints

### User API (`/api`)

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/login` | Login with username & password |
| GET | `/api/register` | Register a new user |
| GET | `/api/get-user?email=` | Get user by email |
| GET | `/api/change-password` | Change user password |

### Product API (`/api`)

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/create-product` | Create a new product |
| GET | `/api/edit-product` | Edit an existing product |
| GET | `/api/delete-product?productId=` | Delete a product |
| GET | `/api/all-products` | List all products |
| GET | `/api/search-product-by-id?productId=` | Get product by ID |
| GET | `/api/search-product?name=&category=` | Search products |

### Order API (`/api`)

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/create-order` | Place a new order |
| GET | `/api/get-order?id=` | Get order by ID |
| GET | `/api/get-all-orders` | Get all orders |
| DELETE | `/api/delete-order?id=` | Delete an order |

---

## 🔒 Security

- Passwords are hashed using **BCrypt**
- Routes are protected via **Spring Security**
- Public routes: `/`, `/register`, `/user-register`, `/forgot-password`, `/reset-password`
- All other routes require authentication
- Password reset is handled via **email OTP** using Gmail SMTP

---

## 📧 Email Configuration

Email is configured for password reset. Update `application.properties` with your own Gmail credentials:

```properties
spring.mail.username=your-email@gmail.com
spring.mail.password=your-app-password
```

> 💡 Use a **Gmail App Password** (not your regular password). Enable 2FA on your Google account first, then generate one at [myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords).

---

## 🤝 Contributing

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
