# 🔧 Oneliner Collection

This repository is a curated collection of useful oneliners penetration testers. Each oneliner is designed to solve specific problems efficiently with a single command.

## 📚 What's Inside?

- 🐧 Linux system administration tricks  
- 🛠️ Command-line tools usage (awk, sed, grep, etc.)  
- 🧪 Penetration testing and security oneliners  
- 📡 Networking and port scanning shortcuts  
- 🐍 Python and Bash oneliners   

## 🚀 Why Use This?

- Save time with ready-to-use one-liners  
- Improve productivity in terminal workflows  
- Learn smart usage of CLI tools  
- Great reference for CTFs, pentests, or scripting tasks  

## 📦 Structure

Each directory or file is categorized based on functionality or tool:

First, download the toolkit from Rootbakar’s repository: [https://github.com/rootbakar/bugbounty-toolkit](https://github.com/rootbakar/bugbounty-toolkit)

## Basic Subdomain Discovery
Discovers subdomains using subfinder with recursive enumeration and saves results to a file.
```bash
subfinder -d example.com -all -recursive > subexample.com.txt
```
## Live Subdomain Filtering
Filters discovered subdomains using httpx and saves the alive ones to a file.
```bash
cat subexample.com.txt | httpx-toolkit -ports 80,443,8080,8000,8888 -threads 200 > subexample.coms_alive.txt
```
