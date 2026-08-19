# MIDRA - Personal Finance Platform

Este é o repositório do **MIDRA**, uma plataforma completa de gestão financeira pessoal desenvolvida com Spring Boot 3 (Java 21) no Backend e React (Vite + TailwindCSS) no Frontend.

## 📌 Status Atual do Projeto (Handover)

Nesta etapa inicial (MVP Fase 1), nós definimos toda a modelagem e arquitetura base do sistema.

### O que já está feito:
- **Banco de Dados (Docker):** Arquivo `docker-compose.yml` configurado para subir o PostgreSQL 16 na porta `5432`.
- **Frontend (React + Vite):** A pasta `/frontend` já foi inicializada, com TailwindCSS, PostCSS, React Router e Recharts instalados e pré-configurados.
- **Backend (Spring Boot):**
  - Projeto estruturado como um **Monólito Modular** (`com.midra.api.auth`, `.users`, `.accounts`, `.categories`, `.transactions`).
  - Dependências essenciais no `pom.xml` (Web, Data JPA, Postgres, Security, JWT, Lombok, Flyway).
  - Entidades de Domínio e Repositórios (Spring Data JPA) das 4 tabelas core mapeadas e finalizadas com Auditoria JPA (campos automáticos de criação/atualização).
  - **Migrations (Flyway):** O script de criação das tabelas no banco de dados já está escrito e será executado automaticamente na subida da aplicação (`V1__init_schema.sql`).

## 🚀 Próximos Passos (Para a Colaboradora)

A base do sistema já está sólida e conectada ao banco. O próximo passo foca nas **Regras de Negócio e APIs REST**.

Recomendamos seguir esta ordem para a continuidade:

1. **Módulo de Usuários e Autenticação (Auth):**
   - Criar os DTOs de `RegisterRequest`, `LoginRequest` e `AuthResponse`.
   - Criar o `AuthService` para criptografar senhas (BCrypt) e o `UserService` para salvar o usuário.
   - Configurar o Spring Security e criar o gerador/validador de Token JWT.
   - Criar o `AuthController` expondo `/api/auth/register` e `/api/auth/login`.

2. **Módulo de Contas (Accounts):**
   - Criar DTOs para Account.
   - Criar o `AccountService` com a regra de criação e os CRUDs básicos, garantindo que uma conta sempre pertence ao usuário autenticado pelo Token JWT.
   - Criar o `AccountController`.

3. **Módulo de Transações e Categorias:**
   - Criar a lógica pesada de Transações (`TransactionService`), garantindo que ao salvar uma transação, o `balance` da conta associada seja automaticamente atualizado.
   - Tratar a lógica da "Transferência" (criar 2 transações linkadas no banco).

## 🛠️ Como rodar o projeto localmente

1. Suba o banco de dados via Docker:
   ```bash
   docker-compose up -d
   ```
2. Rode o backend Java através da classe `MidraApplication.java` na sua IDE (rodará na porta 8080).
3. Rode o frontend React (em um terminal separado):
   ```bash
   cd frontend
   npm run dev
   ```
