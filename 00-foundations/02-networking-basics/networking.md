<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:2C5364,100:00FF87&height=220&section=header&text=02%20-%20Networking%20Basics&fontSize=48&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Paketlardan%20tortib%20protokollargacha&descAlignY=58&descSize=18" width="100%"/>

<p>
  <img src="https://img.shields.io/badge/Level-Beginner-brightgreen?style=for-the-badge&logo=leveldb&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP%2FIP-003366?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Nmap-000000?style=for-the-badge&logo=nmap&logoColor=green"/>
  <img src="https://img.shields.io/badge/Linux-000000?style=for-the-badge&logo=linux&logoColor=white"/>
</p>

<p>
  <img src="https://img.shields.io/badge/Til-O'zbek-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Vaqt-8--12%20soat-yellow?style=flat-square"/>
  <img src="https://img.shields.io/badge/Bo'lim-00--foundations-purple?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Active-success?style=flat-square"/>
</p>

</div>

## 📖 Kirish

Har qanday xavfsizlik mutaxassisi — u pentester bo'ladimi, SOC analitigi yoki malware tadqiqotchisi — tarmoq qanday ishlashini chuqur bilishi shart. Hujumlar ham, himoya ham tarmoq darajasida sodir bo'ladi: paketlarni tinglash, portlarni skanerlash, trafikni tahlil qilish — hammasi shu bo'limdagi bilimlarga tayanadi.

Bu qo'llanma sizni "IP nima o'zi" darajasidan "tcpdump bilan real trafikni tahlil qilaman" darajasiga olib chiqadi.

---

## 🗂️ Mavzular xaritasi

<table>
<tr><th>№</th><th>Mavzu</th><th>Nimani o'rganasiz</th></tr>
<tr><td>1</td><td><a href="#1-osi-va-tcpip-modellari">OSI va TCP/IP modellari</a></td><td>7 qatlam, inkapsulyatsiya</td></tr>
<tr><td>2</td><td><a href="#2-ip-manzillash-va-subnetting">IP manzillash va subnetting</a></td><td>IPv4, CIDR, subnet mask</td></tr>
<tr><td>3</td><td><a href="#3-portlar-va-protokollar">Portlar va protokollar</a></td><td>TCP vs UDP, mashhur portlar</td></tr>
<tr><td>4</td><td><a href="#4-tcp-handshake-va-ulanish-hayoti">TCP handshake</a></td><td>3-way handshake, flags</td></tr>
<tr><td>5</td><td><a href="#5-dns-domen-nomlar-tizimi">DNS</a></td><td>Domen → IP aylantirish jarayoni</td></tr>
<tr><td>6</td><td><a href="#6-dhcp-va-arp">DHCP va ARP</a></td><td>Avtomatik IP olish, MAC↔IP</td></tr>
<tr><td>7</td><td><a href="#7-http--https-asoslari">HTTP / HTTPS</a></td><td>So'rov-javob, headerlar, TLS</td></tr>
<tr><td>8</td><td><a href="#8-linuxda-tarmoq-buyruqlari">Tarmoq buyruqlari (chuqur)</a></td><td>ip, ss, curl, dig, traceroute</td></tr>
<tr><td>9</td><td><a href="#9-paketlarni-ushlash-tcpdump--wireshark">Paketlarni ushlash</a></td><td>tcpdump, Wireshark asoslari</td></tr>
<tr><td>10</td><td><a href="#10-port-skanerlash-nmap">Port skanerlash (Nmap)</a></td><td>Skan turlari, servis aniqlash</td></tr>
<tr><td>11</td><td><a href="#11-firewall-va-vpn">Firewall va VPN</a></td><td>ufw/iptables, tunnellash</td></tr>
<tr><td>12</td><td><a href="#12-mashhur-tarmoq-hujumlariga-kirish">Tarmoq hujumlariga kirish</a></td><td>MITM, ARP spoofing, sniffing</td></tr>
</table>

---

## 1. OSI va TCP/IP modellari

**OSI modeli** — tarmoq ishlashini 7 qatlamga bo'lib tushuntiruvchi nazariy model:

| Qatlam | Nomi | Misol |
|---|---|---|
| 7 | Application | HTTP, DNS, FTP |
| 6 | Presentation | Shifrlash, kodlash (SSL/TLS) |
| 5 | Session | Sessiyalarni boshqarish |
| 4 | Transport | TCP, UDP |
| 3 | Network | IP, ICMP, routing |
| 2 | Data Link | Ethernet, MAC manzil, switch |
| 1 | Physical | Kabel, signal, Wi-Fi to'lqin |

Amaliyotda ko'proq **TCP/IP modeli** (4 qatlam: Application, Transport, Internet, Network Access) ishlatiladi — u OSI'ning soddalashtirilgan varianti.

> 🎯 **Eslab qolish uchun:** Har bir qatlam ma'lumotni "o'raydi" (encapsulation) — Application qatlamdagi ma'lumot pastga tushar ekan, header'lar qo'shilib boradi, natijada oxirida bitlar (0/1) ko'rinishida jismoniy kabel orqali yuboriladi.

