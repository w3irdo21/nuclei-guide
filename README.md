# Nuclei Guide (For Any OS)

Nuclei is a vulnerability scanner by [ProjectDiscovery](https://github.com/projectdiscovery/nuclei).  
This note explains how to install and use Nuclei with templates.  


## 📥 Step 1: Download Nuclei

Go to the [Nuclei Releases page](https://github.com/projectdiscovery/nuclei/releases) and download the ZIP file for your operating system.  
Example for **Linux amd64**:

```bash
wget https://github.com/projectdiscovery/nuclei/releases/download/v3.4.0/nuclei_3.4.0_linux_amd64.zip
unzip nuclei_3.4.0_linux_amd64.zip
mv nuclei /usr/local/bin/
````

Now you can run:

```bash
nuclei -version
```

## 📂 Step 2: Get Templates

Clone the official **nuclei-templates** repository:

```bash
git clone https://github.com/projectdiscovery/nuclei-templates.git ~/nuclei-templates
```

Search for a specific CVE template (example: CVE-2025-4388):

```bash
find ~/nuclei-templates -type f -name "*4388*"
```

## 🚀 Step 3: Run Nuclei

### Scan a single target with a CVE template:

```bash
nuclei -t ~/nuclei-templates/cves/2025/cve-2025-4388-liferay-rxss.yaml -u target.example.com
```

### Scan a list of domains with a custom template:

```bash
nuclei -l domains.txt -t ./CVE-2025-29927-6mile.yaml -fr -stats
```


## ⚡ Flags Explained

* `-u` → Scan a single target
* `-l` → Provide a list of domains (one per line)
* `-t` → Path to template file
* `-fr` → Follow redirects
* `-stats` → Show scan progress in real-time


## ✅ Example

```bash
nuclei -l domains.txt -t ~/nuclei-templates/cves/2025/cve-2025-4388-liferay-rxss.yaml -fr -stats
```

This command scans all domains from `domains.txt` using the selected template, follows redirects, and shows live statistics.
