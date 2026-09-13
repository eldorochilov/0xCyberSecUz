# 💻 Dasturlash Asoslari

> **00-foundations / 03-programming-fundamentals**
> Binary exploitation va reverse engineering'ni tushunish uchun kodni "yozish"dan ko'ra, kod qanday xotirada yashashini tushunish muhimroq.

---

## 🎯 Nima uchun kerak?

`04-binary-exploitation`, `05-reverse-engineering` va `06-arm64-asm` bo'limlari C tilini va dasturlash mantig'ini bilishni talab qiladi. Bu bo'lim — o'sha bo'limlarga sakrash uchun trambut.

---

## 📚 Mavzular ro'yxati

### 1. C tili asoslari
- O'zgaruvchilar, turlar (`int`, `char`, `float`, `struct`)
- Shart operatorlari va sikllar (`if`, `for`, `while`)
- Funksiyalar va scope tushunchasi
- Kompilyatsiya jarayoni: `gcc` bilan `.c` fayldan bajariluvchi fayl olish

### 2. Xotira bilan ishlash (C uchun eng muhim qism)
- Stack vs Heap
- Pointerlar — nima uchun ular "qo'rqinchli" emas
- `malloc`, `free` va xotira sizib chiqishi (memory leak)
- Buffer nima va u qanday to'lib ketishi mumkin (keyingi bo'limga tayyorgarlik)

### 3. Kompilyatsiya va bog'lash (build) jarayoni
- Preprocessor → Compiler → Assembler → Linker
- `.o` fayllar va statik/dinamik kutubxonalar
- `Makefile` asoslari

### 4. Debugging asoslari
- `gdb` bilan birinchi tanishuv: breakpoint, step, watch
- `printf` debugging vs real debugger
- Segmentation fault nima va nega yuzaga keladi

### 5. Python — avtomatlashtirish uchun
- Skript yozish mantiqi (fayllar, argumentlar, sikllar)
- `requests`, `socket` kutubxonalari — tarmoq bilan ishlash uchun asos
- Nega pentesterlar Python'ni sevadi (tezkor prototip yaratish)

---

## 🛠 Amaliyot topshiriqlari

- [ ] Oddiy C dasturi yozing: ikkita sonni qo'shuvchi funksiya, pointer orqali natijani qaytaring
- [ ] `malloc` bilan xotira ajratib, keyin `free` qilmasdan dasturni tugating — `valgrind` bilan sizib chiqishni ko'ring
- [ ] `gdb` orqali oddiy C dasturga breakpoint qo'yib, o'zgaruvchi qiymatlarini kuzating
- [ ] Python'da IP manzilga ping yuboruvchi kichik skript yozing

---

## 📖 Qo'shimcha manbalar

- *The C Programming Language* — Kernighan & Ritchie (K&R)
- [beej.us/guide](https://beej.us/guide/) — C va tarmoq dasturlash bo'yicha bepul qo'llanmalar
- `gdb` rasmiy dokumentatsiyasi

---

⬅️ [Orqaga: 02-networking-basics](../02-networking-basics/README.md) | ➡️ [Keyingi: 04-binary-exploitation](../../04-binary-exploitation/README.md)