---

## 2. IP manzillash va subnetting

**IPv4 manzil** — 32 bitli, 4 ta oktetdan iborat: `192.168.1.10`

| Manzil turi | Diapazon | Ishlatilishi |
|---|---|---|
| Private (A) | 10.0.0.0 – 10.255.255.255 | Katta ichki tarmoqlar |
| Private (B) | 172.16.0.0 – 172.31.255.255 | O'rta tarmoqlar |
| Private (C) | 192.168.0.0 – 192.168.255.255 | Uy/ofis tarmoqlari |
| Loopback | 127.0.0.1 | O'z mashinangiz |

**CIDR notatsiya:** `192.168.1.0/24` — bu yerda `/24` subnet maskani bildiradi (255.255.255.0), ya'ni 256 ta manzil (254 ta foydalanish mumkin) mavjudligini anglatadi.

| CIDR | Subnet mask | Manzillar soni |
|---|---|---|
| /24 | 255.255.255.0 | 256 |
| /16 | 255.255.0.0 | 65,536 |
| /8 | 255.0.0.0 | 16,777,216 |

```bash
ipcalc 192.168.1.0/24      # subnet hisob-kitobi (o'rnatish: apt install ipcalc)
```

---

## 3. Portlar va protokollar

**Port** — bitta IP manzil ichida turli xizmatlarni ajratib turuvchi 0–65535 oralig'idagi raqam.

| Port | Protokol | Xizmat |
|---|---|---|
| 20/21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP (email yuborish) |
| 53 | TCP/UDP | DNS |
| 67/68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |

**TCP vs UDP:**

| Xususiyat | TCP | UDP |
|---|---|---|
| Ulanish | Ulanish o'rnatiladi (connection-oriented) | Ulanishsiz |
| Ishonchlilik | Kafolatlangan yetkazish | Kafolat yo'q |
| Tezlik | Sekinroq | Tezroq |
| Misol | HTTP, SSH, FTP | DNS, video striming, VoIP |

---

## 4. TCP handshake va ulanish hayoti

TCP ulanishi **3-way handshake** orqali o'rnatiladi:

```
Client → SYN      → Server     (ulanish so'raladi)
Client ← SYN-ACK  ← Server     (server rozilik bildiradi)
Client → ACK      → Server     (ulanish tasdiqlanadi)
```

Bu jarayon `nmap`dagi **SYN scan (-sS)** asosini tashkil qiladi — chunki to'liq handshake tugallanmasa, ba'zi loglar yozilmasligi mumkin ("stealth scan" deb ataladi).

**TCP flags:** `SYN`, `ACK`, `FIN` (yopish), `RST` (majburiy uzish), `PSH`, `URG`.

---

## 5. DNS (Domen nomlar tizimi)

DNS — inson o'qiy oladigan domen nomlarini (`google.com`) IP manzilga (`142.250.x.x`) aylantiruvchi "tarmoqning telefon kitobi".

```bash
dig google.com              # to'liq DNS so'rov ma'lumoti
nslookup google.com         # oddiyroq variant
host google.com             # tezkor natija
dig google.com MX           # mail serverlarni ko'rish
```

**DNS so'rov jarayoni:** Brauzer → Resolver → Root server → TLD server (.com) → Authoritative server → IP qaytariladi.

---

## 6. DHCP va ARP

**DHCP** — qurilmangizga avtomatik IP, shlyuz va DNS manzillarini beradigan protokol (4 bosqich: Discover → Offer → Request → Ack, qisqacha **DORA**).

**ARP (Address Resolution Protocol)** — IP manzilni MAC manzilga bog'laydi (lokal tarmoqda).

```bash
arp -a               # ARP jadvalini ko'rish
ip neigh              # zamonaviy muqobili
```

> ⚠️ ARP protokoli autentifikatsiyasiz ishlaydi — shu sababli **ARP spoofing** hujumlari mumkin (12-bo'limda ko'ramiz).

---

## 7. HTTP / HTTPS asoslari

```bash
curl -I https://example.com        # faqat headerlarni ko'rish
curl -v https://example.com        # to'liq so'rov-javob jarayoni
```

**Muhim HTTP metodlari:** `GET`, `POST`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

**Status kodlar:**

| Kod | Ma'nosi |
|---|---|
| 200 | OK |
| 301/302 | Redirect |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Server Error |

**HTTPS** = HTTP + TLS/SSL shifrlash. TLS handshake orqali server va client umumiy shifrlash kalitiga kelishib oladi, shundan keyingina ma'lumot shifrlangan holda uzatiladi.

---

## 8. Linuxda tarmoq buyruqlari (chuqur)

| Buyruq | Vazifasi |
|---|---|
| `ip a` | Interfeyslar va IP manzillar |
| `ip route` | Routing jadvali |
| `ss -tulpn` | Ochiq portlar + jarayonlar |
| `ping -c 4 host` | 4 marta ping yuborish |
| `traceroute host` | Paket qaysi yo'l bilan borishini ko'rish |
| `mtr host` | traceroute + ping birlashgan real-vaqt vositasi |
| `curl -O url` | Faylni yuklab olish |
| `netstat -an` | Eski, lekin hali ishlaydigan variant |

