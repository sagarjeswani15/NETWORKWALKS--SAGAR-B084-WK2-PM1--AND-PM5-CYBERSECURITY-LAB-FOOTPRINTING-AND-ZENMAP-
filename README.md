# NETWORKWALKS--SAGAR-B084-WK2-PM1--AND-PM5-CYBERSECURITY-LAB-FOOTPRINTING-AND-ZENMAP-
This is repository for networkwalks cybersecurityinternship showing my work on Footprinting and Zenmap
# NetworkWalks Week 2 Cybersecurity Lab

**Student:** Sagar Jeswani[cite: 73]  
**Batch:** B084 (Networkwalks Cybersecurity & Ethical Hacking Internship)[cite: 73]  
**Week:** 2  

---

## Project Scope

This repository contains the Week 2 practical work completed for the Networkwalks cybersecurity program.

The Week 2 requirement is one elective module + both essential projects. This submission uses:

| Module / Component | Description | Status |
| :--- | :--- | :--- |
| **W2-PM1** | Footprinting with multiple Kali tools[cite: 73] | Completed[cite: 73] |
| **W2-PM5** | Zenmap based Network Scanning[cite: 73] | Completed[cite: 73] |
| **W2-PM-FINAL** | Detailed Report[cite: 73] | Completed[cite: 73] |

> **Note:** PM2 (GHDB), PM3 (Maltego), and PM4 (theHarvester) are elective alternatives and are therefore not required for this submission.

---

## W2-PM1 — Footprinting

Six Kali Linux tools were used against the assigned NetworkWalks target (`networkwalks.com`) on 11 November 2026[cite: 74]:

1. **WHOIS**[cite: 74]
2. **WhatWeb**[cite: 74]
3. **Nslookup**[cite: 74]
4. **Curl** (`curl -I`)[cite: 74]
5. **Wafw00f**[cite: 74]
6. **DNSRecon**[cite: 74]

The exercise documented domain registration information, DNS resolution, web technologies, HTTP response headers, WAF detection, and DNS enumeration results[cite: 74].

### Key Observations

* **Domain & Registrar:** `networkwalks.com` was registered via `GoDaddy.com, LLC` (creation date: 2019-11-06; expiration date: 2027-11-06) with privacy-protected registrant information and active client protection locks (`clientDeleteProhibited`, `clientRenewProhibited`, etc.)[cite: 74]. Name servers were identified as `NS6135.HOSTGATOR.COM` and `NS6136.HOSTGATOR.COM`[cite: 74].
* **Web Tech Fingerprinting:** WhatWeb identified an Apache web server, WordPress 7.1.4, WordPress Download Manager plugin (v3.3.76), Bootstrap 7.1.4, jQuery 3.7.1, Google Tag Manager, contact email (`info@networkwalks.com`), and the `_wpdm_client` cookie (marked `HttpOnly`)[cite: 74].
* **HTTP Headers:** `curl -I https://networkwalks.com` returned an `HTTP/2 200` response, exposing `Server: Apache`, `x-nginx-cache: WordPress`, `x-endurance-cache-level: 0`, and WordPress REST API link headers (`/wp-json/` and `/wp-json/wp/v2/pages/53`)[cite: 74].
* **WAF Detection:** Wafw00f detected **ModSecurity (SpiderLabs)** protecting the web application[cite: 74].
* **DNS Enumeration:** DNSRecon recorded the SOA record, NS records, BIND version strings (`9.16.23-RH`) on both HostGator name servers, the MX record (`mail.networkwalks.com`), TXT records (Google verification & SPF policy), and 8 cPanel autodiscover SRV records[cite: 74, 75]. DNSSEC was confirmed to be unsigned[cite: 74].

The complete command outputs and visual evidence are stored under `PM1-Footprinting/`.

---

## W2-PM5 — Zenmap Network Scanning

Active host discovery was executed using Zenmap (Nmap 7.993) with the **Ping scan** profile (`nmap -sn <local-lab-subnet>`) across the authorized local LAN lab subnet on 12 November 2026[cite: 75].

* **Addresses scanned:** 256[cite: 75]
* **Scan duration:** 8.41 seconds[cite: 75]
* **Hosts reported up:** 3[cite: 75]

### Observed Hosts

| IP Address / Host | Observation & MAC Details |
| :--- | :--- |
| **Local Scan Workstation** | Up (Local Interface / `localhost` in topology)[cite: 75] |
| **Active LAN Host #1** | Up (0.015s latency); MAC `4C:D5:77:5C:BE:E3` (Chongqing Fugui Electronics)[cite: 75] |
| **Active LAN Host #2** | Up (0.015s latency); MAC `3E:17:6D:AA:85:5C` (Unknown / locally administered randomized MAC)[cite: 75] |

The Zenmap topology (Fisheye view) and topology legend were successfully inspected and exported[cite: 75, 80].

---

## Repository Structure

```text
├── PM1-Footprinting/        # Command outputs, logs, and screenshots for W2-PM1
├── PM5-ZenmapScanning/      # Zenmap XML outputs, topology exports, and PDF reports
└── README.md                # Project documentation and summary
