# 02 — Web Security (Web ilovalar xavfsizligi)

> Web xavfsizlik — kiberxavfsizlikning eng "kirish oson" yo'nalishi, lekin chuqurligi cheksiz. Bu bo'limda siz zamonaviy web ilovalarga qarshi hujum vektorlarini, ularning sabablarini va himoya usullarini o'rganasiz.

## Oldingi shart
HTTP/HTTPS ishlash mexanizmini (`00-foundations`) va asosiy dasturlash tushunchalarini bilishingiz kerak.

---

## 1. OWASP Top 10 — zamin sifatida

OWASP Top 10 — eng keng tarqalgan va xavfli web zaifliklar ro'yxati. Har birini nafaqat "qanday ekspluatatsiya qilish" balki **nega paydo bo'lishi** nuqtai nazaridan o'rganing:

### 1.1 Injection (SQL Injection va boshqalar)
- SQL so'rovlari foydalanuvchi kiritmasi bilan noto'g'ri birlashtirilganda yuzaga keladi
- Klassik hujum: `' OR '1'='1` — autentifikatsiyani chetlab o'tish
- UNION-based, Boolean-based va Time-based blind SQLi farqlari
- **Himoya:** parametrlangan so'rovlar (prepared statements), input validatsiya

### 1.2 Cross-Site Scripting (XSS)
- Stored, Reflected va DOM-based XSS farqlari
- Nega brauzer foydalanuvchi kiritgan skriptni "ishonchli" deb bajaradi
- **Himoya:** output encoding, Content Security Policy (CSP)

### 1.3 Cross-Site Request Forgery (CSRF)
- Foydalanuvchi bilmagan holda uning nomidan so'rov yuborilishi
- CSRF token'lar qanday himoya qiladi

### 1.4 Server-Side Request Forgery (SSRF)
- Server orqali ichki tarmoq resurslariga (masalan, cloud metadata endpoint `169.254.169.254`) so'rov yuborish
- Zamonaviy cloud muhitlarida juda xavfli hujum turi

### 1.5 Broken Authentication / Access Control
- Session boshqaruvidagi xatolar, JWT noto'g'ri validatsiyasi
- IDOR (Insecure Direct Object Reference) — foydalanuvchi ID'ni o'zgartirib, boshqalarning ma'lumotiga kirish

### 1.6 Qolgan muhim toifalar
- Security Misconfiguration, Sensitive Data Exposure, XXE (XML External Entity), Insecure Deserialization

---

## 2. Amaliy vositalar

### 2.1 Burp Suite
- Proxy sifatida brauzer va server orasidagi trafikni ushlab turish
- Request'ni qo'lda o'zgartirib qayta yuborish (Repeater)
- Avtomatlashtirilgan skanerlash (Intruder) — brute-force va fuzzing uchun

### 2.2 Brauzer DevTools
- Network tab orqali so'rov/javoblarni tahlil qilish
- Console orqali JS injection'larni sinash

### 2.3 Boshqa foydali tool'lar
- `sqlmap` — SQL injection'ni avtomatlashtirish (lekin avval qo'lda tushunib, keyin ishlating)
- `ffuf`/`gobuster` — dizayn/fayl fuzzing (yashirin endpoint'larni topish)

---

## 3. Laboratoriyalar (amaliyot qilish joylari)

| Platforma | Nega tavsiya etiladi |
|---|---|
| **PortSwigger Web Security Academy** | Bepul, eng chuqur va tizimli — har bir zaiflik nazariy tushuntirish + interaktiv lab bilan keladi |
| DVWA (Damn Vulnerable Web Application) | Lokal o'rnatib, xavfsiz muhitda mashq qilish uchun |
| TryHackMe (Web fundamentals yo'li) | Boshlang'ichlar uchun yo'naltirilgan, video bilan |
| HackTheBox (Web challenges) | Murakkabroq, real dunyoga yaqin senariylar |

**Tavsiya:** PortSwigger Academy'ni tizimli ravishda, har bir mavzuni tartib bilan o'tib chiqing — bu bepul resurslar orasida eng sifatlisi hisoblanadi.

---

## 4. Amaliy loyiha

**Vazifa:** Ataylab zaif qilib yozilgan oddiy web ilova (masalan, login formasi + qidiruv funksiyasi) yarating (PHP+MySQL yoki Node.js+SQLite), so'ngra:

1. Unga SQL injection orqali kirib ko'ring
2. XSS zaifligini joylashtirib, uni ekspluatatsiya qiling
3. Keyin — har ikkala zaiflikni **to'g'irlang** (parametrlangan so'rov, output encoding)

Bu — "hujum qiluvchi tafakkur" va "himoyachi tafakkur"ni bir vaqtda rivojlantiradi.

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak:

- [ ] OWASP Top 10'dagi har bir zaiflikni misol bilan tushuntira olasiz
- [ ] Burp Suite'da Proxy va Repeater'dan foydalana olasiz
- [ ] SQL injection'ni qo'lda (sqlmap'siz) topib, ekspluatatsiya qila olasiz
- [ ] Stored va Reflected XSS orasidagi farqni amaliyotda ko'rsata olasiz
- [ ] O'z zaif ilovangizni yozib, uni sindirib, keyin tuzatgan bo'lasiz

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| PortSwigger Web Security Academy | Eng to'liq bepul web xavfsizlik kursi |
| OWASP Top 10 rasmiy hujjati | Har yilgi eng dolzarb zaifliklar tahlili |
| *The Web Application Hacker's Handbook* | Chuqur va klassik kitob |
| DVWA / bWAPP | Lokal mashq qilish uchun zaif ilovalar |

**Keyingi qadam:** [`03-network-pentest/`](../03-network-pentest/README.md) — tarmoq penetratsion testi va Active Directory.

