# 06 — ARM64 Assembly

> Assembly — protsessor bilan "to'g'ridan-to'g'ri" muloqot tili. Uni bilish sizga yuqori darajadagi tillar (C, Python) yashirgan barcha tafsilotlarni ko'rish imkonini beradi — bu esa `04-binary-exploitation` va `05-reverse-engineering` bo'limlarida bevosita ishlatiladi.

## Nega ARM64?
ARM64 (AArch64) — zamonaviy mobil qurilmalar, Apple Silicon, va tobora ko'proq server/cloud infratuzilmasida (AWS Graviton, Oracle Cloud Ampere) ishlatiladigan arxitektura. x86_64'dan farqli o'laroq, ARM64'ning registr-asosli, aniqroq tuzilgan instruksiya to'plami uni o'rganish uchun ham qulayroq qiladi.

---

## 1. Asosiy tushunchalar

### 1.1 Registrlar
- Umumiy maqsadli registrlar: `x0`–`x30` (64-bit), `w0`–`w30` (32-bit ko'rinishi)
- Maxsus registrlar: `sp` (stack pointer), `pc` (program counter), `x30`/`lr` (link register — qaytish manzili)
- `xzr`/`wzr` — doim nolga teng "zero registr"

### 1.2 Asosiy instruksiyalar
- Ma'lumot ko'chirish: `mov`, `ldr` (load), `str` (store)
- Arifmetika: `add`, `sub`, `mul`
- Shart va tarmoqlanish: `cmp`, `b.eq`, `b.ne`, `b` (branch), `bl` (branch with link — funksiya chaqirish)

### 1.3 Direktivalar
- `.section`, `.global _start` — dastur tuzilishi va kirish nuqtasi
- `.ascii` vs `.asciz` — farqi: `.asciz` avtomatik null-terminator (`\0`) qo'shadi, `.ascii` qo'shmaydi (bu farqni bilish, ayniqsa string bilan ishlaganda, ko'p xatolarning oldini oladi)
- `.byte`, `.word`, `.quad` — turli o'lchamdagi ma'lumot deklaratsiyasi

---

## 2. Syscall konvensiyasi (Linux ARM64)

Linux'da tizim chaqiruvlari (syscall) quyidagi konvensiya bo'yicha ishlaydi:

- Syscall raqami — `x8` registrida
- Argumentlar — `x0`–`x5` registrlarida (tartib bilan)
- Chaqiruv — `svc #0` instruksiyasi orqali amalga oshiriladi
- Natija — `x0` registrida qaytadi

### Muhim syscall raqamlari (ARM64)
| Syscall | Raqam | Vazifa |
|---|---|---|
| `write` | 64 | Fayl deskriptoriga yozish |
| `read` | 63 | Fayl deskriptoridan o'qish |
| `exit` | 93 | Dasturni tugatish |
| `execve` | 221 | Yangi dastur bajarish |

**Mashq:** `write` va `exit` syscall'laridan foydalanib, ekranga "Salom, dunyo!" chiqaruvchi dastur yozing (libc'siz, faqat toza assembly).

---

## 3. Calling Convention (AAPCS64)

C funksiyasini assembly'dan chaqirish yoki aksincha uchun quyidagi qoidalar muhim:

- Birinchi 8 ta argument `x0`–`x7` registrlarida uzatiladi
- Qaytish qiymati `x0`da (yoki `x0`+`x1`, agar 128-bit bo'lsa)
- `x19`–`x28` — "callee-saved" registrlar (funksiya ularni ishlatsa, avvalgi qiymatini saqlab, oxirida qaytarishi kerak)
- Stack 16-bayt chegarasiga tekislangan (aligned) bo'lishi shart — aks holda ba'zi instruksiyalar noto'g'ri ishlaydi

---

## 4. C + Assembly aralash loyihalar

Bu — assembly bilimini amaliyotga tatbiq etishning eng samarali yo'li: C dasturidan assembly funksiyasini chaqirish.

### Ishchi jarayon (workflow):
```bash
clang mainFayl.c asmFayl.s -o dastur
./dastur
```

### Nima uchun foydali:
- C tomonida murakkab mantiq (I/O, tuzilmalar) qoladi, assembly tomonida esa nozik, performance-kritik yoki o'rganish maqsadidagi qism yoziladi
- Bu — real dunyoda ham qo'llaniladigan yondashuv (masalan, kripto kutubxonalarida tezlik uchun assembly ishlatiladi)

**Mashq:** C'da e'lon qilingan (`extern`) funksiyani assembly'da amalga oshiring — masalan, ikkita sonni qo'shuvchi yoki massiv elementlarini yig'uvchi funksiya.

---

## 5. Debugging va tahlil

- `objdump -d` — kompilyatsiya qilingan dasturni disassemble qilish, kompilyator qanday kod generatsiya qilganini ko'rish
- GDB/GEF — registrlar va stack'ni real vaqtda kuzatish (bu ko'nikma `04-binary-exploitation`da to'g'ridan-to'g'ri ishlatiladi)
- Emulyatsiya uchun **Unicorn engine** — real qurilmasiz kod bajarilishini sinash

---

## 6. Manba materiallar haqida eslatma

Ko'p klassik assembly darsliklari (masalan, Zhirkovning kitobi) macOS/x86 uchun yozilgan bo'lishi mumkin. Bunday holatlarda:
- Syscall raqamlari va konvensiyasi Linux ARM64 uchun qayta moslashtirilishi kerak (yuqoridagi jadvaldan foydalaning)
- Registr nomlari va direktivalar sintaksisi farq qiladi (GAS/AT&T uslubidan ARM sintaksisiga)
- Har doim kodni **o'zingiz qayta yozib, ishga tushirib ko'ring** — faqat o'qish orqali bu ko'nikma shakllanmaydi

---

## ✅ Bu bosqichni tugatgach, siz quyidagilarni bilishingiz kerak:

- [ ] Asosiy registrlar va ularning maxsus vazifalarini (sp, lr, pc) tushuntira olasiz
- [ ] Faqat syscall'lar orqali (libc'siz) oddiy dastur yoza olasiz
- [ ] AAPCS64 calling convention'ga mos C+Assembly aralash dastur yoza olasiz
- [ ] `objdump`/GDB orqali kompilyatsiya qilingan kodni o'qib, mantiqni tiklay olasiz
- [ ] x86-ga mo'ljallangan materialni ARM64'ga mustaqil moslashtira olasiz

## 📚 Resurslar

| Resurs | Izoh |
|---|---|
| Azeria Labs | ARM/ARM64 assembly va exploitation bo'yicha eng yaxshi bepul resurs |
| ARM Architecture Reference Manual (ARMv8) | Rasmiy, to'liq texnik hujjat |
| pwn.college (Assembly moduli) | ARM64'ni amaliy, video bilan o'rgatadi |
| Linux syscall table (arm64) | Barcha syscall raqamlari va argumentlari ro'yxati |

**Keyingi qadam:** Ushbu bo'limdagi bilim bilan qaytadan [`04-binary-exploitation/`](../04-binary-exploitation/README.md) ga qayting — endi ROP va shellcode yozishni ancha chuqurroq tushunasiz.

