<div align="center">

# 🟡 02 — Web Security

![Daraja](https://img.shields.io/badge/Daraja-Intermediate-EAB308?style=for-the-badge)
![Muddat](https://img.shields.io/badge/Muddat-4--6_oy-EAB308?style=for-the-badge)

*Web ilovalar xavfsizligiga chuqur kirish*

</div>

> Web xavfsizlik — kiberxavfsizlikning eng "kirish oson" yo'nalishi, lekin chuqurligi cheksiz. Bu bo'limda siz zamonaviy web ilovalarga qarshi hujum vektorlarini, ularning sabablarini va himoya usullarini o'rganasiz.

⚠️ **Oldingi shart:** HTTP/HTTPS ishlash mexanizmini ([`00-foundations`](../00-foundations/README.md)) va asosiy dasturlash tushunchalarini bilishingiz kerak.

---

## 1️⃣ 🔟 OWASP Top 10 — zamin sifatida

OWASP Top 10 — eng keng tarqalgan va xavfli web zaifliklar ro'yxati. Har birini nafaqat "qanday ekspluatatsiya qilish" balki **nega paydo bo'lishi** nuqtai nazaridan o'rganing:

<details open>
<summary><b>💉 Injection (SQL Injection va boshqalar)</b></summary>
<br>

- SQL so'rovlari foydalanuvchi kiritmasi bilan noto'g'ri birlashtirilganda yuzaga keladi
- Klassik hujum: `' OR '1'='1` — autentifikatsiyani chetlab o'tish
- UNION-based, Boolean-based va Time-based blind SQLi farqlari

✅ **Himoya:** parametrlangan so'rovlar (prepared statements), input validatsiya

</details>

<details open>
<summary><b>🧬 Cross-Site Scripting (XSS)</b></summary>
<br>

- Stored, Reflected va DOM-based XSS farqlari
- Nega brauzer foydalanuvchi kiritgan skriptni "ishonchli" deb bajaradi

✅ **Himoya:** output encoding, Content Security Policy (CSP)

</details>

<details open>
<summary><b>🎭 Cross-Site Request Forgery (CSRF)</b></summary>
<br>

- Foydalanuvchi bilmagan holda uning nomidan so'rov yuborilishi
- CSRF token'lar qanday himoya qiladi

</details>

<details open>
<summary><b>🔄 Server-Side Request Forgery (SSRF)</b></summary>
<br>

- Server orqali ichki tarmoq resurslariga (masalan, cloud metadata endpoint `169.254.169.254`) so'rov yuborish
- Zamonaviy cloud muhitlarida juda xavfli hujum turi

</details>

<details open>
<summary><b>🔓 Broken Authentication / Access Control</b></summary>
<br>

- Session boshqaruvidagi xatolar, JWT noto'g'ri validatsiyasi
- **IDOR** (Insecure Direct Object Reference) — foydalanuvchi ID'ni o'zgartirib, boshqalarning ma'lumotiga kirish

</details>

<details>
<summary><b>➕ Qolgan muhim toifalar</b></summary>
<br>

- Security Misconfiguration
- Sensitive Data Exposure
- XXE (XML External Entity)
- Insecure Deserialization

</details>

---

## 2️⃣ 🔧 Amaliy vositalar

| Tool | Vazifasi |
|---|---|
| 🦊 **Burp Suite** | Proxy sifatida brauzer/server trafigini ushlab turish, Repeater orqali qo'lda o'zgartirish, Intruder orqali fuzzing |
| 🛠️ **Brauzer DevTools** | Network tab orqali so'rov/javoblarni tahlil qilish, Console orqali JS injection sinash |
| 🐍 `sqlmap` | SQL injection'ni avtomatlashtirish *(avval qo'lda tushunib, keyin ishlating!)* |
| 🔍 `ffuf` / `gobuster` | Yashirin endpoint/fayl fuzzing |

---

## 3️⃣ 🧪 Laboratoriyalar

| Platforma | Nega tavsiya etiladi |
|---|---|
| 🏆 **PortSwigger Web Security Academy** | Bepul, eng chuqur va tizimli — har bir zaiflik nazariy tushuntirish + interaktiv lab bilan keladi |
| 🎯 **DVWA** | Lokal o'rnatib, xavfsiz muhitda mashq qilish uchun |
| 🟩 **TryHackMe** (Web fundamentals) | Boshlang'ichlar uchun yo'naltirilgan, video bilan |
| 📦 **HackTheBox** (Web challenges) | Murakkabroq, real dunyoga yaqin senariylar |

> ⭐ **Tavsiya:** PortSwigger Academy'ni tizimli ravishda, har bir mavzuni tartib bilan o'tib chiqing — bu bepul resurslar orasida eng sifatlisi hisoblanadi.

---

## 4️⃣ 🎯 Amaliy loyiha

> **Vazifa:** Ataylab zaif qilib yozilgan oddiy web ilova (masalan, login formasi + qidiruv funksiyasi) yarating (PHP+MySQL yoki Node.js+SQLite), so'ngra:

1. [ ] Unga SQL injection orqali kirib ko'ring
2. [ ] XSS zaifligini joylashtirib, uni ekspluatatsiya qiling
3. [ ] Har ikkala zaiflikni **to'g'irlang** (parametrlangan so'rov, output encoding)

> 💡 Bu — "hujum qiluvchi tafakkur" va "himoyachi tafakkur"ni bir vaqtda rivojlantiradi.

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak

- [ ] OWASP Top 10'dagi har bir zaiflikni misol bilan tushuntira olasiz
- [ ] Burp Suite'da Proxy va Repeater'dan foydalana olasiz
- [ ] SQL injection'ni qo'lda (sqlmap'siz) topib, ekspluatatsiya qila olasiz
- [ ] Stored va Reflected XSS orasidagi farqni amaliyotda ko'rsata olasiz
- [ ] O'z zaif ilovangizni yozib, uni sindirib, keyin tuzatgan bo'lasiz

---

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| PortSwigger Web Security Academy | Eng to'liq bepul web xavfsizlik kursi |
| OWASP Top 10 rasmiy hujjati | Har yilgi eng dolzarb zaifliklar tahlili |
| *The Web Application Hacker's Handbook* | Chuqur va klassik kitob |
| DVWA / bWAPP | Lokal mashq qilish uchun zaif ilovalar |

---

<div align="center">

**◀** [🟢 01-beginner](../01-beginner/README.md) &nbsp;|&nbsp; **Keyingi qadam →** [🟡 03-network-pentest](../03-network-pentest/README.md)

</div>

