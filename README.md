# Employee Management System

This project is an Employee Management System built using Flask, SQLAlchemy, and PostgreSQL. It manages employees, their departments, bonuses, and sales. The system also includes features for tracking which employee is managing each department and calculating bonuses and commissions.

## Entity-Relationship Diagram (ERD)

The following ER diagram describes the relationships between **employees**, **departments**, **bonuses**, and **sales**:

```mermaid
erDiagram
    EMPLOYEE {
        int id PK
        varchar full_name
        varchar category_description
        date date_of_entry
        int years_of_entry
        int years_of_seniority
        decimal basic_salary
        int department_id FK
    }
    
    DEPARTMENT {
        int id PK
        varchar name
        int manager_id FK
    }

    BONUSES {
        int id PK
        int employee_id FK
        varchar bonus_type
        decimal bonus_amount
        date bonus_date
    }

    SALES {
        int id PK
        int employee_id FK
        decimal sales_amount
        decimal commission_rate
        decimal commission_amount
        date sales_date
    }

    EMPLOYEE ||--o{ DEPARTMENT : "belongs to"
    DEPARTMENT ||--o| EMPLOYEE : "managed by"
    EMPLOYEE ||--o{ BONUSES : "receives"
    EMPLOYEE ||--o{ SALES : "makes"
