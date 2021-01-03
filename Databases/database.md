---
title: Database
created: '2020-08-14T18:48:01.532Z'
modified: '2020-08-14T19:33:30.380Z'
---

# Database

Types of databases:




## Relational Databases Design:

### Normalization
Why Normalize?
- Non-atomic values
- Redundancy

  Redundancy Misconceptions
  - Not all redundancy is bad
  - But uncontrolled redundancy is bad

- Modification anomalies

### Basic Normal Forms
- Types of Normal Forms:
  - 1NF
  - 2NF
  - 3NF
  - Elementary Key Normal Form(EKNF)
  - Boyce-Codd Normal Form(BCNF)
  - Fourth Normal Form(4NF)
  - Fifth Normal Form(5NF)
  - Domain/Key Normal Form(DKNF)
  - Sixth Normal Form(6NF)

- Normal Forms apply to table
- Normal form of database = lowest normal form of all its tables
- It is good to have all tables upto third normal form(3NF)
- When to normalize

### Function Dependencies
- Attribute A --> Attribute B
  - Attribute B is functionally dependant on attribute B
- Properties of functional dependencies:
  - FD Can be mutual(if a depends on b and b depends on a)
    - Most are not
  - FD can be a combination of two or more attributes
  - If X depends on Y, it also depends on each superset of Y
    - Dependancy on two or more attributes can sometimes be reduced
    - **Full Dependancy** : FD that cannot be reduced
  - Every attributes depends on itself(and on each superset of itself)
    - This is called as **Trivial Dependency**

-  Functional Dependenices and Normalization
  - Normalization uses functional dependencies that are:
    - Non-trivial
    - Full
- How to find all functional dependencies?
  - Most FD are obvious
  - But what about the rest?
  


### Find Functional Dependencies





Database delivery best practices:


