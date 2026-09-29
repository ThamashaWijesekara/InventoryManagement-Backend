# Inventory Management System — Backend

The backend service for the **Inventory Management System (IMS)**, providing secure RESTful APIs for inventory management, stock transactions, warehouse operations, reporting, auditing, authentication, and role-based access control.

The backend manages the application's business logic, database operations, authentication, authorization, and inventory transaction processing.

## 🚀 Core Features

### 🔐 Authentication & Authorization

* JWT-based authentication
* Role-based access control (RBAC)
* Secure API endpoints
* Role-based authorization

### 📦 Master Data Management

* Item Master management
* Item Group management
* Item search and filtering
* Inventory master data management

### 📥 Goods Received Note (GRN)

The GRN module manages goods received into inventory.

Key operations include:

* Create GRN
* Record received items
* Maintain received quantities
* Update inventory based on received stock
* Track GRN transaction details

### 📋 Opening Stock

The Opening Stock module allows the system to initialize inventory quantities.

Features include:

* Record opening stock
* Set initial item quantities
* Maintain opening stock records
* Update inventory balances

### ⚖️ Stock Adjustment

The Stock Adjustment module handles corrections to inventory quantities.

Features include:

* Increase or decrease stock
* Record adjustment reasons
* Maintain adjustment history
* Update inventory balances
* Track adjustment transactions

### 🔄 Stock Transfer

The Stock Transfer module manages movement of inventory between locations or storage areas.

Features include:

* Create stock transfer requests
* Select source and destination
* Specify transfer quantities
* Track transfer status
* Maintain transfer history

### 📥 Stock Transfer Receipt

The Stock Transfer Receipt module handles the receiving side of stock transfers.

Features include:

* View transferred stock
* Receive transferred items
* Confirm received quantities
* Update destination inventory
* Maintain transfer receipt history

### 📤 Stock Issue

The Stock Issue module manages the issuing of inventory from storage.

Features include:

* Create stock issue transactions
* Select items and quantities
* Record issued stock
* Update inventory balances
* Maintain issue history

### 📋 Bin Card

The Bin Card module provides item-level stock movement information.

It can be used to track:

* Opening balance
* Stock receipts
* Stock issues
* Stock adjustments
* Stock transfers
* Running stock balance
* Transaction history

### 📊 Reports

The reporting module provides information about inventory and stock operations.

Reports can include:

* Inventory reports
* Stock movement reports
* GRN-related reports
* Stock issue reports
* Stock transfer reports
* Stock adjustment reports
* Inventory balance information
* Transaction history

### 🔍 Audit

The Audit module provides traceability of important system activities.

It helps track:

* User activities
* Inventory transactions
* Changes to inventory data
* Transaction timestamps
* Relevant system operations

This provides greater accountability and traceability across inventory operations.

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │   Next.js Frontend  │
                    └──────────┬──────────┘
                               │
                         REST API / JWT
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Spring Boot API   │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       Authentication    Business Logic    Audit / Reports
              │                │                │
              └────────────────┼────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │     PostgreSQL      │
                    └─────────────────────┘
```

## 🔄 Inventory Transaction Flow

The system supports the following major inventory flows:

```text
                    STOCK IN
                       │
              ┌────────┴────────┐
              │                 │
             GRN          Opening Stock
              │                 │
              └────────┬────────┘
                       ▼
                  INVENTORY
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
   Adjustment      Transfer         Issue
                       │
                       ▼
              Transfer Receipt
                       │
                       ▼
                  INVENTORY
```

## 🛠️ Technology Stack

* **Java**
* **Spring Boot**
* **Spring Security**
* **JWT**
* **Spring Data JPA**
* **PostgreSQL**
* **Maven**
* **RESTful APIs**

## 📁 Project Structure

```text
backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── ...
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── pom.xml
└── README.md
```

## ⚙️ Setup

### 1. Clone the repository

```bash
git clone <BACKEND_REPOSITORY_URL>
cd <BACKEND_PROJECT_FOLDER>
```

### 2. Configure PostgreSQL

Create the database:

```sql
CREATE DATABASE inventory_management;
```

Configure the database connection in:

```text
src/main/resources/application.properties
```

Example:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/inventory_management
spring.datasource.username=YOUR_USERNAME
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update
```

### 3. Run the application

```bash
mvn spring-boot:run
```

Or:

```bash
mvn clean package
java -jar target/<application-name>.jar
```

The backend normally runs on:

```text
http://localhost:8080
```

## 🔗 Main API Modules

| Module                 | Purpose                                    |
| ---------------------- | ------------------------------------------ |
| Authentication         | Login and user authentication              |
| Item Master            | Manage inventory items                     |
| Item Groups            | Manage item categories/groups              |
| GRN                    | Receive goods into inventory               |
| Opening Stock          | Initialize stock                           |
| Stock Adjustment       | Correct inventory quantities               |
| Stock Transfer         | Transfer stock between locations           |
| Stock Transfer Receipt | Receive transferred stock                  |
| Stock Issue            | Issue stock from inventory                 |
| Bin Card               | Track item-level stock movements           |
| Reports                | Generate inventory and transaction reports |
| Audit                  | Track system and inventory activities      |
| Dashboard              | Provide inventory analytics                |

## 🔐 Security

The application uses JWT-based authentication and role-based authorization.

```text
Login
  ↓
Validate Credentials
  ↓
Generate JWT
  ↓
Frontend Sends JWT
  ↓
Backend Validates JWT
  ↓
Check User Role
  ↓
Allow / Reject Request
```

## 🧪 Testing

Run the backend tests:

```bash
mvn test
```

API testing can be performed using Postman or other REST API testing tools.

## 📦 Build

```bash
mvn clean package
```

The generated JAR file will be located in:

```text
target/
```

## 👨‍💻 Development Team

Developed by **Bugwarts** as a university Software Project at the **University of Moratuwa — Faculty of Information Technology**.
**Inventory Management System — Bugwarts**
