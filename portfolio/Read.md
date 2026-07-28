# Metasploitable2 Web Enumeration Lab

A hands-on cybersecurity lab demonstrating **reconnaissance and web enumeration techniques** against the intentionally vulnerable **Metasploitable2** virtual machine using **Kali Linux (WSL)**.

## Environment

* **Attacker:** Kali Linux (WSL)
* **Target:** Metasploitable2
* **Platform:** Oracle VirtualBox

## Tools Used

* Nmap
* Gobuster
* curl
* Firefox
* DVWA

## Key Activities

* Host discovery with `ping`
* Service enumeration with `nmap -sV`
* Web reconnaissance using `curl`
* Directory brute-forcing with `gobuster`
* Recursive enumeration of discovered paths
* Information disclosure analysis (`phpinfo.php`)
* DVWA authentication and parameter manipulation

## Notable Findings

* Apache 2.2.8 exposed on port 80
* Multiple vulnerable web applications available
* Directory indexing enabled on `/test/`
* PHP configuration disclosure via `phpinfo.php`
* Dynamic database-backed behavior observed in DVWA (`id=1-5`)

## Learning Outcomes

This lab reinforced:

* Structured reconnaissance methodology
* Iterative enumeration techniques
* The importance of information disclosure findings
* Practical web application testing workflows
* Evidence collection and professional documentation practices

> **Disclaimer:** All activities were performed inside a controlled local lab environment using intentionally vulnerable systems for educational purposes only.
