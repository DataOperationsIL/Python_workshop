# ⚙️ Setup Instructions for Python Workshop

This guide will help you install the required tools and configure your environment for the Python for Data Operations Workshop.

---

## 🐍 Anaconda (Python Environment)

Install the full [Anaconda distribution](https://www.anaconda.com/download/success) (not Miniconda).

### 🖥️ How to Check if You Have an Intel or Apple Silicon Mac for macOS installation

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

Open the Terminal app.
Run this command and press Enter:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Follow the on-screen instructions.

To verify that Homebrew installed correctly, run:
brew --version

#### Step 2: Add the Microsoft SQL Server repository
In the Terminal, run the following commands:

brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
 brew update

#### Step 3: Install the ODBC Driver 18 for SQL Server
Run the following command:
brew install --no-quarantine msodbcsql18
Note: The --no-quarantine flag is used to avoid macOS security restrictions that can block the driver.

#### Step 4: (Optional) Install unixODBC tools
If you want to use tools like odbcinst to inspect installed drivers, run:
brew install unixodbc

#### Step 5: Verify that the driver was installed
To list installed ODBC drivers, run:
odbcinst -q -d
You should see something like:
[ODBC Driver 18 for SQL Server]

## 🗃️ Installing SQL Server

### 🪟 For Windows

1. Download and install SQL Server Management Studio (SSMS):  
   [https://aka.ms/ssmsfullsetup](https://aka.ms/ssmsfullsetup)

2. Use the following connection details:

   - **Server**: `dataoperationsil.database.windows.net`  
   - **User**: `workshop_user`  
   - **Password**: `YourStrongPassword123`

---

### 🍎 For Mac

1. Install **Azure Data Studio**:  
   [Download Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/download)

2. Open Azure Data Studio and click **"New Connection"**.

3. Fill in the connection details:

   - **Server**: `dataoperationsil.database.windows.net`  
   - **Database**: `python_workshop`  
   - **Authentication Type**: `SQL Login`  
   - **User name**: `workshop_user`  
   - **Password**: `YourStrongPassword123`

4. Click **"Connect"** – and start querying.



## Test Connection to Database in Python:
Run this code in Jupyter Notebook:
      import pyodbc
      
      server = 'dataoperationsil.database.windows.net'   # no https
      database = 'python_workshop'
      username = 'workshop_user'
      password = 'StrongPassword123!'
      driver = '{ODBC Driver 18 for SQL Server}'
      
      connection_string = f'''
          DRIVER={driver};
          SERVER={server};
          DATABASE={database};
          UID={username};
          PWD={password};
          Encrypt=yes;
          TrustServerCertificate=no;
          Connection Timeout=30;
      '''
      
      conn = pyodbc.connect(connection_string)
      cursor = conn.cursor()
      
      pd.read_sql("SELECT * FROM employees", con=engine)
   





## 🦙 Installing **Ollama** and Downloading **TinyLlama**

This guide shows how to install **Ollama**—a local LLM runtime—for macOS, Windows, and Linux, and how to download the **TinyLlama** model. Follow the steps for **your** operating system.

> **TinyLlama** is a 1.1 B-parameter model that runs comfortably on most modern laptops (≈ 4 GB VRAM or 8 GB system RAM).

🪟 Windows Installation
1. Install Ollama
Go to https://ollama.com/download
Download the Windows Installer
Run the .exe file and complete the installation
Launch the Ollama app and keep it running in the background

2. Download the TinyLlama model
Open Command Prompt and run: ollama run tinyllama

## 🍎 macOS Installation

### 1. Install Ollama

You can install Ollama using **Homebrew** or download the app directly.

**Option 1: Homebrew (Recommended)**
bash: brew install ollama

Option 2: DMG Installer
Go to https://ollama.com/download/Ollama.dmg
Open the .dmg file and drag Ollama to your Applications folder
Launch Ollama and keep it running in the background

2. Download the TinyLlama model -
   Once ollama is installed run this is the Terminal: ollama run tinyllama




draft for continuation:
install DB for SQLite:
https://sqlitebrowser.org/dl/
Load .db file there
