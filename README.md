# 🛡️ Purple Team Lab: Exploitation & Detection of vsftpd 2.3.4 Backdoor

![Badge Kali](https://img.shields.io/badge/Red%20Team-Kali%20Linux-red) ![Badge Metasploit](https://img.shields.io/badge/Framework-Metasploit-blue) ![Badge Blue Team](https://img.shields.io/badge/Blue%20Team-Incident%20Response-green)

## 📋 Executive Summary
Project ini adalah simulasi laboratorium keamanan siber dengan pendekatan **Purple Team** (gabungan Red Team & Blue Team). Tujuan utamanya adalah mengeksploitasi kerentanan kritis pada layanan FTP legacy dan mempraktikkan langkah-langkah *Incident Response* untuk mendeteksi serta menetralkan serangan tersebut secara *real-time*.

**Objektif:**
1.  **Red Team:** Mendapatkan akses *Root* pada target menggunakan celah keamanan yang diketahui.
2.  **Blue Team:** Mengidentifikasi intrusi jaringan dan melakukan terminasi proses berbahaya.

---

## 🛠️ Lab Environment
Semua aktivitas dilakukan dalam jaringan isolasi virtual (Host-only Network) untuk keamanan.

| Role | OS | IP Address | Tools Used |
| :--- | :--- | :--- | :--- |
| **Attacker** | Kali Linux 2024 | `192.168.56.103` | Nmap, Metasploit Framework |
| **Target** | Metasploitable 2 | `192.168.56.101` | Netstat, System Logs, Bash |

---

## ⚔️ Phase 1: Red Team Operations (Offensive)

### 1. Reconnaissance (Network Scanning)
Langkah awal dilakukan dengan pemindaian port menggunakan **Nmap** untuk mengidentifikasi layanan yang berjalan dan versinya.

```bash
nmap -sV 192.168.56.101
