<div align="center">

# 🟠 05 — Reverse Engineering

![Daraja](https://img.shields.io/badge/Daraja-Advanced-F97316?style=for-the-badge)
![Muddat](https://img.shields.io/badge/Muddat-6--9_oy-F97316?style=for-the-badge)
![Ghidra](https://img.shields.io/badge/Ghidra-ED1C24?style=flat-square)

*Kodni manba kodisiz tahlil qilish san'ati*

</div>

> Reverse engineering — manba kodi bo'lmagan dasturni tushunish san'ati. Bu ko'nikma malware tahlili, CTF crackme'lari, va hatto legacy tizimlarni tushunishda hal qiluvchi ahamiyatga ega.

⚠️ **Oldingi shart:** [`04-binary-exploitation`](../04-binary-exploitation/README.md) bilan parallel yoki undan keyin o'tish tavsiya etiladi — ikkalasi bir-birini to'ldiradi: exploitation "buzish", reversing esa "tushunish"ga ko'proq urg'u beradi.

---

## 1️⃣ 🔬 Statik tahlil (dastur bajarilmasdan tahlil qilish)

<details open>
<summary><b>🖥️ Disassembler'lar</b></summary>
<br>

| Tool | Xususiyati |
|---|---|
| **Ghidra** | NSA tomonidan, bepul, ochiq manba, decompiler funksiyasi bilan assembly'ni C-ga o'xshash kodga aylantiradi |
| **radare2 / rizin** | Terminal-asosli, skriptlashtiriladigan, juda kuchli lekin o'rganish egri chizig'i tikroq |
| **IDA Free** | Sanoat standarti (pullik versiyasi ko'proq imkoniyat beradi) |

</details>

<details open>
<summary><b>🔎 Nima izlash kerak</b></summary>
<br>

- `main` funksiyasini topish, undan chaqiriladigan funksiyalar grafigini qurish
- Satrlar (strings) — parollar, xato xabarlari, debug ma'lumotlari ko'pincha dastur mantig'iga ishora qiladi
- Import qilingan funksiyalar (`strcmp`, `malloc`, tarmoq funksiyalari) — dastur nima qilishi haqida gipoteza tuzishga yordam beradi

</details>

---

## 2️⃣ ⏯️ Dinamik tahlil (dasturni ishga tushirib kuzatish)

- GDB/GEF bilan qadam-baqadam bajarish (`04-binary-exploitation`da o'rgangan ko'nikmalar bu yerda ham ishlatiladi)
- `strace`/`ltrace` — dastur qaysi syscall/kutubxona funksiyalarini chaqirayotganini kuzatish
- Breakpoint qo'yib, muhim taqqoslash (`cmp`) operatsiyalarini topish — bu ko'pincha "to'g'ri parol"ni aniqlash kaliti bo'ladi

---

## 3️⃣ 🕵️ Anti-analysis texnikalarini tanish

> Ba'zi dasturlar (ayniqsa malware yoki murakkab crackme'lar) tahlilni qiyinlashtirish uchun maxsus texnikalardan foydalanadi:

| Texnika | Tavsifi |
|---|---|
| 🚨 **Anti-debugging** | Dastur GDB ilova qilinganini aniqlab, xatti-harakatini o'zgartiradi (`ptrace` tekshiruvi) |
| 🌀 **Obfuskatsiya** | Kodni ataylab murakkablashtirish (keraksiz tarmoqlanishlar, junk instruksiyalar) |
| 📦 **Packing** | Binary'ni siqib/shifrlab, faqat ishga tushganda xotirada "ochish" (masalan, UPX packer) |

> 💡 Bu bosqichda faqat **tanish** darajasida yetarli — chuqur bypass texnikalari Pro darajasida keladi.

---

## 4️⃣ 🎯 Amaliy mashqlar: Crackme'lar

> **Crackme** — ataylab "parolni toping" yoki "seriyani yarating" tarzida yozilgan kichik dasturlar bo'lib, reverse engineering mashqi uchun ideal.

```mermaid
graph LR
    A["1️⃣ file + strings<br/>razvedka"] --> B["2️⃣ Ghidra'da<br/>decompile"]
    B --> C["3️⃣ GDB bilan<br/>tasdiqlash"]
    C --> D["4️⃣ Yechim +<br/>writeup"]

    style A fill:#FED7AA,stroke:#C2410C,color:#000
    style B fill:#FDBA74,stroke:#C2410C,color:#000
    style C fill:#FB923C,stroke:#9A3412,color:#000
    style D fill:#86EFAC,stroke:#15803D,color:#000
```

📍 **Platforma:** crackmes.one — turli qiyinlik darajasidagi minglab crackme'lar, community yechimlari bilan.

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak

- [ ] Ghidra'da binary'ni yuklab, `main` funksiyasidan boshlab mantiqni o'qiy olasiz
- [ ] `strings` va import funksiyalar orqali dastur maqsadi haqida gipoteza tuza olasiz
- [ ] GDB bilan muhim taqqoslash nuqtalarini topib, "to'g'ri kirish"ni aniqlay olasiz
- [ ] Kamida 3–5 ta oddiy/o'rta darajadagi crackme'ni mustaqil yechgan bo'lasiz
- [ ] Anti-debugging va packing nima ekanini, ularni qanday aniqlashni tushuntira olasiz

---

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| Ghidra rasmiy hujjatlari va video darslari | Eng keng qo'llaniladigan bepul decompiler |
| **crackmes.one** | Amaliy mashq uchun eng katta crackme kutubxonasi |
| *Practical Malware Analysis* | Reverse engineering va malware tahlili bo'yicha klassik kitob |
| radare2 Book | r2 bo'yicha rasmiy, chuqur qo'llanma |

---

<div align="center">

**◀** [🟠 04-binary-exploitation](../04-binary-exploitation/README.md) &nbsp;|&nbsp; **Keyingi qadam →** [🟠 06-arm64-asm](../06-arm64-asm/README.md)

</div>

