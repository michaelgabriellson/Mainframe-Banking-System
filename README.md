# Mainframe Banking System 🚧

## 🚀 Overview

This project explores the design of a banking system built on a mainframe using COBOL, CICS, and DB2.

The core idea is to help users better understand their finances by classifying transactions into categories such as:

* Necessary (e.g. rent, utilities)
* Lifestyle (e.g. subscriptions like Netflix)
* Flexible (e.g. discretionary spending)

---

## 💡 Concept

The system provides a simplified account overview:

* Welcome message with customer name
* Account number
* Current balance
* Transaction list including:

  * Transaction type
  * Amount
  * Date
  * Category (spending level)

This allows users to quickly understand how their money is distributed across different types of expenses.

---

## 🚧 Project Status

This project is a work in progress and was not fully completed.

The focus was on system design, data modeling, and initial CICS/DB2 setup.

---

## ⚙️ Technologies

* COBOL (planned business logic)
* CICS (transaction handling and screen navigation)
* DB2 (data storage)

---

## 🧱 System Setup (CICS)

Example of how the system was configured in CICS:

```cics
CEDA DEF PROG(saltbank) G(DBCG)
CEDA DEF TRANS(bank) G(DBCG) PROG(saltbank)

CEDA DEF DB2E(bane) G(DBCG) AuthID(USER11)
CEDA DEF DB2T(banT) G(DBCG) E(bane) T(bank)

CEDA DEF MAPSET(saltbnk) G(dbcg)
```

---

## 🗄️ Data Model (DB2)

The system is based on three core tables:

### Customer

```sql
CREATE TABLE Custinfo (
    Custid INT GENERATED ALWAYS AS IDENTITY,
    Name   VARCHAR(50),
    DOB    DATE
);
```

### Account

```sql
CREATE TABLE Acctinfo (
    Acctid    INT GENERATED ALWAYS AS IDENTITY,
    Accountnr VARCHAR(20) NOT NULL,
    Balance   DECIMAL(15,2),
    Custid    INT NOT NULL
);
```

### Transactions

```sql
CREATE TABLE Transac (
    Transid     INT GENERATED ALWAYS AS IDENTITY,
    Transaction VARCHAR(20),
    TransDet    VARCHAR(100),
    Amount      DECIMAL(15,2),
    Date        DATE,
    Acctid      INT NOT NULL
);
```

---

## 🔍 Design Idea (Future Enhancement)

A classification layer would categorize each transaction into:

* Necessary
* Lifestyle
* Flexible

This would enable better financial insights and budgeting support.

---

## 📸 Screenshots

Screenshots from early development stages illustrate the concept and UI design.

---

## 📚 What I Explored

* Designing a banking system from a user perspective
* Modeling financial data in DB2
* Setting up CICS programs, transactions, and mapsets
* Thinking about how to present financial data clearly to users

---

## 📌 Notes

This repository contains an early-stage version of the system.

COBOL program logic and some components are not included, but the focus is on system design and architecture.
