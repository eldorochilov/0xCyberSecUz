# 🌐 Networking Asoslari

> **00-foundations / 02-networking-basics**
> Tarmoqni tushunmasdan turib "hacker" bo'lish mumkin emas — har qanday hujum, paket darajasida sodir bo'ladigan voqeadir.

---

## 🎯 Nima uchun kerak?

Web xavfsizlik, network pentest va hatto reverse engineering'ning katta qismi — tarmoq protokollari qanday ishlashini bilishga tayanadi.

---

## 📚 Mavzular ro'yxati

### 1. OSI va TCP/IP modellari
- 7 qatlamli OSI model — har biri nima uchun kerak
- TCP/IP modeli bilan solishtirish
- Enkapsulatsiya tushunchasi (paket qanday "o'raladi")

### 2. IP manzillar va subnetting
- IPv4 vs IPv6
- Public vs private IP (`192.168.x.x`, `10.x.x.x`)
- Subnet mask, CIDR notatsiyasi (`/24`, `/16`)

### 3. TCP vs UDP
- 3-way handshake (`SYN`, `SYN-ACK`, `ACK`)
- Nega TCP ishonchli, UDP tezroq
- Portlar tushunchasi (well-known, registered, dynamic)

### 4. DNS
- Domen nomi qanday IP'ga aylanadi
- `A`, `AAAA`, `CNAME`, `MX`, `TXT` yozuvlari
- DNS spoofing/poisoning nima ekanligi haqida umumiy tushuncha

### 5. HTTP/HTTPS
- So'rov-javob (request-response) modeli
- Metodlar: `GET`, `POST`, `PUT`, `DELETE`
- Headerlar, cookie, session
- TLS/SSL nima uchun kerak (shifrlash asoslari)

### 6. Muhim tarmoq vositalari
- `ping`, `traceroute`/`tracert`
- `nmap` — port skanerlash asoslari
- `Wireshark`/`tcpdump` — paketlarni tutish va tahlil qilish

### 7. Firewall va NAT
- Firewall qoidalari qanday ishlaydi
- NAT nima uchun kerak (bitta public IP, ko'p ichki qurilma)

---

## 🛠 Amaliyot topshiriqlari

- [ ] `nmap` bilan o'z lokal tarmog'ingizdagi qurilmalarni skanerlang
- [ ] `Wireshark` orqali brauzerdan yuborilgan bitta HTTP so'rovni tutib, tahlil qiling
- [ ] `dig` yoki `nslookup` yordamida bir nechta domenning DNS yozuvlarini tekshiring
- [ ] TCP handshake'ni Wireshark'da vizual ravishda kuzating

---

## 📖 Qo'shimcha manbalar

- *Computer Networking: A Top-Down Approach* — Kurose & Ross
- [cloudflare.com/learning](https://www.cloudflare.com/learning/) — protokollarni sodda tilda tushuntiradi
- Wireshark rasmiy dokumentatsiyasi

---

⬅️ [Orqaga: 01-linux-basics](../01-linux-basics/README.md) | ➡️ [Keyingi: 03-programming-fundamentals](../03-programming-fundamentals/README.md)

