# 🧩 AppBuilder BFF

Este projeto é um **Backend For Frontend (BFF)** desenvolvido em **Java com Spring Boot**, parte integrante da plataforma **Mackleaps**, com o objetivo de integrar e expor serviços do ecossistema **AppBuilder**.

⚙️ Ele atua como camada intermediária entre o frontend e os serviços de backend, centralizando autenticação, controle de acesso, agregação de dados e cache.

---

## 🏛️ Finalidade Institucional

Este BFF foi desenvolvido no contexto da **Universidade Presbiteriana Mackenzie (UPM)**, como parte da arquitetura do **Mackleaps**, facilitando a construção e integração de aplicações via **AppBuilder**.

---

## 🚀 Tecnologias Utilizadas

- Java 17
- Spring Boot
- Spring Security (OAuth2)
- Redis
- Keycloak (OpenID Connect)
- Docker (via `docker-compose`)
- Maven Wrapper

---

## 🧠 Principais Funcionalidades

- 🔐 Integração com **Keycloak** para autenticação OAuth2
- ⚡ Uso de **Redis** como cache ou gerenciador de sessão
- 🎯 Roteamento de requisições de frontend para serviços do backend
- 🔄 Gerenciamento centralizado de sessão e autenticação
- 🔍 Suporte a múltiplos escopos OAuth2: `openid`, `profile`, `email`

---

## 🔧 Configuração Padrão

Arquivo: `application.properties`

```properties
spring.application.name=bff
server.port=8090

# Redis
spring.redis.host=localhost
spring.redis.port=6379

# Keycloak
spring.security.oauth2.client.registration.keycloak.client-id=appbuilder-client
spring.security.oauth2.client.registration.keycloak.authorization-grant-type=authorization_code
spring.security.oauth2.client.registration.keycloak.scope=openid,profile,email
spring.security.oauth2.client.registration.keycloak.redirect-uri=http://localhost:8090/login/oauth2/code/keycloak
spring.security.oauth2.client.provider.keycloak.issuer-uri=http://localhost:8080/keycloak/realms/Appbuilder
```

---

## 🐳 Execução com Docker (Redis e Keycloak)

No diretório `keycloak/`, um `docker-compose.yaml` já está disponível com a estrutura completa.

1. Suba os containers:

```bash
docker-compose up -d
```

2. Em seguida, rode o BFF:

```bash
cd bff
./mvnw spring-boot:run
```

---

## 🌐 Endpoints

- `GET /` — Verificação de status
- `POST /auth/login` — Inicia autenticação com Keycloak
- Rotas adicionais protegidas com OAuth2

---

## 📁 Estrutura do Projeto

```
appbuilder-bff-refactored/
├── bff/
│   ├── src/
│   │   ├── main/java/com/example/bff/
│   │   │   ├── controller/
│   │   │   ├── configuration/
│   │   │   └── entity/
│   │   └── resources/application.properties
│   └── pom.xml
├── keycloak/
│   └── docker-compose.yaml
```

---

## 🧪 Testes

- Implementações básicas em `BffApplicationTests.java`
- Pode ser estendido com JUnit + Testcontainers

---

## 📄 Licença

Distribuído sob a licença MIT ou conforme definido pela UPM.

---

> Projeto desenvolvido por [Alvaro H. Claver](https://github.com/AlvaroHClaver) na **Universidade Presbiteriana Mackenzie**, como parte do ecossistema **Mackleaps**, conectando o AppBuilder ao backend da instituição.
