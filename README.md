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
