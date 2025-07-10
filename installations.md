# ⚙️ Setup Instructions for Python Workshop

This guide will help you install the required tools and configure your environment for the Python for Data Operations Workshop.

---

## 🐍 Anaconda (Python Environment)

Install the full [Anaconda distribution](https://www.anaconda.com/download/success) (not Miniconda).

### 🖥️ How to Check if You Have an Intel or Apple Silicon Mac

1. Click the Apple  menu in the top-left corner.  
2. Select **"About This Mac"**.  
3. Look at the **"Processor"** or **"Chip"** section:  
   - If it says **Intel Core i5** → you have an **Intel Mac**.  
   - If it says **Apple M1**, **M2**, or **Apple chip** → you have an **Apple Silicon Mac**.

---

## 🔌 SQL ODBC Driver 18

### 🪟 Windows

Download and install from the official Microsoft documentation:  
➡️ [ODBC Driver 18 for SQL Server – Windows](https://learn.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-ver17)

---

### 🍎 macOS

#### Step 1: Install Homebrew (if not already installed)

Open the **Terminal** and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
