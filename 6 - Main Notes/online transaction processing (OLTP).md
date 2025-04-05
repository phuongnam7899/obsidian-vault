2025-04-02 20:57

Tags: [[System Design]]

---

- A type of system architecture designed to handle **multiple concurrent transaction in** **realtime**
- Characteristic:
  - Handle many **small/quick transactions**
  - Focus on data **consistency and integrity**
  - Optimized for fast query processing
  - Support [[ACID]] props
- Use cases:
  - Banking transaction
  - Order processing
  - Inventory management
  - CRM
  - PoS system
- Key features:
  - Transaction-oriented
  - Realtime process
  - High concurrency support
  - Data integrity
  - Fast response
  - Structured data
- Structure:
  - Database layer: [[OLTP databases]]
  - Application layer:
    - Business logic
    - Interface
    - ...

> [!i] OLTP is contrasted with [[OLAP]]

---

# References
