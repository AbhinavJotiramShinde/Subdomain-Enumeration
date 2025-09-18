# DNS & Subdomain Enumeration Scripts

This repository contains **two Python scripts** that help you perform basic reconnaissance on a target domain:

1. '**dns_enum.py** – Enumerates common DNS record types for a given domain.  
2. **subdomain_enum.py** – Performs brute-force subdomain enumeration using a wordlist.


# Files:

| File | Description |
|------|------------|
| `dns_enum.py` | Queries a domain for common DNS records (A, AAAA, CNAME, MX, TXT, SOA). |
| `subdomain_enum.py` | Uses a subdomain wordlist to discover live subdomains via HTTP requests. |
| `subdomain.txt` | Your custom list of potential subdomains to brute-force. |
| `discovered_subdomains.txt` | Auto-generated file containing all successfully discovered subdomains. |


# Requirements

- Python 3.7+
- The following Python packages:
  pip install dnspython requests

  
# Usage:

1.
DNS Enumeration:
Run the script to fetch DNS records for the target domain:
python dns_enum.py
Default target: youtube.com
To change the target, edit the target_domain variable in the script.
It will attempt to retrieve the following record types:

A
AAAA
CNAME
MX
TXT
SOA


2.
Subdomain Enumeration
Make sure you have a subdomain.txt wordlist in the same directory:
python subdomain_enum.py
The script checks each subdomain in parallel using multi-threading.
Discovered live subdomains are printed to the console and saved in:
discovered_subdomains.txt

# How It Works:
1. DNS Enumeration
Uses the dnspython library’s dns.resolver.Resolver() to query DNS servers for common record types.
Prints each record if available; skips if no answer is returned.
2. Subdomain Enumeration
Reads potential subdomains from subdomain.txt.
For each subdomain:
Sends an HTTP GET request to http://<subdomain>.<domain>.
If the request succeeds, logs the discovered subdomain.
Uses Python’s threading module and a Lock to handle concurrent writes to the output file.

## Legal Disclaimer:
This project is intended for educational and ethical security testing only.
Do not run these scripts on domains you do not own or do not have explicit permission to test.

Author: Abhinav Jotirma Shinde
The author is not responsible for any misuse.

