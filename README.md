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
## GAU (Get All) URL Collection
Collects URLs using GAU and saves them to a file.
```bash
echo example.com | gau --mc 200 | urldedupe >urls.txtcat urls.txt | grep -E ".php|.asp|.aspx|.jspx|.jsp" | grep '=' | sort > output.txtcat output.txt | sed 's/=.*/=/' >final.txt
```
## Advanced URL Fetching
Collects URLs from various sources and saves them to a file.
```bash
echo example.com | katana -d 5 -ps -pss waybackarchive,commoncrawl,alienvault -f qurl | urldedupe >output.txtkatana -u https://example.com -d 5 | grep '=' | urldedupe | anew output.txtcat output.txt | sed 's/=.*/=/' >final.txt
```
## Sensitive File Detection
Detects sensitive files on the web server.
```bash
cat allurls.txt | grep -E "\.xls|\.xml|\.xlsx|\.json|\.pdf|\.sql|\.doc|\.docx|\.pptx|\.txt|\.zip|\.tar\.gz|\.tgz|\.bak|\.7z|\.rar|\.log|\.cache|\.secret|\.db|\.backup|\.yml|\.gz|\.config|\.csv|\.yaml|\.md|\.md5"
```
## Information Disclosure Scanner
Checks for information disclosure vulnerabilities using a scanner.
```bash
echo https://example.com | gau | grep -E "\.(xls|xml|xlsx|json|pdf|sql|doc|docx|pptx|txt|zip|tar\.gz|tgz|bak|7z|rar|log|cache|secret|db|backup|yml|gz|config|csv|yaml|md|md5|tar|xz|7zip|p12|pem|key|crt|csr|sh|pl|py|java|class|jar|war|ear|sqlitedb|sqlite3|dbf|db3|accdb|mdb|sqlcipher|gitignore|env|ini|conf|properties|plist|cfg)$"
```
## API Key Finder
Searches for exposed API keys and tokens in JavaScript files.
```bash
cat allurls.txt | grep -E "\.js$" | httpx-toolkit -mc 200 -content-type | grep -E "application/javascript|text/javascript" | cut -d' ' -f1 | xargs -I% curl -s % | grep -E "(API_KEY|api_key|apikey|secret|token|password)"
```


