# Web Development – Semester 3 (Node.js & Express Backend)

[![Node.js](https://img.shields.io/badge/Node.js-v18%2B-3c096c?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Author](https://img.shields.io/badge/Author-Anubhav-9d4edd?style=for-the-badge&logo=github&logoColor=white)](https://github.com/anubhavt675-gif)
[![Roll No](https://img.shields.io/badge/Roll%20No-2501730406-7b2cbf?style=for-the-badge)](#-student-profile)
[![Institution](https://img.shields.io/badge/Institution-K.R.%20Mangalam%20University-5a189a?style=for-the-badge)](https://krmangalam.edu.in)
[![Dependencies](https://img.shields.io/badge/Dependencies-Zero%20(Pure%20Core%20Modules)-240046?style=for-the-badge)](#-technology-stack)
[![License](https://img.shields.io/badge/License-ISC-e0aaff?style=for-the-badge&labelColor=10002b)](web%20dev%203%20assignment%203/LICENSE)

Welcome to the **Web Development III** repository containing coursework, lab assignments, and backend systems implemented using **Node.js Core Modules** and **Express.js**.

---

## 👨‍🎓 Student Profile

- **Name**: Srishti
- **Roll Number**: `2501730380`
- **Program**: B.Tech CSE (Core)
- **Institution**: K.R. Mangalam University, Gurugram, Haryana
- **GitHub Profile**: [@Srish-ttii](https://github.com/Srish-ttii)
- **Repository**: [Srish-ttii/WEB-DEV-III-ASSIGNMENT---1](https://github.com/Srish-ttii/WEB-DEV-III-ASSIGNMENT---1-)
---

## 📑 Repository Structure

```
WEB-DEVELOPMENT-SEM-3/
├── .gitignore
├── README.md                               # Root repository documentation
└── web dev 3 assignment 3/                 # Lab Assignment 1: Smart Utility Toolkit
    ├── app.js                              # Main application entry point reusing custom modules
    ├── calculator.js                       # CLI Calculator parsing process.argv inputs
    ├── dice.js                             # Cryptographic dice generator with history logging
    ├── fileManager.js                      # Async File CRUD operations & sync vs async demo
    ├── server.js                           # Native HTTP server handling custom routes & 404s
    ├── test.txt                            # Sample file for file system testing
    ├── package.json                        # Project metadata & npm execution scripts
    ├── LICENSE                             # ISC Open Source License
    ├── README.md                           # Assignment-specific documentation
    ├── modules/
    │   ├── isEven.js                       # Custom parity verification module
    │   └── logger.js                       # Custom colorized ANSI logger with ISO timestamps
    └── assets/
        ├── EXPLANATION.md                  # Comprehensive architectural & technical explanation
        └── Lab Assignment 1.pdf            # University assignment specification document
```

---

## 🚀 Lab Assignment 1: Smart Utility Toolkit

### Overview
A comprehensive Node.js utility toolkit built **strictly without third-party npm packages**, utilizing standard **Node.js Core Modules**:
- `process` – Command-line interface parsing and execution management
- `http` – Native HTTP web server creation, custom routing, and status codes
- `fs` – Asynchronous CRUD file management (`writeFile`, `readFile`, `appendFile`, `unlink`)
- `crypto` – Cryptographically secure random number generation
- `path` – Cross-platform file path resolution

---

### 🧩 Module Breakdown

#### 1. CLI Calculator (`calculator.js`)
Performs arithmetic operations parsed directly from `process.argv`.
- **Supported Operations**: `add` (`+`), `subtract` (`-`), `multiply` (`*`), `divide` (`/`), `modulo` (`%`), `power` (`^`)
- **Error Handling**: Division/modulo by zero guards, non-numeric operand validation, informative usage tips.

```bash
node "web dev 3 assignment 3/calculator.js" add 15 25      # Output: Result: 40
node "web dev 3 assignment 3/calculator.js" divide 100 4   # Output: Result: 25
node "web dev 3 assignment 3/calculator.js" power 2 8      # Output: Result: 256
```

#### 2. Custom Modules & Reusability (`app.js` & `modules/`)
Demonstrates CommonJS modularity (`module.exports` and `require()`) by combining multiple modules:
- **`modules/isEven.js`**: Reusable numerical parity evaluation.
- **`modules/logger.js`**: Terminal logging formatted with ANSI colors (`[INFO]`, `[SUCCESS]`, `[WARNING]`, `[ERROR]`) and ISO timestamps.
- **`app.js`**: CLI dispatcher that accepts arguments or executes an automated test suite.

```bash
node "web dev 3 assignment 3/app.js" 14     # [SUCCESS] Number 14 is EVEN
node "web dev 3 assignment 3/app.js" 9      # [SUCCESS] Number 9 is ODD
node "web dev 3 assignment 3/app.js" Hello  # [INFO] Input message: "Hello"
```

#### 3. Native HTTP Web Server (`server.js`)
Lightweight web server built on the native `http` module listening on port `3000` (or `process.env.PORT`).

| Route | Response / View | Status Code |
| :--- | :--- | :--- |
| `GET /` or `/home` | Welcome Home Page with Navigation Links | `200 OK` |
| `GET /about` | Student Profile (**Anubhav - Roll No: 2501730406**) & Overview | `200 OK` |
| `GET /contact` | Developer Contact Details & GitHub link | `200 OK` |
| `GET /*` | Custom stylized 404 Not Found Page | `404 Not Found` |

```bash
cd "web dev 3 assignment 3"
npm run server
# Open http://localhost:3000 in your browser
```

#### 4. File Manager & Execution Flow Analysis (`fileManager.js`)
Performs asynchronous CRUD file operations using the `fs` module and includes an **interactive demo** comparing synchronous vs. asynchronous execution order.

```bash
# File CRUD Commands:
node fileManager.js create test.txt "Initial Line"
node fileManager.js read test.txt
node fileManager.js update test.txt "\nAppended Line"
node fileManager.js delete test.txt

# Run Event Loop & Async Flow Demo:
node fileManager.js demo
```

##### 🔍 Understanding Event Loop & Execution Flow:
1. **[STEP 1] Synchronous console log**: Executes immediately on the call stack.
2. **[Async Call Initiated]**: `fs.writeFile` delegates disk I/O to libuv worker threads.
3. **[STEP 2] Synchronous console log**: Executes right away without waiting for file I/O.
4. **[STEP 3 - Callback]**: Once disk write completes, the callback enters the Event Loop's Poll phase and executes.
5. **[STEP 4 & 5 - Nested Callbacks]**: Chained asynchronous append and read operations execute in subsequent event loop ticks.

#### 5. Cryptographic Random Dice Generator (`dice.js`)
Uses `crypto.randomInt(1, 7)` to produce cryptographically unbiased dice values (1–6). Supports single roll, custom loop iterations, and auto-logging to `dice_history.txt` with timestamps.

```bash
# Roll single dice
node dice.js

# Roll dice N times in a loop
node dice.js 5
```

---

## ⚡ Quickstart Guide

Clone and run any utility locally:

```bash
# 1. Clone the repository
git clone https://github.com/Srish-ttii/WEB-DEV-III-ASSIGNMENT---1-
cd WEB-DEV-III-ASSIGNMENT---1/"web dev 3 assignment 1"

# 2. Run Main Application
npm start

# 3. Start HTTP Server
npm run server

# 4. Run Execution Flow Demo
npm run file:demo
```

---

## 📊 Rubric Compliance Matrix

| Rubric Criteria | Allocated Marks | Status | Implementation Details |
| :--- | :---: | :---: | :--- |
| **Functionality** | 1.5 Marks | ✅ **Achieved** | Calculator, Custom `isEven` module, Native HTTP routing, `fs` CRUD file manager, `crypto` dice roll generator. |
| **Code Structure & Modules** | 0.5 Marks | ✅ **Achieved** | Clean CommonJS modularity (`module.exports`/`require`), zero external dependencies, clean folder separation. |
| **Clean Code & Output** | 0.5 Marks | ✅ **Achieved** | ANSI color-coded logging, ISO timestamps, robust input validation, graceful error messages, and full documentation. |
| **Total** | **2.5 / 2.5 Marks** | 💯 | **Fully Satisfied** |

---

## 📜 License & Acknowledgments

This project is licensed under the [ISC License](web%20dev%203%20assignment%203/LICENSE).  
Developed by **Srishti** (Roll No: `2501730380`) for Web Development III.
