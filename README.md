# **SEED Labs – SQL Input Handling and Validation Lab**

## 📌 Overview  
This lab focuses on understanding how web applications interact with SQL databases and how improper input validation can affect the integrity of database operations. By observing the behavior of SQL queries when handling user-provided inputs, learners can better grasp the importance of secure coding practices and query construction.

Participants will examine how crafted inputs may alter SQL statements and learn to implement preventive measures using techniques such as parameterized queries.

---

## 🔹 Topics Covered

- SQL Statements: `SELECT`, `UPDATE`  
- Impact of unsanitized inputs on SQL query behavior  
- Mitigating unintended query execution using prepared statements  

---

## 🏗️ Lab Environment

This lab runs in a containerized setup with two components:

- **Web Application Container**  
- **Database Container**

### 🌐 Web Application Access  
- **URL:** `http://www.seed-server.com`  
- **IP Address:** `10.9.0.5`  
- **Host Mapping:** Add the following entry to `/etc/hosts`:  
```bash
10.9.0.5 www.seed-server.com

  ```

---
## ⚙️ Container Setup & Commands
Download and set up the lab environment using Docker:

```bash
$ docker-compose build   # Build container image
$ docker-compose up      # Start the container
$ docker-compose down    # Stop the container
