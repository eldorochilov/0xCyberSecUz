# 🐧 Linux Asoslari

> **00-foundations / 01-linux-basics**
> Kiberxavfsizlikning butun poydevori shu yerdan boshlanadi. Terminalni bilmasdan, hech qanday pentest, exploit yoki server xavfsizligi haqida gapirib bo'lmaydi.

---

## 🎯 Nima uchun kerak?

Har bir pentester, xavfsizlik muhandisi va low-level dasturchi Linuxda "uyidagidek" harakat qila olishi kerak. Ko'pgina server, target mashina va exploitation muhitlari — Linux asosida ishlaydi.

---

## 📚 Mavzular ro'yxati

### 1. Fayl tizimi va navigatsiya
- `/`, `/etc`, `/var`, `/home`, `/proc`, `/dev` — nima uchun kerak
- `ls`, `cd`, `pwd`, `find`, `locate`, `tree`
- Absolute vs relative path

### 2. Fayllar va ruxsatlar (permissions)
- `chmod`, `chown`, `chgrp`
- `rwx` va oktal notatsiya (`755`, `644`, `777`)
- SUID, SGID, sticky bit — xavfsizlik nuqtai nazaridan muhim

### 3. Foydalanuvchilar va guruhlar
- `/etc/passwd`, `/etc/shadow`, `/etc/group`
- `useradd`, `usermod`, `su`, `sudo`
- Root vs oddiy foydalanuvchi tushunchasi

### 4. Jarayonlar (processes)
- `ps`, `top`, `htop`, `kill`, `kill -9`
- Foreground vs background (`&`, `jobs`, `fg`, `bg`)
- systemd va `systemctl` asoslari

### 5. Matn bilan ishlash
- `cat`, `less`, `head`, `tail`, `grep`, `sed`, `awk`
- Pipe (`|`) va redirection (`>`, `>>`, `<`)
- Regular expressions asoslari

### 6. Paket boshqaruvi
- Debian/Ubuntu: `apt`
- Arch: `pacman`
- Termux: `pkg`

### 7. Tarmoq bilan bog'liq buyruqlar (kirish darajasida)
- `ping`, `curl`, `wget`, `netstat`, `ss`
- `/etc/hosts`, `/etc/resolv.conf`

---

## 🛠 Amaliyot topshiriqlari

- [ ] Termux yoki VPS'da yangi foydalanuvchi yaratib, unga `sudo` huquqi bering
- [ ] `chmod` yordamida faylni faqat egasi o'qiy oladigan qilib sozlang
- [ ] `grep` va `awk` yordamida log fayldan muayyan IP manzillarni ajratib oling
- [ ] Bironta xizmatni (masalan, `ssh`) `systemctl` orqali to'xtatib, qayta ishga tushiring

---

## 📖 Qo'shimcha manbalar

- *The Linux Command Line* — William Shotts (bepul PDF mavjud)
- [explainshell.com](https://explainshell.com) — har qanday buyruqni bo'laklab tushuntiradi
- `man` sahifalari — har doim birinchi manba bo'lsin

---

⬅️ [Orqaga: 00-foundations](../README.md) | ➡️ [Keyingi: 02-networking-basics](../02-networking-basics/README.md)

