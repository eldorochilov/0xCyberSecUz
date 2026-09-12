# 01 — Beginner (Xavfsizlik asoslari va birinchi CTF'lar)

> Bu bosqichda siz "kiberxavfsizlik" tushunchasi ortidagi asosiy g'oyalar va terminologiya bilan tanishasiz, so'ngra o'zingizning birinchi CTF (Capture The Flag) masalalaringizni yechasiz.

## Oldingi shart
`00-foundations` bosqichini tugatgan bo'lishingiz kerak — Linux, tarmoq va C/Python asoslari bu yerda hal qiluvchi ahamiyatga ega.

---

## 1. Xavfsizlik falsafasi va asosiy tushunchalar

### 1.1 CIA Triadasi
- **Confidentiality (Maxfiylik):** ma'lumotga faqat ruxsat etilganlar kira olishi
- **Integrity (Yaxlitlik):** ma'lumot ruxsatsiz o'zgartirilmasligi
- **Availability (Mavjudlik):** tizim kerak bo'lganda ishlashi (DoS hujumlari shu printsipni buzadi)

Har bir zaiflik yoki hujumni tahlil qilganda, "bu qaysi triada elementini buzyapti?" deb so'rang — bu tafakkuringizni tartibga soladi.

### 1.2 Threat Modeling (Tahdid modellashtirish)
- Kim hujum qilishi mumkin? (script kiddie, insayder, davlat darajasidagi aktyor)
- Nima himoyalanadi? (ma'lumot, xizmat, obro')
- Qanday vektorlar orqali hujum bo'lishi mumkin?

### 1.3 Muhim atamalar
| Atama | Ma'nosi |
|---|---|
| CVE | Common Vulnerabilities and Exposures — ma'lum zaifliklar katalogi |
| CVSS | Zaiflikning jiddiylik darajasini baholash tizimi (0–10) |
| Zero-day | Hali hech kimga (ishlab chiqaruvchiga ham) ma'lum bo'lmagan zaiflik |
| Exploit | Zaiflikdan foydalanish uchun yozilgan kod/usul |
| Payload | Exploit orqali yetkaziladigan zararli/maqsadli kod |

---

## 2. Kriptografiya asoslari

### 2.1 Simmetrik vs Asimmetrik shifrlash
- Simmetrik (AES): bir kalit — tez, lekin kalit almashish muammosi
- Asimmetrik (RSA): ochiq/yopiq kalit juftligi — sekinroq, lekin xavfsiz kalit almashinuvini ta'minlaydi
- Hibrid tizimlar (masalan, TLS) ikkalasini birlashtiradi

### 2.2 Hashing
- Hash funksiya nima (MD5, SHA-256) — bir tomonlama funksiya, kalitlarni saqlash uchun ishlatiladi
- Hash collision nima va nega MD5/SHA-1 endi ishonchsiz hisoblanadi
- Salt tushunchasi — parol xeshlashda nega muhim

### 2.3 Klassik shifrlar va ularga hujumlar (amaliy kirish)
- **Caesar shifri:** oddiy siljish shifri, known-plaintext hujumi bilan osongina yechiladi
- **Vigenère shifri:** kalit uzunligini aniqlash (Kasiski tekshiruvi), so'ngra chastota tahlili
- **Amaliyot:** Bash yoki Python skripti yozib, matndagi harflar chastotasini hisoblang va monoalfavitik shifrni frequency analysis orqali yeching

Bu klassik shifrlar zamonaviy tizimlarda ishlatilmaydi, lekin ular orqali **kriptotahliliy fikrlash** (cryptanalytic thinking) shakllanadi — bu ko'nikma keyinchalik CTF'larning kripto bo'limlarida asqotadi.

---

## 3. Birinchi CTF tajribangiz

### 3.1 CTF nima?
CTF (Capture The Flag) — maxsus tuzilgan masalalar bo'lib, ularni yechish natijasida "flag" (masalan, `flag{...}` formatidagi matn) topiladi. Kategoriyalar odatda: Web, Crypto, Pwn (binary exploitation), Reverse Engineering, Forensics, Misc.

### 3.2 Qayerdan boshlash
1. **OverTheWire — Bandit:** SSH orqali ulanib, har bir levelda keyingi levelga parolni topasiz. Bu Linux CLI ko'nikmalarini mustahkamlaydi.
2. **OverTheWire — Narnia:** Bandit'dan keyin, oddiy binary exploitation asoslariga kirish (buffer overflow'ning eng sodda ko'rinishlari).
3. **OverTheWire — Krypton:** Klassik kriptografik hujumlar amaliyoti.
4. **picoCTF:** Boshlang'ichlar uchun juda yaxshi tuzilgan, ko'p yo'nalishli masalalar to'plami — video darslar bilan birga keladi.

### 3.3 CTF yechish metodologiyasi
1. Masalani diqqat bilan o'qing — ko'pincha yechim tavsifda yashiringan bo'ladi
2. Berilgan fayl/xizmatni tekshiring (`file`, `strings`, `nc host port`)
3. Gipoteza tuzing va uni kichik qadamlar bilan sinab ko'ring
4. Yechganingizdan keyin — **writeup yozing**. Bu bilimni mustahkamlaydi va portfolio yaratadi

---

## 4. Amaliy loyiha: oddiy port scanner

Bu bosqichni tugatish uchun quyidagi mini-loyihani bajaring:

**Vazifa:** Python yoki C'da oddiy TCP port scanner yozing.

**Talablar:**
- Berilgan IP manzil uchun 1–1024 portlar oralig'ini tekshirish
- Ochiq portlarni ro'yxatga chiqarish
- (Qo'shimcha ball) Thread/async yordamida tezlashtirish
- (Qo'shimcha ball) Ma'lum portlar uchun xizmat nomini taxmin qilish (banner grabbing)

Bu loyiha orqali siz `nmap` ichida nima sodir bo'lishini "qo'lda" his qilasiz — bu tushunish tool'ni shunchaki ishlatishdan ancha qimmatli.

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak:

- [ ] CIA triadasi va asosiy xavfsizlik terminologiyasini tushuntira olasiz
- [ ] Simmetrik/asimmetrik shifrlash va hashing farqini bilasiz
- [ ] Kamida bitta klassik shifrni frequency analysis orqali yechgan bo'lasiz
- [ ] OverTheWire Bandit'ni to'liq (yoki katta qismini) tugatgan bo'lasiz
- [ ] O'zingizning port scanner'ingizni yozib, ishga tushirgan bo'lasiz

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| OverTheWire (Bandit, Narnia, Krypton) | Amaliy, bosqichma-bosqich CTF wargame'lar |
| picoCTF | Video bilan birga keluvchi boshlang'ich CTF platformasi |
| Cryptopals Challenges | Kriptografiyani amaliy o'rganish uchun mashhur to'plam |
| *CTFtime.org* | Yaqinlashib kelayotgan CTF musobaqalari ro'yxati |

**Keyingi qadam:** [`02-web-security/`](../02-web-security/README.md) — web ilovalar xavfsizligiga chuqur kirish.

