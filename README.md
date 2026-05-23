# CyberSentinel AI

**AI-Powered Cyber Security Awareness, Phishing Simulation & Threat Detection Platform**

Enterprise-grade cybersecurity SaaS built with Spring Boot 3, Thymeleaf, MySQL, JWT, and intelligent AI engines implemented in Java.

![Stack](https://img.shields.io/badge/Spring%20Boot-3.2.5-6DB33F)
![Java](https://img.shields.io/badge/Java-17-orange)
![MySQL](https://img.shields.io/badge/MySQL-8-blue)

## Features

| Module | Capabilities |
|--------|-------------|
| **Authentication** | JWT, RBAC (Super Admin, Org Admin, Employee), OTP reset, login history, device tracking |
| **Phishing Simulation** | AI email generation, campaign scheduling, open/click/credential tracking, analytics |
| **AI Threat Detection** | URL/Email/File scanner, typosquatting, sentiment analysis, threat intelligence |
| **Awareness Training** | Lessons, quizzes, gamification, leaderboards, adaptive AI recommendations |
| **Risk Scoring** | Human Vulnerability Index, department heatmaps, predictive risk levels |
| **Real-Time Dashboard** | Cyber Pulse meter, Chart.js analytics, radar, live threat feed |
| **AI Chatbot** | Security assistant with FAQ and threat guidance |
| **Incident Reporting** | File uploads, AI classification, admin workflow |
| **Reporting** | PDF and Excel export |

## Tech Stack

- **Backend:** Java 17, Spring Boot, Spring Security, Spring Data JPA, Hibernate, REST APIs, JWT
- **Frontend:** HTML5, CSS3, JavaScript ES6, Thymeleaf, GSAP, AOS, Chart.js, Three.js, Particles.js
- **Database:** MySQL 8
- **Security:** BCrypt, CSRF, XSS headers, rate limiting, audit logs

## Prerequisites

- Java 17+
- Maven 3.8+
- MySQL 8+

## Quick Start

### 1. Create MySQL Database (one-time)

MySQL must be running. From the project root:

```powershell
# Windows (root with no password — default on this machine)
.\scripts\setup-mysql.ps1

# Or manually:
mysql -u root < database\setup.sql
```

This creates:
- Database: `cybersentinel_db`
- User: `cybersentinel` / Password: `CyberSentinel@2024`

Credentials are in `src/main/resources/application.properties`. Override with environment variables if needed:

```powershell
$env:SPRING_DATASOURCE_USERNAME="root"
$env:SPRING_DATASOURCE_PASSWORD=""
```

### 2. Run the Application

```bash
mvn spring-boot:run
```

### 3. Access the Platform

| URL | Description |
|-----|-------------|
| http://localhost:8080 | Landing page |
| http://localhost:8080/login | Login |
| http://localhost:8080/swagger-ui.html | API documentation |
| http://localhost:8080/admin/dashboard | Admin dashboard |
| http://localhost:8080/dashboard | User dashboard |

### Demo Accounts

| Email | Password | Role |
|-------|----------|------|
| superadmin@cybersentinel.io | Admin@123 | Super Admin |
| admin@cybersentinel.io | Admin@123 | Org Admin |
| employee@cybersentinel.io | Admin@123 | Employee |

## Project Structure

```
src/main/java/com/cybersentinel/
├── controller/     # REST + MVC controllers
├── service/          # Business logic
│   └── ai/           # AI engines (phishing, threat, risk, chatbot)
├── repository/       # JPA repositories
├── entity/           # JPA entities
├── dto/              # Request/Response DTOs
├── security/         # JWT filter, rate limiting
├── config/           # Security, WebMvc, data seeding
├── util/             # JWT, OTP, helpers
└── exception/        # Global exception handling

src/main/resources/
├── templates/        # Thymeleaf pages
├── static/css|js/    # Frontend assets
├── schema.sql        # MySQL reference schema
└── application.properties
```

## API Endpoints (Sample)

```
POST /api/auth/login
POST /api/auth/register
POST /api/threats/scan
GET  /api/dashboard/admin
GET  /api/risk/me
POST /api/campaigns
POST /api/chat
POST /api/incidents
GET  /api/reports/pdf
```

## Deployment

### JAR Build

```bash
mvn clean package -DskipTests
java -jar target/cybersentinel-ai-1.0.0.jar
```

### Production Checklist

- Change `cybersentinel.jwt.secret` to a secure 256-bit key
- Use environment variables for DB credentials
- Enable HTTPS behind a reverse proxy (Nginx)
- Set `spring.thymeleaf.cache=true`
- Configure MySQL connection pooling

## AI Engine Architecture

AI features use rule-based and statistical Java algorithms (no external API required):

- **Phishing Generator:** Emotional tone templates, manipulation scoring
- **Threat Detector:** Keyword analysis, URL heuristics, typosquat patterns, threat intel matching
- **Risk Engine:** Click behavior, training completion, incident reporting weights
- **Chatbot:** Intent matching with cybersecurity knowledge base

## License

Educational / Final Year Project — CyberSentinel AI © 2024
