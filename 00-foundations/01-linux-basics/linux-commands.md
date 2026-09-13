<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:2C5364,100:00FF87&height=220&section=header&text=01%20-%20Linux%20Basics&fontSize=52&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Terminaldan%20tortib%20tizim%20boshqaruvigacha&descAlignY=58&descSize=18" width="100%"/>

<p>
  <img src="https://img.shields.io/badge/Level-Beginner-brightgreen?style=for-the-badge&logo=leveldb&logoColor=white"/>
  <img src="https://img.shields.io/badge/Linux-000000?style=for-the-badge&logo=linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white"/>
  <img src="https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=android&logoColor=green"/>
</p>

<p>
  <img src="https://img.shields.io/badge/Til-O'zbek-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Vaqt-6--10%20soat-yellow?style=flat-square"/>
  <img src="https://img.shields.io/badge/Bo'lim-00--foundations-purple?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Active-success?style=flat-square"/>
</p>

</div>

## 📖 Kirish

Kiberxavfsizlik, penetratsion test, backend dasturlash yoki DevOps — qaysi yo'nalishni tanlamang, barchasining fundamenti bitta: **Linux**. Deyarli barcha serverlar, xavfsizlik vositalari (Nmap, Metasploit, Burp Suite), va hatto Android (shu jumladan sizning Termux muhitingiz) Linux yadrosiga asoslangan.

Bu qo'llanma sizni Linuxni "bilaman" darajasidan "terminalda erkin harakatlanaman" darajasiga olib chiqadi. Har bir mavzu nazariya + amaliy misollar bilan beriladi.

> 💡 **Eslatma:** Barcha misollarni Termux yoki Oracle Cloud ARM instance'ingizda bemalol takrorlashingiz mumkin — buyruqlar universal.

---

## 🗂️ Mavzular xaritasi

<table>
<tr><th>№</th><th>Mavzu</th><th>Nimani o'rganasiz</th></tr>
<tr><td>1</td><td><a href="#1-linux-nima-va-nega-muhim">Linux nima va tarixi</a></td><td>Kernel, distributivlar, ochiq kod falsafasi</td></tr>
<tr><td>2</td><td><a href="#2-fayl-tizimi-ierarxiyasi-fhs">Fayl tizimi (FHS)</a></td><td>/etc, /var, /home, /bin va boshqalar</td></tr>
<tr><td>3</td><td><a href="#3-terminal-va-navigatsiya">Terminal va navigatsiya</a></td><td>ls, cd, pwd, mkdir, cp, mv, rm</td></tr>
<tr><td>4</td><td><a href="#4-fayllarni-korish-va-tahrirlash">Fayllarni ko'rish/tahrirlash</a></td><td>cat, less, nano, vim/nvim asoslari</td></tr>
<tr><td>5</td><td><a href="#5-ruxsatlar-va-egalik-permissions">Ruxsatlar (permissions)</a></td><td>chmod, chown, octal notatsiya</td></tr>
<tr><td>6</td><td><a href="#6-foydalanuvchilar-va-guruhlar">Foydalanuvchilar va guruhlar</a></td><td>useradd, passwd, /etc/passwd, sudo</td></tr>
<tr><td>7</td><td><a href="#7-jarayonlarni-boshqarish-processes">Jarayonlar (processes)</a></td><td>ps, top, kill, jobs, systemctl</td></tr>
<tr><td>8</td><td><a href="#8-paket-menejerlari">Paket menejerlari</a></td><td>apt, dnf, pacman, pkg (Termux)</td></tr>
<tr><td>9</td><td><a href="#9-matn-bilan-ishlash-text-processing">Matn bilan ishlash</a></td><td>grep, sed, awk, find, sort, wc</td></tr>
<tr><td>10</td><td><a href="#10-pipe-redirection-va-environment">Pipe, redirection, ENV</a></td><td>|, >, >>, $PATH, export</td></tr>
<tr><td>11</td><td><a href="#11-tarmoq-buyruqlari-networking">Tarmoq buyruqlari</a></td><td>ip, ping, curl, wget, ss, netstat</td></tr>
<tr><td>12</td><td><a href="#12-bash-skriptlash-asoslari">Bash skriptlash</a></td><td>o'zgaruvchilar, sikl, shart, funksiya</td></tr>
<tr><td>13</td><td><a href="#13-loglar-va-monitoring">Loglar va monitoring</a></td><td>/var/log, journalctl, dmesg</td></tr>
<tr><td>14</td><td><a href="#14-xavfsizlik-asoslari">Xavfsizlik asoslari</a></td><td>sudo, ssh-keygen, ufw firewall</td></tr>
</table>

