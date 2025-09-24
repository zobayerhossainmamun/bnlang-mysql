# bnlang-mysql

A lightweight, fast, and ergonomic MySQL client for **Bnlang (Bangla Programming Language)**.  
It provides a simple API for connecting, running queries, transactions, and connection pooling—tailored for Bnlang apps and tools.

---

## ✨ Features

- Zero-config quick start
- Safe parameterized queries (prepared statements)
- Pooled and single connections
- Transactions with `begin → commit/rollback`
- Streamed results for large datasets
- Typed helpers for common CRUD
- Graceful shutdown hooks

---

## 📦 Installation

Using **BPM (Bnlang Package Manager)**:

```bash
bpm install bnlang-mysql
```

Require in your Bnlang source:

```bnl
const mysql = require("bnlang-mysql");
```

> Tested with MySQL 5.7+, 8.x, and MariaDB 10.3+.

---

## ⚙️ Configuration

Create a client by URL or by object.

```bnl
ধ্রুবক conn = mysql.createConnection({
  host: "127.0.0.1",
  user: "root",
  password: "",
  database: "myapp",
  port: 3306,
  ssl: false,
  debug: true
});
```
---

## 🚀 Quick Start

```bnl
"use strict";

ধ্রুবক conn = mysql.createConnection({
  host: "127.0.0.1",
  user: "root",
  password: "",
  database: "myapp",
  port: 3306,
  ssl: false,
  debug: true
});

অসমলয় ফাংশন main(){
  চেষ্টা{
    অপেক্ষা conn.connect();
    ধ্রুবক result = অপেক্ষা conn.query("SELECT * FROM users");
    console.log('Users:', result);
  }ধরুন(err){
    console.error("Connection error: ", err);
  }অবশেষে{
    অপেক্ষা conn.end();
  }
}
main();
```

---

## 🔐 Parameterized Queries

Always pass values separately to prevent SQL injection:

```bnl
const user = await db.query(
  "SELECT id, email FROM users WHERE email = ?",
  ["alice@example.com"]
);
```

- `?` placeholders are replaced safely with encoded values.
- For IN-lists, pass arrays and use helpers:

```bnl
const ids = [1,2,3];
const rows = await db.query("SELECT * FROM orders WHERE id IN (?)", [ids]);
```

---

## 🤝 Contributing

Issues and PRs are welcome!  
Please open an issue describing the change before sending a large PR.

- Ensure tests cover your change
- Keep the API minimal and consistent
- Follow the existing code style

---

## License


bnlang-mysql is licensed under the [MIT License](./LICENSE).
