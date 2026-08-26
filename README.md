# 🖥️ JavaFX + JDBC Desktop Application

[![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://www.oracle.com/java/)
[![JavaFX](https://img.shields.io/badge/JavaFX-11%2B-blue?style=for-the-badge&logo=java)](https://openjfx.io/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-00758F?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

Aplicação desktop desenvolvida em **Java** utilizando **JavaFX** para a interface gráfica e **JDBC** para integração com o banco de dados **MySQL**. O projeto tem como objetivo gerenciar um sistema completo de cadastro de **Departamentos** e **Vendedores**, aplicando padrões de projeto essenciais para a construção de softwares bem estruturados e manuteníveis.

---

## 📌 Funcionalidades

- 📋 **Gestão de Departamentos:** Listagem, inserção, edição e remoção de departamentos (CRUD completo).
- 👤 **Gestão de Vendedores:** Listagem, inserção, edição e remoção de vendedores vinculados a um departamento.
- 🖼️ **Interface Gráfica Dinâmica:** Telas desenvolvidas com **FXML** e estilizadas com CSS.
- 🔄 **Atualização em Tempo Real:** Uso de *Listeners* e padrão *Observer* para atualizar a listagem automaticamente após alterações.
- ⚠️ **Tratamento de Exceções:** Validação de campos de formulário e tratamento de erros do banco de dados (ex: impedimentos de exclusão de departamentos vinculados a vendedores).

---

## 🛠️ Tecnologias e Padrões Utilizados

- **Linguagem:** Java (JDK 11+)
- **Interface Gráfica:** JavaFX & FXML (Scene Builder)
- **Persistência de Dados:** JDBC (Java Database Connectivity)
- **Banco de Dados:** MySQL
- **Padrões de Arquitetura & Design:**
  - **MVC (Model-View-Controller):** Separação clara de responsabilidades da aplicação.
  - **DAO (Data Access Object):** Abstração e desacoplamento da camada de acesso aos dados.
  - **Service Layer:** Camada intermediária para isolar regras de negócio.
  - **Observer Pattern:** Notificação de eventos entre controllers para atualização automática da interface.

---

## 📁 Estrutura do Projeto

```text
src/
├── application/          # Classe principal de inicialização (Main.java)
├── db/                   # Gerenciador de conexão com o banco (DB, DbException, DbIntegrityException)
├── gui/                  # Controllers, Views (.fxml) e Listeners
│   ├── util/             # Utilitários de interface (Alerts, Constraints, Utils)
│   └── ...
└── model/
    ├── dao/              # Interfaces e Implementações DAO (DaoFactory, SellerDao, DepartmentDao)
    ├── entities/         # Classes de Domínio (Department, Seller)
    ├── exceptions/       # Exceções personalizadas de validação
    └── services/         # Camada de Serviços (DepartmentService, SellerService)
```

---

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [JDK 11+](https://www.oracle.com/java/technologies/downloads/)
- [MySQL Server](https://dev.mysql.com/downloads/installer/) (rodando na porta padrão `3306`)
- Uma IDE de sua preferência (Eclipse, IntelliJ IDEA ou VS Code)
- *Opcional:* [Scene Builder](https://gluonhq.com/products/scene-builder/) para edição visual dos arquivos FXML.

---

## 🛢️ Configuração do Banco de Dados

1. Acesse o seu SGBD MySQL e execute o script abaixo para criar a estrutura do banco e popular os dados iniciais:

```sql
CREATE DATABASE coursefx;
USE coursefx;

CREATE TABLE department (
  Id int(11) NOT NULL AUTO_INCREMENT,
  Name varchar(60) DEFAULT NULL,
  PRIMARY KEY (Id)
);

CREATE TABLE seller (
  Id int(11) NOT NULL AUTO_INCREMENT,
  Name varchar(60) NOT NULL,
  Email varchar(60) NOT NULL,
  BirthDate datetime NOT NULL,
  BaseSalary double NOT NULL,
  DepartmentId int(11) NOT NULL,
  PRIMARY KEY (Id),
  FOREIGN KEY (DepartmentId) REFERENCES department (Id)
);

INSERT INTO department (Name) VALUES 
  ('Computers'),
  ('Electronics'),
  ('Fashion'),
  ('Books');

INSERT INTO seller (Name, Email, BirthDate, BaseSalary, DepartmentId) VALUES 
  ('Bob Brown','bob@gmail.com','1998-04-21 00:00:00',1000,1),
  ('Maria Green','maria@gmail.com','1979-12-31 00:00:00',3500,2),
  ('Alex Grey','alex@gmail.com','1988-01-15 00:00:00',2200,1);
```

2. Crie o arquivo `db.properties` na raiz do projeto com as suas credenciais de acesso ao MySQL:

```properties
user=SEU_USUARIO_MYSQL
password=SUA_SENHA_MYSQL
dburl=jdbc:mysql://localhost:3306/coursefx?useSSL=false
useSSL=false
```

---

## 🚀 Como Executar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone [https://github.com/andrade111/javafx-jdbc.git](https://github.com/andrade111/javafx-jdbc.git)
   ```

2. **Abra o projeto na sua IDE favorita:**
   - Adicione as bibliotecas do **JavaFX SDK** e o driver **MySQL Connector/J** ao *Build Path* do projeto.
   - Adicione os argumentos de VM necessários para a execução do JavaFX (caso esteja utilizando JDK 11 ou superior sem Maven/Gradle):
     ```bash
     --module-path /caminho/para/javafx-sdk/lib --add-modules javafx.controls,javafx.fxml
     ```

3. **Execute a aplicação:**
   - Localize a classe `Main.java` em `src/application/Main.java` e execute-a.

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<p align="center">Desenvolvido por <a href="https://github.com/andrade111">Gabriel Andrade</a> 👋</p>
