# 📚 Library Management System (Java)

A **modular, extensible Library Management System** implemented in **Java**, designed with **object-oriented best practices** and multiple **design patterns**.  
The system supports library operations such as **user management**, **work cataloging**, **borrowing/returning**, **notifications**, **rule enforcement**, and **advanced searching**, all through a clean separation between **core logic** and **user interface layers**.

## ✨ Key Features

- 📖 Manage different types of works (Books, DVDs, etc.)
- 👤 User registration, behavior tracking, fines, and notifications
- 🔄 Borrowing and returning workflows with rule validation
- 🔍 Advanced search using the **Visitor pattern**
- 🔔 Event-driven notifications for availability and requests
- 🧱 Clean separation between **Application**, **Core Domain**, and **UI Library**
- 🧪 Robust exception handling across all layers
- 🧩 Highly extensible architecture

## 🏗️ Architecture Overview

The project follows a **layered architecture**:

- **Core:** `bci-core/`  
  Contém as classes de domínio principais da aplicação.

- **Interaction:** `bci-app/`  
  Contém as classes responsáveis pela interação com o utilizador.

- **UML diagrams:** `uml/`  
  Contém os diagramas UML da primeira entrega.

## 🧠 Design Patterns Used

### 🧭 Visitor Pattern
- Used for advanced search functionality
- Decouples search logic from domain entities  
  (`SearchVisitor`, `SearchFilterVisitor`)

### 🔔 Observer Pattern
- Used in the notification subsystem
- Enables event-driven updates  
  (`NotificationService`, `NotificationListener`)

### 🧠 Strategy Pattern
- Used for user behavior management
- Dynamic behavior switching  
  (`NormalBehaviour`, `AbidingBehaviour`, `WrongfulBehaviour`)

### 🏗️ Command Pattern
- Used extensively in the application layer
- Each user action is encapsulated as a command  
  (`DoRegisterUser`, `DoRequestWork`, etc.)

### 🧩 Layered Architecture
- UI is fully decoupled from business logic
- Core logic is reusable and UI-agnostic


## 📦 Domain Model Highlights (bci-core)

### Works
- Abstract `Work` class
- Concrete implementations:
  - `Book`
  - `DVD`
- Associated entities:
  - `Creator`
  - `Category`

### Users
- `User` entity with dynamic behavior
- Borrowing requests via `Request`
- Fine management and notifications

### Rules Engine
Borrowing rules enforced via:
- `Rule` interface
- Concrete implementations:
  - `NoDuplicateRequestRule`
  - `LimitRequestRule`
  - `PriceLimitRule`
  - `NotSuspendedRule`
  - `NoReferenceWorkRule`


## ⚠️ Exception Handling

The system uses **domain-specific exceptions** to ensure robustness and clarity:

- `UserUnknownException`
- `WorkUnknownException`
- `RuleNotMetException`
- `BorrowingRuleFailedException`
- `UnavailableFileException`

This approach guarantees:
- Clear error propagation
- Strong domain boundaries
- UI-friendly error handling

---

## 🛠️ Build & Run

### Requirements
- Java 11+
- `make`

### ClASSPATH
Before running the program, you need to configure the CLASSPATH to include the po-uilib.jar library, which is used for the text-based interface.

```bash
Em Linux/MacOS:
export CLASSPATH=.:po-uilib/po-uilib.jar
```

```bash
Em Windows (PowerShell):
set CLASSPATH=.;po-uilib\po-uilib.jar
```

### Build
```bash
make
## Compilação e Execução

The compilation of the entire project (including the po-uilib library) is done automatically through the main Makefile.

```bash
make
```




Se quiseres definir esta configuração permanentemente, adiciona o comando ao teu ficheiro de inicialização (.bashrc, .zshrc, etc.).