---

## 1. Linux nima va nega muhim

**Linux** — bu 1991-yilda Linus Torvalds tomonidan yaratilgan, ochiq manba kodli (open-source) operatsion tizim yadrosi (kernel). "Linux" atamasi ko'pincha GNU vositalari + Linux kernel birikmasi (GNU/Linux) ma'nosida ishlatiladi.

**Nega kiberxavfsizlikda Linux markaziy o'rin tutadi:**
- 🖥️ Dunyodagi serverlarning katta qismi (~96%+) Linuxda ishlaydi
- 🛡️ Deyarli barcha xavfsizlik vositalari (Kali, Parrot OS) Linux asosida
- 🔓 Ochiq kod — tizim ichida nima bo'layotganini to'liq ko'rish mumkin
- ⚙️ Avtomatlashtirish va skriptlash uchun eng kuchli muhit

**Mashhur distributivlar:**

| Distributiv | Maqsad | Paket menejeri |
|---|---|---|
| Ubuntu / Debian | Umumiy foydalanish, serverlar | `apt` |
| Kali Linux | Penetratsion testing | `apt` |
| Arch Linux | Moslashuvchan, minimalistik | `pacman` |
| Fedora / RHEL | Enterprise, korporativ | `dnf` |
| Alpine | Konteynerlar, Docker | `apk` |

---

## 2. Fayl tizimi ierarxiyasi (FHS)

Windows'dan farqli o'laroq (C:\, D:\), Linuxda **hammasi bitta ildizdan** (`/`) boshlanadi.

```
/
├── bin      → asosiy buyruqlar (ls, cp, cat)
├── boot     → yuklash fayllari (kernel, GRUB)
├── dev      → qurilmalar (device fayllar)
├── etc      → tizim konfiguratsiyalari
├── home     → foydalanuvchilar papkalari (/home/eldor)
├── lib      → kutubxonalar (libraries)
├── media    → tashqi disklar (USB va h.k.)
├── opt      → qo'shimcha dasturlar
├── proc     → jarayonlar haqida virtual ma'lumot
├── root     → root foydalanuvchi uy papkasi
├── sbin     → tizim buyruqlari (root uchun)
├── tmp      → vaqtinchalik fayllar
├── usr      → foydalanuvchi dasturlari va resurslar
└── var      → o'zgaruvchan ma'lumotlar (loglar, cache)
```

> 🎯 **Amaliyot:** `ls -la /` buyrug'ini bajarib, yuqoridagi papkalarni o'zingiz ko'ring.

---

## 3. Terminal va navigatsiya

| Buyruq | Vazifasi | Misol |
|---|---|---|
| `pwd` | Joriy papkani ko'rsatadi | `pwd` |
| `ls` | Papka tarkibini ko'rsatadi | `ls -la` |
| `cd` | Papkani almashtiradi | `cd /etc` |
| `mkdir` | Yangi papka yaratadi | `mkdir loyiha` |
| `touch` | Bo'sh fayl yaratadi | `touch main.c` |
| `cp` | Nusxa oladi | `cp a.txt b.txt` |
| `mv` | Ko'chiradi/nomlaydi | `mv a.txt papka/` |
| `rm` | O'chiradi | `rm -rf papka/` |
| `find` | Fayl qidiradi | `find / -name "*.log"` |
| `man` | Yordam sahifasi | `man ls` |

