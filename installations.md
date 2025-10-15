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

## 🔌 DB Browser for SQLite
Install [DB Browser for SQLite](https://sqlitebrowser.org/dl/)

Download [workshop_db file](https://github.com/DataOperationsIL/Python_workshop/blob/main/workshop_db.db)

Open DB Browser for SQLite:
1. "Open Database" and load the file
2. Check "Database Structure" tab has all the tables
3. Go to "Execute SQL" tab and run - select * from products limit 10







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





