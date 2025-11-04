# E-Commerce Backend

A simple Spring Boot REST API backend for an e-commerce platform with product management, order processing, and multiple payment support.

## What Does This Do?

**API FEATURES:**

✓ Product CRUD operations  
✓ Order management  
✓ Customer management  
✓ Payment processing (COD, Card, bKash, Nagad)  
✓ Admin authentication  
✓ Database persistence with MySQL

---

## What You Need

- **Java 17+** - Download from [https://www.oracle.com/java/technologies/downloads/](https://www.oracle.com/java/technologies/downloads/)
- **Maven 3.8+** - Comes with IntelliJ IDEA
- **MySQL 8.0+** - Download from [https://dev.mysql.com/downloads/](https://dev.mysql.com/downloads/)
- **IntelliJ IDEA Ultimate** (Recommended) or any Java IDE

---

## Quick Setup

### STEP 1: Download

```bash
git clone https://github.com/smrefat02/E-Commerce-Backend-Part.git
cd E-Commerce-Backend-Part
```

### STEP 2: Setup MySQL Database

Open MySQL Workbench or Terminal and run:

```sql
CREATE DATABASE ecommerce_db;
```

### STEP 3: Configure Database

Edit `src/main/resources/application.properties`:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_db
spring.datasource.username=root
spring.datasource.password=your_mysql_password

# JPA Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Server Configuration
server.port=8080
```

### STEP 4: Build Project

```bash
mvn clean install
```

*(Wait 2-3 minutes for dependencies)*

### STEP 5: Run Backend

**Using Maven:**
```bash
mvn spring-boot:run
```

**Using IntelliJ IDEA:**
1. Open project in IntelliJ
2. Wait for Maven dependencies to download
3. Find main application file (with `@SpringBootApplication`)
4. Click green Run button

**Backend starts on:** http://localhost:8080

**Done!**

---

## API Endpoints

### Products
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/products` | Get all products |
| GET | `/api/products/{id}` | Get product by ID |
| POST | `/api/products` | Create new product (Admin) |
| PUT | `/api/products/{id}` | Update product (Admin) |
| DELETE | `/api/products/{id}` | Delete product (Admin) |

### Orders
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/orders` | Get all orders (Admin) |
| GET | `/api/orders/{id}` | Get order by ID |
| POST | `/api/orders` | Create new order |
| PUT | `/api/orders/{id}` | Update order status (Admin) |

### Customers
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/customers` | Get all customers (Admin) |
| GET | `/api/customers/{id}` | Get customer by ID |
| POST | `/api/customers` | Register new customer |

### Payments
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/payments/process` | Process payment |

---

## Technology Stack

- **Spring Boot 3.x** - Backend framework
- **Spring Data JPA** - Database operations
- **MySQL 8.0** - Database
- **Maven** - Build tool
- **Java 17** - Programming language
- **Hibernate** - ORM

---

## Project Structure

```
E-Commerce-Backend-Part/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/ecommerce/
│   │   │       ├── controller/    # REST Controllers
│   │   │       ├── model/         # Entity Classes
│   │   │       ├── repository/    # JPA Repositories
│   │   │       ├── service/       # Business Logic
│   │   │       └── Application.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/                      # Unit Tests
├── pom.xml                        # Maven Dependencies
└── README.md
```

---

## Commands

| Command | What It Does |
|---------|--------------|
| `mvn clean install` | Build project |
| `mvn spring-boot:run` | Run backend |
| `mvn test` | Run tests |
| `mvn clean package` | Create JAR file |

---

## Troubleshooting

**Problem:** Java not found  
**Solution:** Install JDK 17+ from Oracle

**Problem:** MySQL connection error  
**Solution:** Check MySQL service is running and credentials are correct

**Problem:** Port 8080 already in use  
**Solution:** Change port in `application.properties`:
```properties
server.port=8081
```

**Problem:** Maven dependencies not downloading  
**Solution:** Check internet connection, run `mvn clean install -U`

---

## Environment Variables (Optional)

Instead of hardcoding in `application.properties`, use environment variables:

```properties
spring.datasource.url=${DB_URL:jdbc:mysql://localhost:3306/ecommerce_db}
spring.datasource.username=${DB_USERNAME:root}
spring.datasource.password=${DB_PASSWORD:your_password}
```

---

## Payment Integration

Supports multiple payment methods:

✓ **Cash on Delivery (COD)** - No integration needed  
✓ **Credit/Debit Card** - Integration ready  
✓ **bKash** - Bangladesh mobile banking  
✓ **Nagad** - Bangladesh mobile banking

---

## Database Schema

**Products Table:**
- id, name, description, price, category, stock, image_url

**Orders Table:**
- id, customer_id, total_amount, payment_method, status, order_date

**Customers Table:**
- id, name, email, phone, address

**Order Items Table:**
- id, order_id, product_id, quantity, price

---

## Security

- CORS enabled for frontend (port 3000)
- Input validation on all endpoints
- SQL injection prevention with JPA
- Authentication ready for implementation

---

## Deployment

### Deploy to Render.com:

1. Push code to GitHub ✓
2. Go to [render.com](https://render.com)
3. Create new **Web Service**
4. Connect GitHub repository
5. Set build command: `mvn clean package`
6. Set start command: `java -jar target/*.jar`
7. Add environment variables (Database URL, username, password)
8. Deploy!

### Deploy JAR file:

```bash
# Build JAR
mvn clean package

# Run JAR
java -jar target/ecommerce-backend-0.0.1-SNAPSHOT.jar
```

---

## Frontend Integration

This backend works with the **Next.js Frontend**:

**Frontend Repo:** [https://github.com/smrefat02/Ecommerce-Frontend-part](https://github.com/smrefat02/Ecommerce-Frontend-part)


---

## Testing

Run tests:
```bash
mvn test
```

Test API using **Postman** or **cURL**:

```bash
# Test GET all products
curl http://localhost:8080/api/products

# Test POST create order
curl -X POST http://localhost:8080/api/orders \
  -H "Content-Type: application/json" \
  -d '{"customerId": 1, "items": [{"productId": 1, "quantity": 2}]}'
```

---

## Need Help?

- **GitHub:** [https://github.com/smrefat02](https://github.com/smrefat02/E-Commerce-Backend-Part)
- **Email:** [s.m.refat03@gmail.com](mailto:s.m.refat03@gmail.com)
- **Frontend Repo:** [https://github.com/smrefat02/Ecommerce-Frontend-part](https://github.com/smrefat02/Ecommerce-Frontend-part)

---

## License

Open source - Free to use and modify

---

**Built with using Spring Boot**