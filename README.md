# Back-end-FINAL-SPRING-BOOT-PROJECT
# Final Project — Spring Boot To-Do List Application

**Student:** Aiana Kutmanova  
**Group:** COMSE-23

---

## 1. Introduction

This is the final version of the *To-Do List Application* backend, developed with Spring Boot.  
The project demonstrates secure authentication, authorization, task management, and clean REST API design.

**Main features:**
- Username/password authentication
- Google social login (OAuth2)
- JWT tokens (access & refresh)
- Refresh tokens stored in the database
- CRUD for task management
- API documentation (Swagger UI)
- Unit and integration tests

---

## 2. System Overview

**Architecture:**  
Layered structure: Controller → Service → Repository → Entity → Database.

**Technologies:**  
- Spring Boot  
- Spring Security  
- Spring Data JPA  
- H2 Database  
- Swagger/OpenAPI  
- JWT  
- OAuth2 (Google login)

---

## 3. Functional Requirements

### 3.1 User Authentication
- Register with username & password.
- Login with username & password.
- Login via Google.
- Generate access & refresh tokens.
- Store refresh tokens securely in the database.

### 3.2 Task Management
- Create, update, delete, and view tasks.
- Each task has a title, description, and status.

### 3.3 API Documentation
- All endpoints are available in Swagger UI (`/swagger-ui.html`).

---

## 4. Non-Functional Requirements

- **Security:** BCrypt passwords, JWT tokens, refresh tokens stored securely.
- **Performance:** Response time under 2 seconds.
- **Maintainability:** Modular layered architecture.
- **Scalability:** Ready for PostgreSQL in production.

---

## 5. Security Design

**SecurityConfig.java:**
- CSRF disabled.
- JWTTokenFilter added to the security filter chain.
- Public access for:
  - `/api/auth/**`
  - `/oauth2/**`
  - `/swagger-ui/**`
  - `/h2-console/**`
- All other endpoints require JWT access token.
- H2 console frame options set to same origin.

**Password encoding:** BCrypt.  
**JWT:** Access token (1 hour), Refresh token (41 days).  
**OAuth2:** Google login integrated via Spring Security.

---

## 6. Use Cases

| Use Case | Actor | Description |
|----------|-------|-------------|
| User Registration | New User | Register with username & password |
| User Login | Registered User | Login with username & password |
| Google Login | User | Login via Google |
| Task CRUD | Authenticated User | Manage tasks |
| Token Refresh | Authenticated User | Request new access token using refresh token |

---

## 7. API Overview

| Endpoint | Method | Description |
|----------|--------|-------------|
| /api/v1/auth/register | POST | User registration |
| /api/v1/auth/login | POST | Username/password login |
| /oauth2/authorization/google | GET | Google login |
| /api/v1/auth/refresh | POST | Get new access token |
| /api/v1/tasks | GET, POST | List or create tasks |
| /api/v1/tasks/{id} | PUT, PATCH, DELETE | Update or delete task |

**Note:** Task endpoints require this header:
Authorization: Bearer <access_token>

yaml
Копировать
Редактировать

---

## 8. Testing Overview

**Unit Tests:**
- UserRepository
- TaskRepository
- DTO mappers

**Integration Tests:**
- Authentication flow
- Task CRUD

**Manual Testing:**
- Swagger UI
- Postman for JWT and refresh token flow

---

## 9. Security Setup (for video presentation)

1. Passwords encrypted with BCrypt.
2. Login generates access & refresh tokens.
3. Refresh token saved in database linked to the user.
4. Access token added to Authorization header for protected requests.
5. Refresh token used when access token expires.
6. Google login available as an alternative.
7. SecurityFilterChain controls access to public and protected endpoints.

---

## 10. Submission Checklist

- ✅ Video uploaded to YouTube (Unlisted)
- ✅ GitHub repository updated
- ✅ README updated with security setup and testing instructions
- ✅ Application demonstrates all required features

---
🔗 [Swagger UI](http://localhost:8080/swagger-ui/index.html)