---

## 9. Paketlarni ushlash: tcpdump & Wireshark

```bash
sudo tcpdump -i eth0                     # barcha trafikni ko'rish
sudo tcpdump -i eth0 port 80             # faqat 80-port trafigi
sudo tcpdump -i eth0 -w capture.pcap     # faylga yozish
sudo tcpdump -r capture.pcap             # yozilgan faylni o'qish
```

**Wireshark** — GUI vositasi, `.pcap` fayllarni vizual tahlil qilish uchun. Filtr misollari: `http`, `ip.addr == 192.168.1.1`, `tcp.port == 443`.

---

## 10. Port skanerlash (Nmap)

```bash
nmap 192.168.1.1              # oddiy skan
nmap -sS 192.168.1.1          # SYN (stealth) skan — sudo talab qiladi
nmap -sV 192.168.1.1          # servis versiyasini aniqlash
nmap -O 192.168.1.1           # OS aniqlash
nmap -p 1-1000 192.168.1.1    # port diapazonini belgilash
nmap -A 192.168.1.1           # to'liq agressiv skan (OS+versiya+skript)
nmap --script vuln 192.168.1.1   # zaifliklarni skanerlash skriptlari
```

> ⚠️ **Muhim:** O'zingizga tegishli bo'lmagan tarmoqlarni skanerlash **noqonuniy** — faqat o'z laboratoriyangiz yoki ruxsat berilgan (CTF, bug bounty) muhitda ishlating.

---

## 11. Firewall va VPN

```bash
sudo ufw enable
sudo ufw allow 22/tcp
sudo ufw deny 23/tcp
sudo ufw status verbose

sudo iptables -L -n -v            # qoidalarni ko'rish (past darajali)
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

**VPN** — trafikni shifrlangan "tunnel" orqali uzatadi, IP manzilingizni yashiradi va ochiq Wi-Fi'da xavfsizlikni oshiradi. Mashhur protokollar: OpenVPN, WireGuard.

---

## 12. Mashhur tarmoq hujumlariga kirish

| Hujum | Mohiyati |
|---|---|
| **MITM (Man-in-the-Middle)** | Ikki tomon o'rtasiga kirib, trafikni tinglash/o'zgartirish |
| **ARP Spoofing** | Soxta ARP javoblari yuborib, trafikni o'ziga yo'naltirish |
| **DNS Spoofing** | Soxta DNS javob berish orqali qalbaki saytga yo'naltirish |
| **SYN Flood** | Ko'plab SYN so'rov yuborib serverni band qilish (DoS) |
| **Packet Sniffing** | Shifrlanmagan trafikni tinglab ma'lumot o'g'irlash |

> 📌 Bu mavzular `03-network-pentest` bo'limida amaliy vositalar (Ettercap, Bettercap) bilan chuqurroq o'rganiladi.

---

## ✅ Amaliy topshiriqlar (checklist)

- [ ] O'z kompyuteringizning IP, subnet mask va default gateway'ini `ip a` va `ip route` orqali aniqlang
- [ ] `dig` yordamida 3 ta turli domenning DNS ma'lumotlarini oling (A, MX, NS)
- [ ] `curl -v` bilan biror saytga so'rov yuboring va headerlarni tahlil qiling
- [ ] Lokal tarmog'ingizda `nmap -sV` bilan qurilmalarni aniqlang (faqat o'zingizga tegishli tarmoqda!)
- [ ] `tcpdump` bilan 1 daqiqalik trafikni ushlab, `.pcap` faylga saqlang
- [ ] Saqlangan `.pcap` faylni Wireshark'da oching va HTTP so'rovlarini filtrlang
- [ ] `ufw` yordamida faqat SSH (22) va HTTPS (443) portlariga ruxsat bering, qolganini yoping
- [ ] TCP 3-way handshake'ni Wireshark orqali vizual kuzatib, SYN/SYN-ACK/ACK paketlarini toping

---

## 📚 Qo'shimcha resurslar

| Manba | Tavsif | Havola |
|---|---|---|
| Nmap Official Docs | To'liq buyruqlar qo'llanmasi | nmap.org/book |
| Wireshark University | Rasmiy Wireshark darslari | wireshark.org |
| Practical Networking | Networking asoslarini oson tushuntiruvchi sayt | practicalnetworking.net |
| TryHackMe: Network Fundamentals | Amaliy, interaktiv xona | tryhackme.com |
| RFC 793 (TCP) | TCP protokolining rasmiy standarti | rfc-editor.org |

---

<div align="center">

⬅️ **Oldingi:** [01-linux-basics](../01-linux-basics/README.md) &nbsp;&nbsp;|&nbsp;&nbsp; **Keyingi:** [03-programming-fundamentals](../03-programming-fundamentals/README.md) ➡️

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00FF87,50:2C5364,100:0F2027&height=120&section=footer" width="100%"/>

</div>

