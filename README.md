# **SEED Labs - SQL Injection Attack Lab**

## 📌 Overview
SQL injection is a code injection technique that exploits vulnerabilities in web applications interacting with database servers. When user inputs are not properly validated, attackers can manipulate SQL queries to extract or alter sensitive data.

In this lab, we explore SQL injection vulnerabilities in a web application, demonstrating potential exploits and implementing defense mechanisms.

### 🔹 Topics Covered:
- SQL statements: `SELECT` and `UPDATE`
- SQL injection attacks
- Securing applications using prepared statements

---

## 🏗️ Lab Environment
The lab runs in a containerized environment with two containers:

- **Web application container**
- **Database container**

### 🌐 Web Application Access
- **URL:** `http://www.seed-server.com`
- **IP Address:** `10.9.0.5`
- **Host Mapping:** Add the following entry to `/etc/hosts` (requires root privileges):
  
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
```

### 🔹 Aliases in `.bashrc` for convenience:
```bash
$ dcbuild  # Alias for docker-compose build
$ dcup     # Alias for docker-compose up
$ dcdown   # Alias for docker-compose down
```

### 🔹 To interact with a running container:
```bash
$ dockps          # List running containers
$ docksh <id>     # Open shell in container
```

---

## 🗄️ MySQL Database
- **Database:** `sqllab_users`
- **Table:** `credential`

### 🔹 MySQL Credentials:
- **Username:** `root`
- **Password:** `dees`

### 🔹 Connect to MySQL inside the container:
```bash
$ mysql -u root -pdees
mysql> use sqllab_users;
mysql> show tables;
```

### 🔹 To reset the database:
```bash
$ sudo rm -rf mysql_data
```

---

## 🏆 Lab Tasks

### 🔹 **Task 1: SQL Commands Exploration**
Query the database to retrieve employee data.

**Example SQL command to display Alice’s information:**
```sql
SELECT * FROM credential WHERE name='Alice';
```

### 🔹 **Task 2: SQL Injection Attacks**

#### ✅ **Task 2.1: Attack via Webpage**
- Exploit the SQL injection vulnerability in the login page (`unsafe_home.php`).
- Gain admin access without knowing the password.

#### ✅ **Task 2.2: Attack via Command Line**
Use `curl` to send SQL injection payloads:
```bash
$ curl 'http://www.seed-server.com/unsafe_home.php?username=alice&Password=11'
```
- **URL encode special characters** (`%27` for `'`, `%20` for space).

#### ✅ **Task 2.3: Modifying Database via SQL Injection**
Modify database entries using injection techniques.

**Example of appending an additional SQL statement:**
```sql
' OR '1'='1'; UPDATE credential SET salary=100000 WHERE name='Alice'; --
```

---

## 📚 Additional Resources
📖 **SEED Book:** *Computer & Internet Security: A Hands-on Approach*

📄 **Lab Environment Manual:** Refer to the [SEED Labs website](https://seedsecuritylabs.org/).

⚠️ **Disclaimer:** This lab is designed for educational purposes to understand and mitigate SQL injection attacks. Ensure ethical use of learned techniques.
