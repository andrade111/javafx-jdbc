# 🖥️ JavaFX + JDBC Desktop Application

[![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://www.oracle.com/java/)
[![JavaFX](https://img.shields.io/badge/JavaFX-11%2B-blue?style=for-the-badge&logo=java)](https://openjfx.io/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-00758F?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

Aplicação desktop desenvolvida em **Java** utilizando **JavaFX** para a interface gráfica e **JDBC** para integração com o banco de dados **MySQL**. O projeto tem como objetivo gerenciar um sistema simples de cadastro de **Departamentos** e **Vendedores**, aplicando padrões de projeto essenciais para o desenvolvimento de softwares bem estruturados.

---

## 📌 Funcionalidades

- 📋 **Gestão de Departamentos:** Listagem, inserção, edição e remoção de departamentos (CRUD completo).
- 👤 **Gestão de Vendedores:** Listagem, inserção, edição e remoção de vendedores vinculados a um departamento.
- 🖼️ **Interface Gráfica Dinâmica:** Telas desenvolvidas com **FXML** e estilizadas com CSS.
- 🔄 **Atualização em Tempo Real:** Uso de *Listeners* e padrão *Observer* para atualizar a listagem automaticamente após alterações.
- ⚠️ **Tratamento de Exceções:** Validação de campos de formulário e tratamento de erros do banco de dados (ex: impedimento de exclusão de departamentos com vendedores associados).

---

## 🛠️ Tecnologias e Padrões Utilizados

- **Linguagem:** Java (JDK 11+)
- **Interface Gráfica:** JavaFX & FXML (Scene Builder)
- **Persistência de Dados:** JDBC (Java Database Connectivity)
- **Banco de Dados:** MySQL
- **Padrões de Projeto (Design Patterns):**
  - **MVC (Model-View-Controller):** Separação de responsabilidades da aplicação.
  - **DAO (Data Access Object):** Abstração e desacoplamento do acesso aos dados.
  - **Service Layer:** Camada intermediária de regras de negócio.
  - **Observer Pattern:** Notificação de eventos entre controllers para atualização da interface.

---

## 📁 Estrutura do Projeto

```text
src/
├── gui/                  # Controllers, Views (.fxml) e Listeners
│   ├── util/             # Utilitários de interface (Alerts, Constraints, Utils)
│   └── ...
├── model/
│   ├── dao/              # Interfaces e Implementações DAO (JDBC)
│   ├── entities/         # Classes de Domínio (Department, Seller)
│   ├── exceptions/       # Exceções personalizadas (DbException, DbIntegrityException)
│   └── services/         # Camada de Serviços
└── db/                   # Gerenciador de Conexão com o Banco de Dados
