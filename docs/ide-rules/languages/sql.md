---
description: SQL best practices covering query optimization, database design, and secure data manipulation patterns.
---

# SQL Development Guidelines

To create a new Cursor Rule:

1. Create a file named `sql.md` in `.cursor/rules/`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: 
globs: **/*.sql
alwaysApply: false
---
# SQL Development Guidelines

This document provides a comprehensive set of guidelines for SQL development, covering aspects from naming conventions and table design to query optimization, security, and testing, aimed at promoting best practices in database management and application development.

## Implementing These Principles

These guidelines are built upon the following core principles:

- Principle 1: Clarity and Maintainability: Ensuring SQL code and database structures are easy to understand, modify, and maintain.
- Principle 2: Performance and Scalability: Designing databases and queries for optimal performance and the ability to handle growing data and user loads.
- Principle 3: Data Integrity and Security: Protecting data accuracy, consistency, and safeguarding against unauthorized access or loss.
- Principle 4: Consistency: Applying uniform standards across the database schema and SQL code.

## Table of contents

- Rule 1: Naming Conventions
- Rule 2: Table Design
- Rule 3: Query Writing
- Rule 4: Indexing Strategy
- Rule 5: Security Guidelines
- Rule 6: Performance Optimization Tips
- Rule 7: Transaction Guidelines
- Rule 8: Migration Best Practices
- Rule 9: Code Examples
- Rule 10: Testing Guidelines
- Rule 11: Monitoring Practices

## Rule 1: Naming Conventions

Title: Consistent Naming for Database Objects
Description: Defines standard naming conventions for database objects like tables, columns, foreign keys, views, triggers, indexes, and constraints to ensure clarity and consistency across the database schema.

**Good example:**

**General:**
- Use snake_case for all database objects
- Use plural for table names (e.g., `users`, `orders`)
- Use singular for column names (e.g., `user_id`, `order_date`)
- Prefix foreign keys with referenced table name (e.g., `user_id`)
- Use verb_noun format for stored procedures (e.g., `get_user`, `update_order`)

**Prefixes:**
- Views: `v_`
- Triggers: `trg_`
- Indexes: `idx_`
- Constraints:
  - Primary Key: `pk_`
  - Foreign Key: `fk_`
  - Unique: `uq_`
  - Check: `ck_`

## Rule 2: Table Design

Title: Best Practices for Designing Database Tables
Description: Outlines best practices for table design, including primary keys, appropriate data types, normalization (aiming for at least 3NF), inclusion of timestamp columns (`created_at`, `updated_at`), use of foreign key constraints for referential integrity, consideration for soft deletes (`deleted_at`), and strategic indexing for frequently queried columns.

**Good example:**

**Best Practices:**
- Always include a primary key.
- Use appropriate data types for columns.
- Normalize to at least 3NF unless there's a good reason not to.
- Include `created_at` and `updated_at` timestamp columns.
- Use foreign key constraints to maintain referential integrity.
- Consider soft deletes using a `deleted_at` timestamp.
- Add appropriate indexes for frequently queried columns.

**Common Columns:**
- `id: BIGINT AUTO_INCREMENT PRIMARY KEY`
- `created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP`
- `updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP`
- `deleted_at: TIMESTAMP NULL`

## Rule 3: Query Writing

Title: Guidelines for Writing Effective and Readable SQL Queries
Description: Provides guidelines for formatting SQL queries for readability and optimizing them for performance. This includes advice on `SELECT` statements, using `EXISTS` versus `IN`, appropriate indexing, avoiding correlated subqueries where possible, using `EXPLAIN` to analyze query performance, considering query execution plans, and using batch operations for bulk data modifications.

**Good example:**

**Formatting:**
- Use uppercase for SQL keywords (e.g., `SELECT`, `FROM`, `WHERE`).
- Place one clause per line for better readability.
- Indent subqueries and Common Table Expressions (CTEs).
- Align column lists vertically in `SELECT` statements.
- Use meaningful and concise table aliases.

**Performance:**
- Avoid `SELECT *`; specify only the columns needed.
- Use `EXISTS` instead of `IN` with subqueries for potentially better performance, especially on large datasets.
- Ensure appropriate indexes are available for columns used in `WHERE` clauses, `JOIN` conditions, and `ORDER BY` clauses.
- Avoid correlated subqueries when an equivalent join or non-correlated subquery can be used.
- Use `EXPLAIN` (or similar command for your RDBMS) to analyze query performance and understand the execution plan.
- Consider the query execution plan to identify bottlenecks.
- Use batch operations for bulk updates or inserts to reduce overhead.

**Example Query:**
```sql
SELECT
    u.id,
    u.first_name,
    u.last_name,
    o.order_date
FROM
    users u
LEFT JOIN
    orders o ON u.id = o.user_id
WHERE
    u.deleted_at IS NULL
    AND o.status = 'COMPLETED'
ORDER BY
    o.order_date DESC;
```

## Rule 4: Indexing Strategy

Title: Principles for Effective Database Indexing
Description: Covers principles for creating and managing database indexes. This includes indexing foreign key columns, columns frequently used in `WHERE` clauses or `JOIN` conditions, considering composite indexes for multi-column queries, and avoiding over-indexing which can negatively impact write performance. It also mentions monitoring index usage and removing unused indexes.

**Good example:**

**Principles:**
- Index foreign key columns.
- Index frequently queried columns (those appearing in `WHERE`, `JOIN`, `ORDER BY`, `GROUP BY` clauses).
- Consider composite indexes for queries that filter or sort on multiple columns. The order of columns in a composite index matters.
- Avoid over-indexing, as each index consumes storage and adds overhead to write operations (inserts, updates, deletes).
- Monitor index usage to identify underutilized or unused indexes.
- Remove unused indexes to reclaim space and reduce maintenance overhead.

**Types (common examples):**
- B-tree (default for most relational databases, good for range queries and equality)
- Hash (good for exact equality checks, not for range queries)
- Full-text (for searching text content within columns)
- Spatial (for indexing geographical data)

## Rule 5: Security Guidelines

Title: Database Security Best Practices
Description: Highlights essential security measures for databases, including the use of prepared statements or parameterized queries to prevent SQL injection, implementation of proper access control mechanisms (granting least privilege), encryption of sensitive data both at rest and in transit, auditing access to sensitive data, conducting regular security reviews, establishing a robust backup and recovery strategy, and using appropriate user permissions.

**Good example:**

- Use prepared statements (or parameterized queries) to prevent SQL injection vulnerabilities.
- Implement proper access control: Grant users and applications only the permissions necessary to perform their tasks (principle of least privilege).
- Encrypt sensitive data: Protect data at rest (e.g., using TDE or column-level encryption) and in transit (e.g., using SSL/TLS).
- Audit sensitive data access: Log and monitor access to critical data to detect and investigate suspicious activity.
- Conduct regular security reviews and vulnerability assessments.
- Implement a comprehensive backup and recovery strategy.
- Use appropriate and distinct user permissions for different application roles or services.

## Rule 6: Performance Optimization Tips

Title: Tips for Optimizing Database Performance
Description: Provides a collection of tips for optimizing database performance. These include selecting appropriate data types for columns to save space and improve comparison speed, normalizing database design to reduce redundancy, indexing strategically, writing optimized queries, using connection pooling to manage database connections efficiently, implementing caching mechanisms where appropriate, performing regular database maintenance (like `VACUUM`, `ANALYZE`, or index rebuilding), and continuously monitoring query performance.

**Good example:**

- Use appropriate data types: Choose the smallest data type that can reliably store the required data.
- Normalize database design: Reduce data redundancy and improve data integrity, which can also benefit performance.
- Index strategically: Create indexes on columns used in search conditions and joins, but avoid over-indexing.
- Optimize queries: Rewrite inefficient queries, avoid `SELECT *`, and use `EXPLAIN` to analyze execution plans.
- Use connection pooling: Reduce the overhead of establishing database connections for each request.
- Implement caching where appropriate: Cache frequently accessed, relatively static data to reduce database load.
- Perform regular maintenance: Tasks like `VACUUM` (in PostgreSQL), `ANALYZE`, or rebuilding indexes can improve performance.
- Monitor query performance: Identify and address slow or resource-intensive queries.

## Rule 7: Transaction Guidelines

Title: Guidelines for Managing Database Transactions
Description: Offers guidelines for managing database transactions effectively. Key advice includes keeping transactions as short as possible to minimize locking and resource contention, using appropriate isolation levels to balance consistency and concurrency needs, handling potential deadlocks gracefully, implementing robust error handling within transactions, and considering the use of savepoints for more complex transactional logic.

**Good example:**

- Keep transactions as short as possible: Long-running transactions can hold locks for extended periods, impacting concurrency.
- Use appropriate isolation levels: Understand the trade-offs (e.g., `READ COMMITTED`, `REPEATABLE READ`, `SERIALIZABLE`) and choose the level that meets the application's consistency requirements without unduly harming performance.
- Handle deadlocks appropriately: Implement mechanisms to detect and retry transactions in case of deadlocks.
- Implement proper error handling: Ensure that transactions are rolled back in case of errors to maintain data consistency.
- Consider using savepoints for complex transactions that might need partial rollbacks.

## Rule 8: Migration Best Practices

Title: Best Practices for Database Schema Migrations
Description: Outlines best practices for managing database schema changes and data migrations. This includes version controlling all database changes, using dedicated migration tools (like Flyway or Liquibase), designing migrations to be reversible whenever possible, thoroughly testing migrations in non-production environments before applying them to production, including rollback scripts or procedures, and clearly documenting any breaking changes.

**Good example:**

- Version control all database changes: Store schema definitions and migration scripts in a version control system (e.g., Git).
- Use migration tools (e.g., Flyway, Liquibase): These tools help manage, track, and apply database changes systematically.
- Make migrations reversible when possible: Design changes so they can be undone if necessary.
- Test migrations thoroughly in non-production environments that mirror production as closely as possible.
- Include rollback scripts or procedures for migrations.
- Document breaking changes and communicate them to relevant teams.

## Rule 9: Code Examples

Title: Illustrative SQL Code Examples
Description: Provides practical examples of SQL code, including table creation and stored procedure definitions, to demonstrate the application of various guidelines such as naming conventions, data type selection, and indexing.

**Good example:**

**Table Creation:**
```sql
CREATE TABLE users (
    id BIGINT AUTO_INCREMENT,
    email VARCHAR(255) NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    status ENUM('ACTIVE', 'INACTIVE', 'SUSPENDED') DEFAULT 'ACTIVE',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    deleted_at TIMESTAMP NULL,
    PRIMARY KEY (pk_users_id), -- Example of pk_ prefix
    UNIQUE INDEX uq_users_email (email), -- Example of uq_ prefix for unique index
    INDEX idx_users_status (status) -- Example of idx_ prefix for general index
);
```
*Note: The `pk_users_id` demonstrates the primary key prefix. `AUTO_INCREMENT` syntax might vary by RDBMS (e.g., `SERIAL` or `IDENTITY`). Enum usage also varies.*

**Stored Procedure:**
```sql
-- Syntax for DELIMITER and stored procedure creation can vary by RDBMS.
-- This is a MySQL-like example.
DELIMITER //
CREATE PROCEDURE get_active_users(IN status_param VARCHAR(20))
BEGIN
    SELECT
        id,
        email,
        first_name,
        last_name
    FROM
        users
    WHERE
        status = status_param
        AND deleted_at IS NULL;
END //
DELIMITER ;
```

## Rule 10: Testing Guidelines

Title: Guidelines for Database Testing
Description: Covers guidelines for comprehensively testing database components and interactions. This includes testing with representative data volumes to uncover performance issues, including edge cases and boundary conditions in test data, testing performance under various load conditions, verifying data integrity constraints (like primary keys, foreign keys, unique constraints, check constraints), testing stored procedures and functions for correctness, validating migration scripts (both upgrade and rollback), and testing rollback procedures.

**Good example:**

- Test with representative data volumes: Small test datasets may not reveal performance issues that appear with larger amounts of data.
- Include edge cases and boundary conditions in test data.
- Test performance under load to simulate real-world usage patterns.
- Verify data integrity constraints: Attempt to insert/update data that violates constraints to ensure they are enforced.
- Test stored procedures, functions, and triggers for correct behavior and logic.
- Validate migration scripts: Test both the application of migrations and, if applicable, their rollback.
- Test rollback procedures to ensure they work as expected in case of deployment failures.

## Rule 11: Monitoring Practices

Title: Practices for Database Monitoring
Description: Details essential practices for monitoring database health and performance. This involves monitoring overall query performance, tracking slow queries that may indicate bottlenecks, monitoring disk usage to prevent storage issues, tracking connection pool usage to ensure it's adequately sized, monitoring cache hit rates to assess caching effectiveness, setting up alerts for critical issues (e.g., high error rates, low disk space, long-running queries), and conducting regular performance reviews.

**Good example:**

- Monitor query performance: Use database-specific tools or APM solutions to track execution times and resource consumption of queries.
- Track slow queries: Identify and analyze queries that exceed performance thresholds.
- Monitor disk usage: Keep an eye on storage capacity and I/O performance.
- Track connection pool usage: Ensure the pool is not exhausted and is efficiently managing connections.
- Monitor cache hit rates: For database caches or application-level caches interacting with the database.
- Set up alerts for critical issues (e.g., low disk space, high CPU usage, long-running transactions, replication lag).
- Conduct regular performance reviews to proactively identify and address potential issues.
--- 
```