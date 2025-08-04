Phase 1: PROJECT SETUP 
Goal: "To analyze inventory data using SQL, Power BI, and Python to identify demand patterns, optimize stock levels, reduce out-of-stock issues, and improve restocking strategies."
| Use Case                 | Recommended Tool                        |
| ------------------------ | --------------------------------------- |
| Data storage/querying    | **SQLite**         |
| Analysis + Visualization | **Power BI** / Excel / Python (Jupyter) |
| Bonus (Automation)       | Python (for scheduling or alerts)       |

Entity Relationship Diagram
[Products]──┬──[Sales]
            ├──[Purchases]
            └──[Restocks]──[Suppliers]
| Table       | Purpose                            |
| ----------- | ---------------------------------- |
| `products`  | Product master info                |
| `sales`     | Sale transactions (quantity, date) |
| `purchases` | Purchase transactions              |
| `restocks`  | Supplier-wise restocks ordered     |
| `suppliers` | Supplier details                   |