**Foydali flaglar:** `ls -la` (yashirin fayllar + batafsil), `rm -rf` (majburiy, rekursiv o'chirish — ⚠️ **ehtiyot bo'ling**, qaytarib bo'lmaydi).

---

## 4. Fayllarni ko'rish va tahrirlash

| Buyruq | Vazifasi |
|---|---|
| `cat fayl.txt` | Faylni to'liq chiqaradi |
| `less fayl.txt` | Sahifalab ko'rish (`q` — chiqish) |
| `head -n 20 fayl.txt` | Birinchi 20 qator |
| `tail -n 20 fayl.txt` | Oxirgi 20 qator |
| `tail -f fayl.log` | Real-vaqtda kuzatish (loglar uchun) |
| `nvim fayl.txt` | Neovim orqali tahrirlash |

---

## 5. Ruxsatlar va egalik (permissions)

`ls -l` buyrug'ida quyidagini ko'rasiz:

```
-rwxr-xr-- 1 eldor eldor 4096 Sep 13 main.sh
```

**Tuzilishi:** `[tur][egasi][guruh][boshqalar]`

| Belgi | Ma'nosi | Raqam |
|---|---|---|
| `r` | read (o'qish) | 4 |
| `w` | write (yozish) | 2 |
| `x` | execute (bajarish) | 1 |

**Octal (raqamli) notatsiya:**

| Ruxsat | Raqam |
|---|---|
| `rwx` | 7 |
| `rw-` | 6 |
| `r-x` | 5 |
| `r--` | 4 |

```bash
chmod 755 script.sh     # egasi: rwx, guruh/boshqa: r-x
chmod +x script.sh      # faqat bajarish huquqini qo'shadi
chown eldor:eldor fayl  # egasi va guruhini o'zgartiradi
```

---

## 6. Foydalanuvchilar va guruhlar

```bash
whoami                  # joriy foydalanuvchi
id                      # UID, GID va guruhlar
sudo useradd -m yangi   # yangi foydalanuvchi (uy papkasi bilan)
sudo passwd yangi       # parol o'rnatish
sudo usermod -aG sudo yangi   # sudo guruhiga qo'shish
cat /etc/passwd         # barcha foydalanuvchilar ro'yxati
```

`sudo` — vaqtincha root (administrator) huquqi bilan buyruq bajarish. Xavfsizlik nuqtai nazaridan, doim oddiy foydalanuvchi bilan ishlab, faqat kerak bo'lganda `sudo` ishlatish tavsiya etiladi.

---

## 7. Jarayonlarni boshqarish (processes)

| Buyruq | Vazifasi |
|---|---|
| `ps aux` | Barcha jarayonlar ro'yxati |
| `top` / `htop` | Real-vaqtda resurs monitoring |
| `kill PID` | Jarayonni to'xtatish |
| `kill -9 PID` | Majburiy o'ldirish |
| `jobs` | Fon (background) jarayonlar |
| `bg` / `fg` | Fonga/oldinga o'tkazish |
| `command &` | Jarayonni fonda ishga tushirish |
| `systemctl status ssh` | Xizmat (service) holatini ko'rish |
| `systemctl start/stop/restart ssh` | Xizmatni boshqarish |

---

## 8. Paket menejerlari

| Distributiv | O'rnatish | Yangilash | O'chirish |
|---|---|---|---|
| Debian/Ubuntu | `apt install paket` | `apt update && apt upgrade` | `apt remove paket` |
| Fedora/RHEL | `dnf install paket` | `dnf update` | `dnf remove paket` |
| Arch | `pacman -S paket` | `pacman -Syu` | `pacman -R paket` |
| **Termux** | `pkg install paket` | `pkg update && pkg upgrade` | `pkg uninstall paket` |

---

## 9. Matn bilan ishlash (text processing)

Bu bo'lim keyingi loglarni tahlil qilish va xavfsizlik ishlarida juda muhim.

```bash
grep "error" fayl.log          # "error" so'zi bor qatorlarni topadi
grep -r "TODO" .               # rekursiv qidiruv
grep -i "ERROR" fayl.log       # katta-kichik harfga sezgirsiz

sed 's/eski/yangi/g' fayl.txt  # matn almashtirish

awk '{print $1}' fayl.txt      # birinchi ustunni chiqaradi

sort fayl.txt | uniq -c        # saralash + takrorlarni sanash

wc -l fayl.txt                 # qatorlar sonini hisoblaydi

find / -name "*.conf" 2>/dev/null   # konfiguratsiya fayllarni qidirish
```

---

## 10. Pipe, redirection va environment

```bash
ls -la | grep ".sh"        # pipe (|) — bir buyruq chiqishini boshqasiga uzatadi
echo "log" > fayl.txt      # > — qayta yozadi
echo "yana log" >> fayl.txt # >> — qo'shib yozadi
command 2> xato.log        # xatolarni faylga yo'naltirish

echo $PATH                 # buyruqlar qidiriladigan papkalar
export PATH=$PATH:/yangi/yol   # PATH ga yangi yo'l qo'shish
env                        # barcha environment o'zgaruvchilar
```

---

## 11. Tarmoq buyruqlari (networking)

| Buyruq | Vazifasi |
|---|---|
| `ip a` | Tarmoq interfeyslari va IP manzillar |
| `ping google.com` | Ulanishni tekshirish |
| `curl -I https://site.com` | HTTP headerlarni ko'rish |
| `wget https://file.zip` | Faylni yuklab olish |
| `ss -tulpn` | Ochiq portlar ro'yxati |
| `whois domen.com` | Domen haqida ma'lumot |
| `traceroute site.com` | Paket yo'lini kuzatish |

---

## 12. Bash skriptlash asoslari

```bash
#!/bin/bash
# Oddiy Bash skript namunasi

ism="Eldor"
echo "Salom, $ism!"

if [ -f "main.c" ]; then
    echo "Fayl mavjud"
else
    echo "Fayl topilmadi"
fi

for i in 1 2 3; do
    echo "Raqam: $i"
done

salomlash() {
    echo "Funksiya ishladi: $1"
}
salomlash "test"
```

Ishga tushirish: `chmod +x skript.sh && ./skript.sh`

---

## 13. Loglar va monitoring

```bash
journalctl -xe             # tizim loglari (systemd)
journalctl -u ssh -f       # ma'lum xizmat logini real-vaqtda
dmesg | less                # kernel xabarlari
cat /var/log/auth.log       # autentifikatsiya loglari (Debian/Ubuntu)
```

---

## 14. Xavfsizlik asoslari

```bash
ssh-keygen -t ed25519           # SSH kalit juftligi yaratish
ssh-copy-id user@server         # ochiq kalitni serverga yuborish
ssh user@server -p 22           # SSH orqali ulanish

sudo ufw enable                 # firewall yoqish
sudo ufw allow 22/tcp           # ma'lum portga ruxsat
sudo ufw status                 # holatni ko'rish

sudo apt update && sudo apt upgrade -y   # tizimni yangilab turish — xavfsizlikning asosi
```

> ⚠️ Parolga asoslangan SSH kirishni o'chirib, faqat kalit (key-based) autentifikatsiyani yoqish — real serverlarda birinchi qoidalardan biri.

---

## ✅ Amaliy topshiriqlar (checklist)

- [ ] Terminalda 15 daqiqa faqat `cd`, `ls`, `pwd` bilan tizim bo'ylab sayohat qiling
- [ ] O'z uy papkangizda 3 ta papka va 5 ta fayl yarating, so'ng `find` bilan qidiring
- [ ] Bitta faylga `chmod 700`, boshqasiga `chmod 644` qo'yib, farqini tushuntiring
- [ ] Yangi foydalanuvchi yarating va unga sudo huquqi bering (VM/konteynerda sinang)
- [ ] `ps aux | grep bash` buyrug'ini bajarib natijani tahlil qiling
- [ ] `/var/log` papkasidagi kamida 2 ta log faylini `tail -f` bilan kuzating
- [ ] 10 qatorlik oddiy Bash skript yozing (fayllarni avtomatik arxivlaydigan)
- [ ] `grep`, `awk`, `sed` yordamida biror log faylidan kerakli ma'lumotni ajratib oling
- [ ] `ip a` va `ss -tulpn` orqali o'z tizimingizdagi ochiq portlarni aniqlang
- [ ] SSH kalit juftligi yaratib, uni qanday ishlashini tushuntiring

---

## 📚 Qo'shimcha resurslar

| Manba | Tavsif | Havola |
|---|---|---|
| Linux Journey | Interaktiv, bepul Linux darsligi | linuxjourney.com |
| The Linux Command Line (kitob) | Chuqur, klassik qo'llanma | William Shotts |
| OverTheWire: Bandit | Amaliy Linux/xavfsizlik wargame | overthewire.org |
| ExplainShell | Har qanday buyruqni bo'laklab tushuntiradi | explainshell.com |
| TLDR Pages | Qisqa, amaliy man sahifalari | tldr.sh |

---

<div align="center">

⬅️ **Oldingi:** [00-foundations](../00-foundations) &nbsp;&nbsp;|&nbsp;&nbsp; **Keyingi:** [02-networking-basics](../02-networking-basics/networking.md) ➡️

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00FF87,50:2C5364,100:0F2027&height=120&section=footer" width="100%"/>

</div>

