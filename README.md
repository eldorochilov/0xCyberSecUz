# 0xCyberSecUz
# Kiberxavfsizlik
## Yo'l Xaritasi

> O'zbek tilida kiberxavfsizlikni jiddiy, tizimli va amaliy asosda o'rganish uchun ochiq loyiha. Maqsad — nazariyani emas, **ko'nikmani** shakllantirish: har bir bosqich amaliyot, laboratoriya va real muammolar bilan mustahkamlanadi.

---

## 📌 Loyiha falsafasi

Bu roadmap uchta printsipga asoslanadi:

1. **Fundament birinchi** — tarmoq, operatsion tizim va dasturlash asoslarisiz "hacking" faqat skript ishlatishga aylanadi. Biz avval tizimni tushunamiz, keyin uni sindiramiz.
2. **Qo'l bilan qilish** — har bir mavzu amaliy laboratoriya, CTF masalasi yoki mini-loyiha bilan yakunlanadi. Faqat video ko'rish yoki kitob o'qish yetarli emas.
3. **Pastdan yuqoriga** — yuqori darajadagi tool'lardan (Metasploit, Burp) boshlamaymiz. Avval ular qanday ishlashini tushunamiz: paket qanday yuriladi, protsess xotirada qanday joylashadi, syscall nima.

---

## 🗺️ Umumiy tuzilma (5 bosqich)

| Bosqich | Nomi | Taxminiy muddat | Maqsad |
|---|---|---|---|
| 0 | Zamin (Foundations) | 2–3 oy | Linux, tarmoq, dasturlash asoslari |
| 1 | Beginner | 2–3 oy | Xavfsizlik asoslari, birinchi CTF'lar |
| 2 | Intermediate | 4–6 oy | Web xavfsizlik, tarmoq pentesti, skriptlash |
| 3 | Advanced | 6–9 oy | Binary exploitation, reverse engineering, low-level |
| 4 | Pro | Doimiy | Ixtisoslashuv: pwn, red team, kernel/driver security, tadqiqot |

Har bir bosqich mustaqil emas — ular ustma-ust qatlamlanadi. Masalan, Linux fundamentallarini 0-bosqichda boshlaysiz, lekin 3-bosqichda kernel darajasida qaytib kelasiz.

---

## 🔹 Bosqich 0 — Zamin (Foundations)

### Linux
- Fayl tizimi, ruxsatlar (chmod/chown), process boshqaruvi (ps, kill, systemd)
- Bash skriptlash: shart operatorlari, tsikllar, matn qayta ishlash (grep, sed, awk)
- Arch Linux yoki Debian'da o'rnatishdan boshlab qo'lda sozlash (GUI'dan qochish)
- **Amaliyot:** o'z Linux muhitingizni noldan sozlang (dotfiles, shell, tmux/vim)

### Tarmoq (Networking)
- OSI va TCP/IP modeli, IP/subnetting, routing asoslari
- TCP handshake, UDP farqi, DNS, HTTP/HTTPS ishlash mexanizmi
- Asosiy tool'lar: `ip`, `ss`, `tcpdump`, `nmap`, `netcat`
- **Amaliyot:** Wireshark/tcpdump bilan o'z trafigingizni tahlil qiling; oddiy client-server dasturini socket orqali yozing

### Dasturlash
- **C tili** — kiberxavfsizlik uchun eng muhim til: xotira modeli, pointer'lar, stack/heap farqi
- **Python** — instrument sifatida: avtomatlashtirish, skriptlash, pwntools/scapy uchun zamin
- (Ixtiyoriy, lekin tavsiya etiladi) **Assembly** — x86_64 yoki ARM64, protsessor darajasida tushunish uchun

**Resurslar:** K&R (*The C Programming Language*), *The Linux Programming Interface*, OverTheWire Bandit (Linux+CLI uchun ajoyib kirish nuqtasi)

---

## 🔹 Bosqich 1 — Beginner

