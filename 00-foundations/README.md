<div align="center">

# 🔵 00 — Foundations (Zamin)

![Daraja](https://img.shields.io/badge/Daraja-Foundations-3B82F6?style=for-the-badge)
![Muddat](https://img.shields.io/badge/Muddat-2--3_oy-3B82F6?style=for-the-badge)

*Kiberxavfsizlikdagi 90% muvaffaqiyatsizlik — zaif zamindan kelib chiqadi*

</div>

> Bu bosqichni shoshilmasdan, chuqur o'tang. Tool ishlatishni bilish oson, lekin **nima uchun** u ishlashini tushunish — bu bosqichning maqsadi.

---

### 🧭 Nega bu bosqich shart?

Ko'p boshlovchilar to'g'ridan-to'g'ri "hacking" videolariga o'tib ketishadi va Metasploit yoki SQLMap kabi tool'larni ishga tushiradi, lekin natija chiqmasa nima qilishni bilishmaydi — chunki ular tizim qanday ishlashini tushunmaydi. Bu bo'lim sizni shu holatdan qutqaradi.

---

## 1️⃣ 🐧 Linux — operatsion tizim darajasida tushunish

<details open>
<summary><b>📂 Fayl tizimi va ruxsatlar</b></summary>
<br>

- `/etc`, `/var`, `/proc`, `/dev`, `/home` — har birining vazifasi
- `ls -la`, `chmod`, `chown`, `umask` — ruxsatlar tizimi (rwx, oktal notatsiya)
- SUID/SGID bitlari — bular privilege escalation'da keyinchalik muhim bo'ladi

</details>

<details open>
<summary><b>⚙️ Process va xizmatlarni boshqarish</b></summary>
<br>

- `ps aux`, `top`/`htop`, `kill`, `pgrep`
- `systemctl` bilan xizmatlarni boshqarish, log'larni `journalctl` orqali ko'rish
- Process nima, PID/PPID, foreground/background jarayonlar (`&`, `jobs`, `fg`, `bg`)

</details>

<details open>
<summary><b>📜 Bash skriptlash</b></summary>
<br>

- Shart operatorlari (`if`, `case`), tsikllar (`for`, `while`)
- Matn qayta ishlash: `grep`, `sed`, `awk`, `cut`, `sort`, `uniq`
- Pipe (`|`) va redirection (`>`, `>>`, `2>&1`) mantig'i

> 🎯 **Mashq:** log faylidan muayyan IP manzillarni ajratib olib, chastotasi bo'yicha saralaydigan skript yozing

</details>

<details open>
<summary><b>🖥️ Muhitni o'zingiz sozlang</b></summary>
<br>

- Arch Linux yoki Debian'ni virtual mashina (VirtualBox/QEMU) yoki WSL'da o'rnating
- Dotfiles (`.bashrc`, `.vimrc`/`.config/nvim`) ni qo'lda sozlang — GUI konfiguratsiya vositalaridan qoching
- `tmux` yoki `screen` bilan terminal sessiyalarini boshqarishni o'rganing

</details>

> 💡 **Nima uchun muhim:** deyarli barcha xavfsizlik tool'lari Linux'da ishlaydi, ko'p server infratuzilmasi Linux asosida qurilgan, va CTF muhitlarining aksariyati Linux konteynerlari.

---

## 2️⃣ 🌐 Tarmoq (Networking) — paketlar darajasida tushunish

<details open>
<summary><b>📡 Modellar va asosiy protokollar</b></summary>
<br>

- OSI 7 qatlam vs TCP/IP 4 qatlam modeli — har biri qanday vazifa bajaradi
- IP manzillash, subnetting (CIDR notatsiya, masalan `/24`), IPv4 vs IPv6
- TCP 3-tomonlama handshake (SYN, SYN-ACK, ACK) va UDP bilan farqi
- DNS ishlash mexanizmi: so'rov qanday resolve bo'ladi (recursive vs iterative)
- HTTP/HTTPS: request/response tuzilishi, headerlar, status kodlari, TLS handshake asoslari

</details>

<details open>
<summary><b>🔧 Amaliy tool'lar</b></summary>
<br>

| Tool | Vazifasi |
|---|---|
| `ip addr` / `ip route` | Tarmoq interfeysi va marshrutlash holatini ko'rish |
| `ss -tulnp` | Ochiq portlar va socket holatini ko'rish |
| `tcpdump` / Wireshark | Trafikni ushlab, tahlil qilish |
| `nmap` | Host/port skanerlash (`-sV`, `-sC`, `-sS`) |
| `netcat` (`nc`) | Port tinglash, fayl uzatish, oddiy backdoor tushunchasi |

</details>

**🎯 Mashq loyihalari:**
1. Python yoki C'da oddiy TCP client-server dastur yozing (socket API orqali)
2. `tcpdump` bilan brauzeringizdagi HTTP so'rovni ushlab, paket tuzilishini qo'lda tahlil qiling
3. Uy tarmog'ingizni `nmap` bilan skanerlang va natijani tahlil qiling *(faqat o'zingizga tegishli tarmoqda!)*

---

## 3️⃣ 💻 Dasturlash — vositalar emas, tushunish uchun

<details open>
<summary><b>🔴 C tili (eng muhim)</b></summary>
<br>

Kiberxavfsizlikda, ayniqsa binary exploitation va reverse engineeringda C bilmasdan chuqurlashib bo'lmaydi:
- O'zgaruvchilar, tiplar, funksiyalar, ko'rsatkichlar (pointers)
- Xotira modeli: stack vs heap, `malloc`/`free`, xotira sizishi (memory leak)
- Massivlar va pointer arifmetikasi orasidagi bog'liqlik
- Kompilyatsiya jarayoni: preprocessing → compilation → assembly → linking (`gcc -E`, `-S`, `-c`)

📖 **Kitob:** *The C Programming Language* (K&R) — qisqa, lekin har bir bo'limi muhim.

</details>

<details open>
<summary><b>🐍 Python (instrument sifatida)</b></summary>
<br>

- Asosiy sintaksis, fayllar bilan ishlash, tarmoq so'rovlari (`requests`, `socket`)
- Avtomatlashtirish uchun skriptlar yozish
- Keyinchalik `pwntools` va `scapy` kabi kutubxonalar shu asosda ishlaydi

</details>

<details>
<summary><b>⚙️ (Ixtiyoriy) Assembly'ga kirish</b></summary>
<br>

- x86_64 yoki ARM64 assembly'ning eng sodda qismlarini ko'rib chiqing (registrlar, `mov`, `add`, `syscall`)
- Bu — [`06-arm64-asm`](../06-arm64-asm/README.md) bo'limida chuqurroq davom etadi

</details>

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak

- [ ] Linux terminalida GUI'siz to'liq ishlay olasiz (fayl, process, xizmat boshqaruvi)
- [ ] Bash skript yozib, matnni avtomatik qayta ishlay olasiz
- [ ] TCP va UDP orasidagi farqni, HTTP so'rovining tuzilishini tushuntirib bera olasiz
- [ ] `nmap`, `tcpdump`, `netcat` bilan asosiy amaliy vazifalarni bajara olasiz
- [ ] C'da pointer va xotira bilan ishlaydigan oddiy dastur yoza olasiz

---

## 📚 Resurslar

| Resurs | Turi | Izoh |
|---|:---:|---|
| OverTheWire: Bandit | 🎮 Praktika | Linux+CLI asoslarini o'rgatuvchi eng yaxshi kirish nuqtasi |
| *The Linux Programming Interface* | 📖 Kitob | Linux tizim dasturlash bo'yicha eng to'liq manba |
| *The C Programming Language* (K&R) | 📖 Kitob | C tilining klassik darsligi |
| Beej's Guide to Network Programming | 📘 Qo'llanma | Socket dasturlash bo'yicha bepul va tushunarli |
| Professor Messer (Network+) | 🎥 Video kurs | Tarmoq asoslarini vizual tushuntiradi |

---

<div align="center">

**Keyingi qadam →** [🟢 01-beginner](../01-beginner/README.md)

</div>

