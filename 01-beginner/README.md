<div align="center">

# 🟢 01 — Beginner

![Daraja](https://img.shields.io/badge/Daraja-Beginner-22C55E?style=for-the-badge)
![Muddat](https://img.shields.io/badge/Muddat-2--3_oy-22C55E?style=for-the-badge)

*Xavfsizlik asoslari va birinchi CTF'laringiz*

</div>

> ⚠️ **Oldingi shart:** [`00-foundations`](../00-foundations/README.md) bosqichini tugatgan bo'lishingiz kerak — Linux, tarmoq va C/Python asoslari bu yerda hal qiluvchi ahamiyatga ega.

---

## 1️⃣ 🧠 Xavfsizlik falsafasi va asosiy tushunchalar

<details open>
<summary><b>🔺 CIA Triadasi</b></summary>
<br>

| Element | Ma'nosi |
|---|---|
| **C**onfidentiality (Maxfiylik) | Ma'lumotga faqat ruxsat etilganlar kira olishi |
| **I**ntegrity (Yaxlitlik) | Ma'lumot ruxsatsiz o'zgartirilmasligi |
| **A**vailability (Mavjudlik) | Tizim kerak bo'lganda ishlashi (DoS hujumlari shu printsipni buzadi) |

> 💡 Har bir zaiflik yoki hujumni tahlil qilganda, "bu qaysi triada elementini buzyapti?" deb so'rang — bu tafakkuringizni tartibga soladi.

</details>

<details open>
<summary><b>🎯 Threat Modeling (Tahdid modellashtirish)</b></summary>
<br>

- Kim hujum qilishi mumkin? (script kiddie, insayder, davlat darajasidagi aktyor)
- Nima himoyalanadi? (ma'lumot, xizmat, obro')
- Qanday vektorlar orqali hujum bo'lishi mumkin?

</details>

<details open>
<summary><b>🏷️ Muhim atamalar</b></summary>
<br>

| Atama | Ma'nosi |
|---|---|
| **CVE** | Common Vulnerabilities and Exposures — ma'lum zaifliklar katalogi |
| **CVSS** | Zaiflikning jiddiylik darajasini baholash tizimi (0–10) |
| **Zero-day** | Hali hech kimga (ishlab chiqaruvchiga ham) ma'lum bo'lmagan zaiflik |
| **Exploit** | Zaiflikdan foydalanish uchun yozilgan kod/usul |
| **Payload** | Exploit orqali yetkaziladigan zararli/maqsadli kod |

</details>

---

## 2️⃣ 🔑 Kriptografiya asoslari

<details open>
<summary><b>🔄 Simmetrik vs Asimmetrik shifrlash</b></summary>
<br>

- **Simmetrik (AES):** bir kalit — tez, lekin kalit almashish muammosi
- **Asimmetrik (RSA):** ochiq/yopiq kalit juftligi — sekinroq, lekin xavfsiz kalit almashinuvini ta'minlaydi
- **Hibrid tizimlar** (masalan, TLS) ikkalasini birlashtiradi

</details>

<details open>
<summary><b>#️⃣ Hashing</b></summary>
<br>

- Hash funksiya nima (MD5, SHA-256) — bir tomonlama funksiya, kalitlarni saqlash uchun ishlatiladi
- Hash collision nima va nega MD5/SHA-1 endi ishonchsiz hisoblanadi
- Salt tushunchasi — parol xeshlashda nega muhim

</details>

<details open>
<summary><b>📜 Klassik shifrlar va ularga hujumlar</b></summary>
<br>

- **Caesar shifri:** oddiy siljish shifri, known-plaintext hujumi bilan osongina yechiladi
- **Vigenère shifri:** kalit uzunligini aniqlash (Kasiski tekshiruvi), so'ngra chastota tahlili

> 🎯 **Amaliyot:** Bash yoki Python skripti yozib, matndagi harflar chastotasini hisoblang va monoalfavitik shifrni frequency analysis orqali yeching

Bu klassik shifrlar zamonaviy tizimlarda ishlatilmaydi, lekin ular orqali **kriptotahliliy fikrlash** shakllanadi — bu ko'nikma keyinchalik CTF'larning kripto bo'limlarida asqotadi.

</details>

---

## 3️⃣ 🏁 Birinchi CTF tajribangiz

### ❓ CTF nima?

CTF (Capture The Flag) — maxsus tuzilgan masalalar bo'lib, ularni yechish natijasida "flag" (masalan, `flag{...}` formatidagi matn) topiladi.

| Kategoriya | Qisqacha |
|:---:|---|
| 🌐 Web | Web ilova zaifliklari |
| 🔑 Crypto | Kriptografik hujumlar |
| 💥 Pwn | Binary exploitation |
| 🔍 Reverse | Teskari muhandislik |
| 🕵️ Forensics | Raqamli tergov |
| 🎲 Misc | Aralash masalalar |

### 🚀 Qayerdan boshlash

| # | Platforma | Nima uchun |
|:---:|---|---|
| 1 | **OverTheWire — Bandit** | SSH orqali ulanib, har bir levelda keyingi levelga parolni topasiz. Linux CLI ko'nikmalarini mustahkamlaydi |
| 2 | **OverTheWire — Narnia** | Bandit'dan keyin, oddiy binary exploitation asoslariga kirish |
| 3 | **OverTheWire — Krypton** | Klassik kriptografik hujumlar amaliyoti |
| 4 | **picoCTF** | Boshlang'ichlar uchun juda yaxshi tuzilgan, video darslar bilan birga keladi |

### 🧩 CTF yechish metodologiyasi

1. Masalani diqqat bilan o'qing — ko'pincha yechim tavsifda yashiringan bo'ladi
2. Berilgan fayl/xizmatni tekshiring (`file`, `strings`, `nc host port`)
3. Gipoteza tuzing va uni kichik qadamlar bilan sinab ko'ring
4. Yechganingizdan keyin — **writeup yozing**. Bu bilimni mustahkamlaydi va portfolio yaratadi

---

## 4️⃣ 🎯 Amaliy loyiha: oddiy port scanner

> **Vazifa:** Python yoki C'da oddiy TCP port scanner yozing.

**Talablar:**
- [ ] Berilgan IP manzil uchun 1–1024 portlar oralig'ini tekshirish
- [ ] Ochiq portlarni ro'yxatga chiqarish
- [ ] *(Qo'shimcha ball)* Thread/async yordamida tezlashtirish
- [ ] *(Qo'shimcha ball)* Ma'lum portlar uchun xizmat nomini taxmin qilish (banner grabbing)

> 💡 Bu loyiha orqali siz `nmap` ichida nima sodir bo'lishini "qo'lda" his qilasiz — bu tushunish tool'ni shunchaki ishlatishdan ancha qimmatli.

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak

- [ ] CIA triadasi va asosiy xavfsizlik terminologiyasini tushuntira olasiz
- [ ] Simmetrik/asimmetrik shifrlash va hashing farqini bilasiz
- [ ] Kamida bitta klassik shifrni frequency analysis orqali yechgan bo'lasiz
- [ ] OverTheWire Bandit'ni to'liq (yoki katta qismini) tugatgan bo'lasiz
- [ ] O'zingizning port scanner'ingizni yozib, ishga tushirgan bo'lasiz

---

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| OverTheWire (Bandit, Narnia, Krypton) | Amaliy, bosqichma-bosqich CTF wargame'lar |
| picoCTF | Video bilan birga keluvchi boshlang'ich CTF platformasi |
| Cryptopals Challenges | Kriptografiyani amaliy o'rganish uchun mashhur to'plam |
| CTFtime.org | Yaqinlashib kelayotgan CTF musobaqalari ro'yxati |

---

<div align="center">

**◀** [🔵 00-foundations](../00-foundations/README.md) &nbsp;|&nbsp; **Keyingi qadam →** [🟡 02-web-security](../02-web-security/README.md)

</div>