- **Xavfsizlik asoslari:** CIA triadasi, threat modeling, umumiy atamalar (CVE, CVSS, zero-day)
- **Kriptografiya asoslari:** simmetrik/asimmetrik shifrlash, hashing, klassik shifrlar (Caesar, Vigenère) va ularga hujumlar
- **Birinchi CTF tajribasi:** OverTheWire (Bandit → Narnia → Krypton), picoCTF
- **Amaliyot loyihasi:** oddiy port scanner yozish (Python yoki C'da, raw socket bilan)

---

## 🔹 Bosqich 2 — Intermediate

### Web xavfsizlik
- OWASP Top 10: SQL injection, XSS, CSRF, SSRF, auth bypass
- Burp Suite bilan ishlash, HTTP request/response'ni qo'lda manipulyatsiya qilish
- **Laboratoriyalar:** PortSwigger Web Security Academy (bepul va eng sifatli), DVWA, TryHackMe web yo'nalishi

### Tarmoq pentesti
- Nmap chuqur skanerlash, xizmatlarni fingerprint qilish
- Active Directory asoslari (Windows muhitlarida keng tarqalgan)
- Privilege escalation texnikalari (Linux va Windows)
- **Platformalar:** TryHackMe, HackTheBox (Easy/Medium mashinalar)

### Skriptlash va avtomatlashtirish
- Python bilan exploit-dev asoslari, scapy bilan paket yasash
- O'z tool'laringizni yozish (recon skriptlari, enum skriptlari)

---

## 🔹 Bosqich 3 — Advanced (Low-level va Binary Exploitation)

Bu — loyihaning eng chuqur va eng qadrli qatlami, ayniqsa C/Assembly zaminiga ega bo'lganlar uchun.

### Binary Exploitation asoslari
- ELF format tuzilishi, `readelf`, `objdump`, `checksec`
- Stack-based buffer overflow, shellcode yozish
- GDB + GEF bilan debugging, breakpoint strategiyalari
- **Laboratoriya:** OverTheWire Narnia, pwn.college, pwnable.kr

### Reverse Engineering
- Statik va dinamik tahlil: Ghidra, radare2/rizin, IDA (yoki bepul alternativalar)
- Anti-debugging va obfuskatsiya texnikalarini tanish
- **Amaliyot:** crackme'larni yechish (crackmes.one)

### Zamonaviy himoya mexanizmlarini yengish
- ASLR, NX/DEP, stack canary, PIE — har birining ishlash prinsipi va bypass strategiyasi
- ROP (Return-Oriented Programming) zanjirlari qurish
- Format string zaifliklari, heap exploitation (use-after-free, double-free)
- **Platforma:** pwntools bilan exploit avtomatlashtirish, ROPgadget/pwntools ROP moduli

### Arxitektura chuqurligi (x86_64 va ARM64)
- Registrlar, calling convention (System V ABI / AAPCS64), syscall konvensiyalari
- C + Assembly aralash loyihalar yozish (masalan, `clang main.c asm.s -o prog`)
- Emulyatsiya: unicorn engine bilan kod bajarilishini tahlil qilish

**Tayanch kitoblar:** *Hacking: The Art of Exploitation*, *Computer Systems: A Programmer's Perspective (CS:APP)*, *Expert C Programming*

---

## 🔹 Bosqich 4 — Pro (Ixtisoslashuv)

Bu bosqichda tor yo'nalish tanlanadi — hammasini bir vaqtda chuqur o'rganib bo'lmaydi:

- **Exploit Development / Pwn:** murakkab heap exploitation, kernel exploitation, fuzzing (AFL++, syzkaller)
- **Kernel / Driver Security:** Linux kernel moduli yozish, rootkit tahlili va aniqlash, *Linux Device Drivers (LDD3)* asosida amaliyot
- **Reverse Engineering (pro):** malware tahlili, ICS/SCADA xavfsizligi, firmware reverse engineering
- **Red Team / Offensive Security:** OSCP darajasidagi ko'nikmalar, C2 infratuzilmasi, Active Directory attack chain
- **Tadqiqot:** yangi CVE qidirish, zero-day tadqiqoti, responsible disclosure jarayoni

Bu bosqichda o'z laboratoriyangiz (masalan, Oracle Cloud / o'zga bulutdagi ARM64 yoki x86_64 instance) muhim rol o'ynaydi — real muhitga yaqin sharoitda ishlash imkonini beradi.

---

## 🧰 Doimiy foydalaniladigan CTF va laboratoriya platformalari

| Platforma | Yo'nalish |
|---|---|
| OverTheWire | Linux, kriptografiya, binary exploitation (Bandit/Narnia/Krypton) |
| picoCTF | Umumiy kirish darajasi, ko'p yo'nalishli |
| TryHackMe | Boshlang'ichdan o'rtaga, yo'naltirilgan yo'llar |
| HackTheBox | O'rta-yuqori daraja, real mashinalar |
| pwn.college | Binary exploitation, chuqur va tizimli |
| pwnable.kr / crackmes.one | Reverse engineering va pwn mashqlari |
| PortSwigger Web Academy | Web xavfsizlik, bepul va eng sifatli |

---

## 📁 Repozitoriy tuzilishi (taklif)

```
0xCyberSecUz/
├── README.md                  # ushbu fayl — asosiy roadmap
├── 00-foundations/             # Linux, tarmoq, C/Python asoslari
├── 01-beginner/                 # xavfsizlik asoslari, birinchi CTF yechimlari
├── 02-web-security/            # OWASP, Burp yozuvlari, writeup'lar
├── 03-network-pentest/         # AD, privesc, tool skriptlari
├── 04-binary-exploitation/     # pwn writeup'lari, exploit skriptlari
├── 05-reverse-engineering/     # crackme yechimlari, tahlillar
├── 06-arm64-asm/                # assembly mashqlari va build workflow
├── resources.md                 # kitoblar, kurslar, havolalar ro'yxati
└── notes/                       # shaxsiy konspektlar, mavzu bo'yicha eslatmalar
```

---

## ✅ Qanday boshlash kerak

1. `00-foundations` papkasidan boshlang — Linux va tarmoqni chuqur bilmasdan keyingi bosqichlarga o'tish vaqt yo'qotish bo'ladi.
2. Har bir mavzu bo'yicha **kamida bitta amaliy masala** yeching va uni `notes/` yoki mos papkaga writeup sifatida yozing — bu bilim mustahkamlanadi va portfolio bo'ladi.
3. Reja tuzing: haftada nechta soat ajratasiz, qaysi bosqichni qachongacha tugatishni belgilang.
4. Community bilan bog'laning — solo o'rganish sekinlashtiradi; Discord/Telegram CTF guruhlariga qo'shiling.

---

## 🤝 Hissa qo'shish (Contributing)

Bu loyiha jamoaviy rivojlanadi. Agar sizda foydali resurs, writeup yoki tuzatish bo'lsa — pull request oching yoki issue qoldiring. Har bir bo'lim uchun batafsil `README.md` alohida yozilishi rejalashtirilgan.

---

*"Kiberxavfsizlikda yorliq yo'q — faqat tizim va vaqt bor."*

