# Simple User Management System
Este projeto foi desenvolvido com o objetivo de estudo e prática de desenvolvimento backend moderno utilizando Java e arquitetura baseada em microsserviços.

---

### Sobre o Projeto

O **Simple User Management System** é um sistema para gerenciamento de usuários, contendo funcionalidades de cadastro, autenticação, painel administrativo e análise de dados.

O projeto foi estruturado para simular um ambiente real de desenvolvimento, utilizando tecnologias amplamente adotadas no mercado e metodologia de desenvolvimento seguindo fortes regras e padrões.

---

## Objetivos de Aprendizado

* Praticar desenvolvimento com Spring Boot (Java 21)
* Implementar um sistema CRUD completo
* Desenvolver autenticação com segurança (hash de senha)
* Trabalhar com banco de dados relacional usando PostgreSQL
* Utilizar cache com Redis
* Aplicar containerização com Docker
* Orquestrar serviços com Docker Compose
* Configurar balanceamento de carga com Nginx

---

## Funcionalidades

### CRUD de Usuários

* Cadastro de usuários
* Listagem de usuários
* Atualização de dados
* Remoção de usuários
* Busca por ID e nome

---

### Autenticação

* Login com email e senha
* Armazenamento seguro de senha (hash SHA-256)
* Controle de acesso por nível:
  * Gerente

---

### Painel Administrativo

* Histórico de cadastros
* Quantidade de usuários por dia
* Filtros de busca
* Métricas gerais do sistema

---

## ⚙️ Arquitetura do Sistema

* Backend: API REST com Spring Boot
* Banco de dados: PostgreSQL
* Cache: Redis
* Proxy reverso e balanceamento: Nginx

---

## 🧪 Testes

Cada funcionalidade implementada passa por um processo de validação manual:

* Testes de fluxo principal
* Testes de erro
* Validação de comportamento

---