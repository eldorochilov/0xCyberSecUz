# 00 — Foundations (Zamin)

> Bu bosqichni shoshilmasdan, chuqur o'tang. Kiberxavfsizlikdagi 90% muvaffaqiyatsizlik — mana shu zaminning zaif bo'lishidan kelib chiqadi. Tool ishlatishni bilish oson, lekin **nima uchun** u ishlashini tushunish — bu bosqichning maqsadi.

## Nega bu bosqich shart?

Ko'p boshlovchilar to'g'ridan-to'g'ri "hacking" videolariga o'tib ketishadi va Metasploit yoki SQLMap kabi tool'larni ishga tushiradi, lekin natija chiqmasa nima qilishni bilishmaydi — chunki ular tizim qanday ishlashini tushunmaydi. Bu bo'lim sizni shu holatdan qutqaradi.

---

## 1. Linux — operatsion tizim darajasida tushunish

### 1.1 Fayl tizimi va ruxsatlar
- `/etc`, `/var`, `/proc`, `/dev`, `/home` — har birining vazifasi
- `ls -la`, `chmod`, `chown`, `umask` — ruxsatlar tizimi (rwx, oktal notatsiya)
- SUID/SGID bitlari — bular privilege escalation'da keyinchalik muhim bo'ladi

### 1.2 Process va xizmatlarni boshqarish
- `ps aux`, `top`/`htop`, `kill`, `pgrep`
- `systemctl` bilan xizmatlarni boshqarish, log'larni `journalctl` orqali ko'rish
- Process nima, PID/PPID, foreground/background jarayonlar (`&`, `jobs`, `fg`, `bg`)

### 1.3 Bash skriptlash
- Shart operatorlari (`if`, `case`), tsikllar (`for`, `while`)
- Matn qayta ishlash: `grep`, `sed`, `awk`, `cut`, `sort`, `uniq`
- Pipe (`|`) va redirection (`>`, `>>`, `2>&1`) mantig'i
- **Mashq:** log faylidan muayyan IP manzillarni ajratib olib, chastotasi bo'yicha saralaydigan skript yozing

### 1.4 Muhitni o'zingiz sozlang
- Arch Linux yoki Debian'ni virtual mashina (VirtualBox/QEMU) yoki WSL'da o'rnating
- Dotfiles (`.bashrc`, `.vimrc`/`.config/nvim`) ni qo'lda sozlang — GUI konfiguratsiya vositalaridan qoching
- `tmux` yoki `screen` bilan terminal sessiyalarini boshqarishni o'rganing

**Nima uchun muhim:** deyarli barcha xavfsizlik tool'lari Linux'da ishlaydi, ko'p server infratuzilmasi Linux asosida qurilgan, va CTF muhitlarining aksariyati Linux konteynerlari.

---

## 2. Tarmoq (Networking) — paketlar darajasida tushunish

### 2.1 Modellar va asosiy protokollar
- OSI 7 qatlam vs TCP/IP 4 qatlam modeli — har biri qanday vazifa bajaradi
- IP manzillash, subnetting (CIDR notatsiya, masalan `/24`), IPv4 vs IPv6
- TCP 3-tomonlama handshake (SYN, SYN-ACK, ACK) va UDP bilan farqi (nega DNS/video streaming UDP ishlatadi)
- DNS ishlash mexanizmi: so'rov qanday resolve bo'ladi (recursive vs iterative)
- HTTP/HTTPS: request/response tuzilishi, headerlar, status kodlari, TLS handshake asoslari

### 2.2 Amaliy tool'lar
- `ip addr`, `ip route`, `ss -tulnp` — o'z tizimingiz tarmoq holatini ko'rish
- `tcpdump` va Wireshark — trafikni ushlab, tahlil qilish
- `nmap` — host/port skanerlash (`-sV`, `-sС`, `-sS` farqlari)
- `netcat` (`nc`) — "tarmoqning shveytsariya pichog'i": port tinglash, fayl uzatish, oddiy backdoor tushunchasi

### 2.3 Mashq loyihalari
1. Python yoki C'da oddiy TCP client-server dastur yozing (socket API orqali)
2. `tcpdump` bilan o'z brauzeringizdagi HTTP so'rovni ushlab, paket tuzilishini qo'lda tahlil qiling
3. Uy tarmog'ingizni `nmap` bilan skanerlang va natijani tushunib tahlil qiling (faqat o'zingizga tegishli tarmoqda!)

---

## 3. Dasturlash — vositalar emas, tushunish uchun

### 3.1 C tili (eng muhim)
Kiberxavfsizlikda, ayniqsa binary exploitation va reverse engineeringda C bilmasdan chuqurlashib bo'lmaydi:
- O'zgaruvchilar, tiplar, funksiyalar, ko'rsatkichlar (pointers)
- Xotira modeli: stack vs heap, `malloc`/`free`, xotira sizishi (memory leak)
- Massivlar va pointer arifmetikasi orasidagi bog'liqlik
- Kompilyatsiya jarayoni: preprocessing → compilation → assembly → linking (`gcc -E`, `-S`, `-c`)

**Kitob:** *The C Programming Language* (K&R) — qisqa, lekin har bir bo'limi muhim.

### 3.2 Python (instrument sifatida)
- Asosiy sintaksis, fayllar bilan ishlash, tarmoq so'rovlari (`requests`, `socket`)
- Avtomatlashtirish uchun skriptlar yozish (masalan, ko'p fayl ustida takroriy amal)
- Keyinchalik `pwntools` va `scapy` kabi kutubxonalar shu asosda ishlaydi

### 3.3 (Ixtiyoriy, lekin tavsiya) Assembly'ga kirish
- Agar protsessor darajasida tushunishni istasangiz, x86_64 yoki ARM64 assembly'ning eng sodda qismlarini ko'rib chiqing (registrlar, `mov`, `add`, `syscall`)
- Bu — `06-arm64-asm` bo'limida chuqurroq davom etadi

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak:

- [ ] Linux terminalida GUI'siz to'liq ishlay olasiz (fayl, process, xizmat boshqaruvi)
- [ ] Bash skript yozib, matnni avtomatik qayta ishlay olasiz
- [ ] TCP va UDP orasidagi farqni, HTTP so'rovining tuzilishini tushuntirib bera olasiz
- [ ] `nmap`, `tcpdump`, `netcat` bilan asosiy amaliy vazifalarni bajara olasiz
- [ ] C'da pointer va xotira bilan ishlaydigan oddiy dastur yoza olasiz

## 📚 Resurslar

| Resurs | Turi | Izoh |
|---|---|---|
| OverTheWire: Bandit | Praktika | Linux+CLI asoslarini o'rgatuvchi eng yaxshi kirish nuqtasi |
| *The Linux Programming Interface* | Kitob | Linux tizim dasturlash bo'yicha eng to'liq manba |
| *The C Programming Language* (K&R) | Kitob | C tilining klassik darsligi |
| Beej's Guide to Network Programming | Qo'llanma | Socket dasturlash bo'yicha bepul va tushunarli |
| Professor Messer (Network+) | Video kurs | Tarmoq asoslarini vizual tushuntiradi |

**Keyingi qadam:** [`01-beginner/`](../01-beginner/README.md) — xavfsizlik asoslari va birinchi CTF tajribangiz.

