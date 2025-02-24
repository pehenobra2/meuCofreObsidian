
## 📌 **1. Tecnologias Utilizadas**
- **Spring Boot** (Framework principal)
- **Spring Security** (Autenticação e autorização)
- **Spring Data JPA** (Integração com banco de dados)
- **PostgreSQL** (Banco de dados)
- **JWT (JSON Web Token)** (Autenticação segura)
- **Lombok** (Redução de código boilerplate)
- **MapStruct** (Mapeamento de DTOs)
- **Flyway** (Migrações do banco de dados)
- **Swagger/OpenAPI** (Documentação da API)
- **Spring Boot Actuator** (Monitoramento e métricas)

---

## 📌 **2. Estrutura do Projeto**
O backend será estruturado da seguinte forma:

```
/src/main/java/com/loja/reallidi
│── config/          # Configurações do projeto (segurança, CORS, etc.)
│── controller/      # Controllers da API
│── dto/             # Data Transfer Objects (DTOs)
│── entity/          # Entidades do banco de dados
│── repository/      # Repositórios JPA
│── service/         # Lógica de negócios
│── security/        # Configuração de autenticação e JWT
│── util/            # Utilitários
└── main.java        # Ponto de entrada da aplicação
```

--- 

## 📌3. Configuração do `application.yml`

Para configurar a conexão com o PostgreSQL:

```
server:
  port: 8080

spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/loja_reallidi
    username: postgres
    password: senha_aqui
    driver-class-name: org.postgresql.Driver
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        format_sql: true
  flyway:
    enabled: true
```