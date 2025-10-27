# 🛠️ Spring Boot Project Setup (Detailed Guide)

A step-by-step guide to creating a clean Spring Boot project from scratch with database configuration, useful dependencies and good practices.

---

## 🧰 1. Prerequisites

Make sure you have the following installed:

- **Java 17+**
  - Check: `java -version`
- **Maven** (or Gradle)
  - Check: `mvn -version`
- **IDE** (e.g., IntelliJ IDEA, VS Code)
- **Git**
- **PostgreSQL / MySQL** (for DB setup)

---

## 🌱 2. Generate Project with Spring Initializr

Go to: [https://start.spring.io](https://start.spring.io)

**Recommended Settings:**

| Setting        | Value                |
|----------------|----------------------|
| Project        | Maven (build tool)   |
| Language       | Java                 |
| Spring Boot    | 3.x.x (latest stable)|
| Group          | `com.example`        |
| Artifact       | `myapp`              |
| Name           | `MyApp`              |
| Packaging      | Jar                  |
| Java Version   | 17                   |

**Add dependencies:**
- Spring Web
- Spring Boot DevTools
- Spring Data JPA
- PostgreSQL Driver (or your DB)
- Spring Security *(optional)*
- Lombok *(optional)*

Click **"Generate"**, download the `.zip`, and extract it.

---

## 🧱 3. Open the Project in Your IDE

- Open the folder in **IntelliJ** or **VS Code**
- Let it auto-import Maven dependencies
- Wait for indexing to finish

---

## 📁 4. Understand Project Structure

```
src/
├── main/
│ ├── java/
│ │ └── com/example/myapp/
│ │ ├── MyAppApplication.java
│ │ ├── config/
│ │ ├── controller/
│ │ ├── dto/
│ │ ├── entity/
│ │ ├── enums/
│ │ ├── exception/
│ │ ├── repository/
│ │ ├── response/
│ │ ├── service/
│ │ └── util/
│ └── resources/
│ ├── application.yml
│ ├── static/
│ ├── templates/
│ └── schema.sql / data.sql (optional)
└── test/
```

---

## ⚙️ 5. Configure Application Properties
Change **_application.properties_** to **_application.yml_** for convenience.
```yaml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/mydb
    username: your_db_user
    password: your_db_password
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        format_sql: true
  application:
    name: myapp
```
 Tip: Use **ddl-auto: create** on first run only. Later use update, validate, or none.

---

## ▶️ 6. Run application

```bash
    ./mvnw spring-boot:run
```

Expected output: **Tomcat started on port(s): 8080**

Visit: http://localhost:8080 → You should see the default Spring Boot error page.

---

## 🛠️ 7. Optional Improvements

- Enable Lombok in IDE (IntelliJ plugin + enable annotation processing)

- Use application-dev.yml, application-prod.yml for profiles

- Add Swagger for API documentation

---

