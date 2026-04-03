# Working with a Relational Database Using the Spring Ecosystem (June 2015)

The goal of this project is to study and compare different data access architectures in a Java application based on the **Spring** ecosystem, specifically **Spring JDBC** and **Spring JPA**, when applied to a relational database.

The associated theoretical and educational materials are available here:  
👉 https://stahe.github.io/en-spring-database-juin-2015/

---

## Project Objectives

- Understand a **layered application architecture**
- Compare two data access approaches:
  - "Classic" JDBC
  - JPA (Java Persistence API)
- Measure and compare the **performance** of both solutions
- Examine the challenges of **portability between DBMS**

---

## General Architecture

The application is based on a layered architecture, where the execution flow goes from left to right:

![](https://stahe.github.io/spring-database-juin-2015/images/10000000000007080000017A09403716.png)


### Role of the Layers

#### UI Layer
- Application entry point
- Receives user actions
- Displays results

#### Business Layer
- Implements **business rules**
- Processes data from:
  - the database (via DAO)
  - the user (via UI)
- Can return or persist results

#### DAO (Data Access Object) Layer
- Exposes a **business data access interface**
- Hides the technical details of database access
- Depends on the technology used (JDBC or JPA)

#### JDBC Layer
- Standard interface for accessing relational databases
- DBMS-independent (via JDBC drivers)
- Enables good performance but limited portability in practice

---

## Evolution toward JPA

Since the mid-2000s, the architecture can evolve as follows:

![](https://stahe.github.io/spring-database-juin-2015/images/10000000000006FE000001774C207100.png)

### Specific Features of JPA

- The **JPA** layer generates SQL queries
- The DAO layer:
  - no longer contains SQL
  - manipulates persistent objects
- Advantages:
  - Better portability between DBMSs
  - Abstraction from proprietary SQL
- Disadvantages:
  - Performance generally lower than JDBC

JPA formalizes concepts previously introduced by frameworks such as **Hibernate**.

---

## JDBC vs. JPA Comparison

The project implements **two distinct DAO implementations**:

![](https://stahe.github.io/spring-database-juin-2015/images/10000000000006FE000001774C207100.png)

![](https://stahe.github.io/spring-database-juin-2015/images/10000000000006E10000016947159BE8.png)


### Common Constraints

- `DAO1` and `DAO2` implement the **same `IDAO` interface**
- The unit tests are **identical** for both implementations
- Objective: compare **functionality** and **performance**

---

## Tests and Performance

- Tests are performed using **JUnit**
- A single test class (`JUnitTestsDao`) is used
- The results allow us to:
  - verify functional compliance
  - compare JDBC vs. JPA execution times

---

## DBMS Portability

Although JDBC aims for maximum portability:
- proprietary SQL;
- primary key generation strategies;
- specific reserved words;

limit this portability in practice.

In this project, the JDBC and JPA architectures were ported to **six different DBMSs**, requiring specific configurations for each DBMS.

---

## Conclusion

This project illustrates:
- the trade-offs between **performance** and **abstraction**
- architectural choices related to data access
- the contribution of Spring to the structuring and testability of applications

It serves as an educational resource for gaining a practical understanding of JDBC, JPA, and their comparative uses within a Spring architecture.

Serge Tahé, june 2015
---
