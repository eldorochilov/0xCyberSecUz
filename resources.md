<div align="center">

# 📚 Resources — Kitoblar, Kurslar va Havolalar

![Yangilanadi](https://img.shields.io/badge/Holat-Doimiy_yangilanadi-8B5CF6?style=for-the-badge)

*Barcha bosqichlar uchun bitta joyga jamlangan resurslar ro'yxati*

</div>

> 💡 Bu fayl har bir bo'limdagi resurslarni bitta joyda jamlaydi — tezkor qidiruv uchun. Batafsil kontekst uchun tegishli bo'lim README'siga qarang.

---

## 📖 Kitoblar

<details open>
<summary><b>🔵 Foundations / Umumiy</b></summary>
<br>

| Kitob | Muallif | Nega o'qish kerak |
|---|---|---|
| *The C Programming Language* | Kernighan & Ritchie (K&R) | C tilining klassik, qisqa va aniq darsligi |
| *The Linux Programming Interface* | Michael Kerrisk | Linux tizim dasturlash bo'yicha eng to'liq manba |
| *Expert C Programming* | Peter van der Linden | C tilining "yashirin qoidalari" va tuzoqlari |
| *Computer Systems: A Programmer's Perspective (CS:APP)* | Bryant & O'Hallaron | Xotira, kompilyatsiya, tizim darajasidagi tushunish uchun |

</details>

<details open>
<summary><b>🟠 Advanced / Low-level</b></summary>
<br>

| Kitob | Muallif | Nega o'qish kerak |
|---|---|---|
| *Hacking: The Art of Exploitation* | Jon Erickson | Binary exploitation'ga eng klassik va tushunarli kirish |
| *The Web Application Hacker's Handbook* | Stuttard & Pinto | Web xavfsizlik bo'yicha chuqur va klassik kitob |
| *Practical Malware Analysis* | Sikorski & Honig | Reverse engineering va malware tahlili bo'yicha standart kitob |
| *The Hacker Playbook 3* | Peter Kim | Amaliy pentest metodologiyasi va senariylari |
| *Linux Device Drivers (LDD3)* | Corbet, Rubini, Kroah-Hartman | Kernel/driver darajasidagi dasturlash uchun |

</details>

---

## 🎓 Kurslar va Platformalar

<details open>
<summary><b>🏁 CTF va Wargame platformalari</b></summary>
<br>

| Platforma | Yo'nalish | Daraja |
|---|---|:---:|
| [OverTheWire](https://overthewire.org/wargames/) | Linux, kripto, binary exploitation (Bandit/Narnia/Krypton) | 🔵🟢 |
| [picoCTF](https://picoctf.org/) | Umumiy kirish darajasi, ko'p yo'nalishli, video bilan | 🟢 |
| [TryHackMe](https://tryhackme.com/) | Yo'naltirilgan yo'llar, boshlang'ichdan o'rtaga | 🟢🟡 |
| [HackTheBox](https://www.hackthebox.com/) | Real-world uslubidagi mashinalar, o'rta-yuqori daraja | 🟡🟠 |
| [pwn.college](https://pwn.college/) | Chuqur, video-ma'ruzali binary exploitation kursi (ASU) | 🟠 |
| [pwnable.kr](http://pwnable.kr/) | Klassik va mashhur pwn mashqlari | 🟠 |
| [crackmes.one](https://crackmes.one/) | Reverse engineering mashqlari to'plami | 🟠 |
| [Vulnhub](https://www.vulnhub.com/) | Yuklab olinadigan zaif VM'lar, offline mashq | 🟡🟠 |

</details>

<details open>
<summary><b>🌐 Web xavfsizlik</b></summary>
<br>

| Resurs | Izoh |
|---|---|
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | Bepul, eng chuqur va tizimli web xavfsizlik kursi |
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | Har yilgi eng dolzarb zaifliklar tahlili (rasmiy hujjat) |
| DVWA / bWAPP | Lokal o'rnatib mashq qilish uchun ataylab zaif ilovalar |

</details>

<details open>
<summary><b>💥 Binary Exploitation / ARM64</b></summary>
<br>

| Resurs | Izoh |
|---|---|
| [Azeria Labs](https://azeria-labs.com/) | ARM/ARM64 assembly va exploitation bo'yicha eng yaxshi bepul resurs |
| ARM Architecture Reference Manual (ARMv8) | Rasmiy, to'liq texnik hujjat |
| [ROP Emporium](https://ropemporium.com/) | ROP texnikasini bosqichma-bosqich o'rgatuvchi mashqlar |
| GEF (GDB Enhanced Features) | GDB'ni vizual va qulay qiluvchi plugin |

</details>

<details open>
<summary><b>🔎 Reverse Engineering</b></summary>
<br>

| Resurs | Izoh |
|---|---|
| Ghidra rasmiy hujjatlari | Eng keng qo'llaniladigan bepul decompiler |
| radare2 Book | r2 bo'yicha rasmiy, chuqur qo'llanma |

</details>

<details open>
<summary><b>📡 Tarmoq va Pentest</b></summary>
<br>

| Resurs | Izoh |
|---|---|
| [HackTricks](https://book.hacktricks.xyz/) | Deyarli har qanday texnika bo'yicha eng to'liq bepul spravochnik |
| [GTFOBins](https://gtfobins.github.io/) | SUID/sudo orqali privesc uchun binary'lar bazasi |
| Ippsec YouTube kanali | HTB mashinalari yechimi bo'yicha video tahlillar |
| Professor Messer (Network+) | Tarmoq asoslarini vizual tushuntiruvchi bepul video kurs |
| Beej's Guide to Network Programming | Socket dasturlash bo'yicha bepul va tushunarli qo'llanma |

</details>

<details open>
<summary><b>🔑 Kriptografiya</b></summary>
<br>

| Resurs | Izoh |
|---|---|
| Cryptopals Challenges | Kriptografiyani amaliy o'rganish uchun mashhur to'plam |

</details>

---

## 🛠️ Asosiy vositalar (cheat-sheet ko'rinishida)

| Kategoriya | Vositalar |
|---|---|
| 🐧 Tizim tahlili | `ps`, `top`, `systemctl`, `journalctl`, `find`, `sudo -l` |
| 🌐 Tarmoq | `nmap`, `tcpdump`, `netcat`, `ss`, `ip`, Wireshark |
| 🌍 Web | Burp Suite, `sqlmap`, `ffuf`, `gobuster` |
| 💥 Binary/Pwn | `gdb` + GEF, `checksec`, `readelf`, `objdump`, `pwntools`, `ROPgadget` |
| 🔍 Reversing | Ghidra, radare2/rizin, `strings`, `strace`/`ltrace` |
| 🏢 Active Directory | `enum4linux`, `smbclient`, Responder, `LinPEAS`/`WinPEAS` |

---

## 🎥 YouTube kanallar

| Kanal | Yo'nalish |
|---|---|
| Ippsec | HTB writeup va metodologiya |
| LiveOverflow | Binary exploitation, CTF, xavfsizlik tadqiqoti |
| John Hammond | CTF yechimlari, keng qamrovli xavfsizlik kontenti |
| Azeria Labs (blog + video) | ARM/ARM64 exploitation |

---

## 🌍 Community

> Solo o'rganish sekinlashtiradi — quyidagilarga qo'shilishni unutmang:

- CTF-ga yo'naltirilgan Discord/Telegram guruhlari
- [CTFtime.org](https://ctftime.org/) — yaqinlashib kelayotgan musobaqalar va jamoalar reytingi
- Mahalliy (O'zbekiston) kiberxavfsizlik hamjamiyatlari va Telegram kanallari

---

<div align="center">

📌 Yangi foydali resurs topsangiz — PR oching va shu faylga qo'shing!

**◀** [🏠 Bosh sahifa](README.md)

</div>

