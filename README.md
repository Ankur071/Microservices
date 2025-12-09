# Spring Boot Microservices – Quiz Application

A backend **Microservices-based application** built using **Spring Boot** that demonstrates real-world distributed system concepts like **Service Discovery, Inter-Service Communication, Load Balancing, and API Gateway**.

This project is inspired by the **Telusko Microservices series** and implements a **Quiz–Question platform** using independent services.

---

## ⚙️ Tech Stack

- Java
- Spring Boot
- Spring Data JPA
- Spring Cloud Netflix (Eureka)
- Spring Cloud OpenFeign
- Spring Cloud Gateway
- MySQL / H2
- REST APIs

---

## 🧩 Microservices Overview

### 1. Question Service
Handles all **question-related operations**.
- Add questions
- Fetch questions by category
- Provide question IDs for quiz creation
- Own database and independent lifecycle

### 2. Quiz Service
Responsible for **quiz management**.
- Create quizzes
- Fetch questions dynamically from Question Service
- Stores quiz data separately

### 3. Eureka Server (Service Registry)
Centralized **service discovery mechanism**.
- Registers all microservices
- Enables dynamic communication
- Eliminates hardcoded service URLs

### 4. API Gateway
Single **entry point** for the client.
- Routes requests to appropriate microservices
- Hides internal service structure
- Acts as a base for security & logging

---

## 🧠 Key Microservices Concepts Used

### ✅ Microservices Architecture
Each service is:
- Independently deployable
- Loosely coupled
- Focused on a single business responsibility
- Backed by its own database

---

### ✅ Service Discovery (Eureka)
Services register themselves with Eureka and communicate using **service names instead of IP/ports**, enabling:
- Scalability
- Fault tolerance
- Dynamic service resolution

---

### ✅ Inter-Service Communication (Feign Client)
Used **OpenFeign** to enable clean and declarative REST calls between microservices.

```java
@FeignClient("QUESTION-SERVICE")
public interface QuestionClient {
    @GetMapping("/question/generate")
    List<Integer> getQuestions();
}
