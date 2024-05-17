# Core vs ORM

SQLAlchemy is presented as two distinct APIs, one building on top of the other. This
APIs are known as **Core** and **ORM**.

**SQLAlchemy Core** is the foundational architecture for SQLAlchemy as a "database
toolkit". The library provides tools for managing connectivity to a database,
interacting with database queries and results, and programmatic construction of SQL
statements.

SQLAlchemy constructs used in core will be imported from the `sqlalchemy` namespace.
