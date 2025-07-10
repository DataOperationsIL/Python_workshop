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




# 🦙 Installing **Ollama** and Downloading **TinyLlama**

This guide shows how to install **Ollama**—a local LLM runtime—for macOS, Windows, and Linux, and how to download the **TinyLlama** model. Follow the steps for **your** operating system.

> **TinyLlama** is a 1.1 B-parameter model that runs comfortably on most modern laptops (≈ 4 GB VRAM or 8 GB system RAM).

---

## 1. Prerequisites

| Requirement | Notes |
|-------------|-------|
| **Disk space** | ~6 GB free (Ollama binaries + TinyLlama model) |
| **CPU / GPU** | Any recent x86-64 or Apple Silicon CPU. GPU optional but improves speed. |
| **OS** | macOS 12+, Windows 10/11 (64-bit), Ubuntu 20.04+ (or compatible) |

---

## 2. Install Ollama

### 2.1 macOS (Intel & Apple Silicon)

```bash
# Homebrew (recommended)
brew install ollama

# or download the .dmg installer
open https://ollama.com/download/Ollama.dmg

