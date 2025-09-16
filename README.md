Microservice-project
# 📚 Python Library App (Dockerized)

This project is a **Python-based Library Management Application** containerized with **Docker Compose**.  
It demonstrates a microservices architecture with separate services for authentication, book management, borrowing system, and a frontend, all connected through custom Docker networks.

---

## 🚀 Features
- **Database (MySQL)** for storing user, book, and borrowing data.
- **Authentication Service** for managing user logins and sessions.
- **Book Service** for managing available books.
- **Borrow Service** for handling borrow/return transactions.
- **Frontend App Service** to interact with the system.
- Uses **Docker volumes** for persistent database storage.
- Custom **Docker bridge networks** for secure service communication.

---

## 🏗️ Architecture
The system consists of the following services:

1. **Database (`db`)**
   - Runs MySQL
   - Persists data with a named Docker volume
   - Exposes port `3306`

2. **Auth Service (`auth_service`)**
   - Handles user authentication
   - Connects to both `db` and `app` networks
   - Runs on port `5001`

3. **Book Service (`book_service`)**
   - Manages book records
   - Connects with the database
   - Runs on port `5002`

4. **Borrow Service (`borrow_service`)**
   - Manages borrowing and returning of books
   - Connects with the database
   - Runs on port `5003`

5. **Frontend App (`frontend`)**
   - Main entry point for users
   - Connects with `auth_service`, `book_service`, and `borrow_service`
   - Runs on port `5000`

---

## 🗂️ Project Structure

├── docker-compose.yml
├── database/ # MySQL Dockerfile & init scripts
├── auth/ # Auth service code & Dockerfile
├── book/ # Book service code & Dockerfile
├── borrow/ # Borrow service code & Dockerfile
└── frontend/ # Frontend app code & Dockerfile

🔌 Networks

dbnet → Used for communication with the database.

middlenet → Internal communication between backend services.

appnet → Connects the frontend with backend services.

💾 Volumes

db_volume → Persists MySQL data so it is not lost when containers are restarted or removed.
 
