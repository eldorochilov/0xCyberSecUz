<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:2C5364,100:00FF87&height=220&section=header&text=03%20-%20Programming%20Fundamentals&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Xotiradan%20boshlab%20mantiqqacha&descAlignY=58&descSize=18" width="100%"/>

<p>
  <img src="https://img.shields.io/badge/Level-Beginner-brightgreen?style=for-the-badge&logo=leveldb&logoColor=white"/>
  <img src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white"/>
  <img src="https://img.shields.io/badge/GDB-A42E2B?style=for-the-badge&logo=gnu&logoColor=white"/>
</p>

<p>
  <img src="https://img.shields.io/badge/Til-O'zbek-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Vaqt-10--15%20soat-yellow?style=flat-square"/>
  <img src="https://img.shields.io/badge/Bo'lim-00--foundations-purple?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Active-success?style=flat-square"/>
</p>

</div>

## 📖 Kirish

Xavfsizlik mutaxassisi dasturchi bo'lishi shart emas, lekin **kod qanday ishlashini** tushunmasdan turib zaiflik topib bo'lmaydi. Ayniqsa **binary exploitation** va **reverse engineering** yo'nalishlarida C tili va xotira boshqaruvini bilish — majburiy poydevor.

Bu bo'limda biz **C tiliga** asosiy urg'u beramiz (chunki u xotira bilan bevosita ishlaydi va keyingi `04-binary-exploitation`, `06-arm64-asm` bo'limlari uchun zarur), shuningdek **Python**ni avtomatlashtirish va skript yozish vositasi sifatida qisqacha ko'rib chiqamiz.

> 💡 **Falsafa:** Python — tezkor vosita (pwntools, scapy uchun). C — tizim qanday ishlashini "ichkaridan" tushunish uchun til.

---

## 🗂️ Mavzular xaritasi

<table>
<tr><th>№</th><th>Mavzu</th><th>Nimani o'rganasiz</th></tr>
<tr><td>1</td><td><a href="#1-dastur-qanday-bajariladi">Dastur qanday bajariladi</a></td><td>Kompilyatsiya, source→binary jarayoni</td></tr>
<tr><td>2</td><td><a href="#2-ozgaruvchilar-va-malumot-turlari">O'zgaruvchilar va ma'lumot turlari</a></td><td>int, char, float, o'lcham</td></tr>
<tr><td>3</td><td><a href="#3-operatorlar-va-shart-operatorlari">Operatorlar va shartlar</a></td><td>if/else, mantiqiy operatorlar</td></tr>
<tr><td>4</td><td><a href="#4-sikllar-loops">Sikllar (loops)</a></td><td>for, while, do-while</td></tr>
<tr><td>5</td><td><a href="#5-funksiyalar">Funksiyalar</a></td><td>Parametr, qaytish qiymati, scope</td></tr>
<tr><td>6</td><td><a href="#6-massivlar-va-satrlar-arrays--strings">Massivlar va satrlar</a></td><td>array, char[], indekslash</td></tr>
<tr><td>7</td><td><a href="#7-pointerlar-korsatkichlar">Pointerlar (ko'rsatkichlar)</a></td><td>&, *, manzil bilan ishlash</td></tr>
<tr><td>8</td><td><a href="#8-xotira-boshqaruvi-stack-va-heap">Stack va Heap</a></td><td>malloc/free, xotira tuzilishi</td></tr>
<tr><td>9</td><td><a href="#9-struct-va-malumot-tuzilmalari">Struct'lar</a></td><td>Murakkab ma'lumot tuzilmalari</td></tr>
<tr><td>10</td><td><a href="#10-fayllar-bilan-ishlash-io">Fayllar bilan ishlash (I/O)</a></td><td>fopen, fread, fwrite</td></tr>
<tr><td>11</td><td><a href="#11-kompilyatsiya-jarayoni-chuqur">Kompilyatsiya jarayoni (chuqur)</a></td><td>Preprocessor → Assembly → ELF</td></tr>
<tr><td>12</td><td><a href="#12-python-tezkor-skriptlash-uchun">Python — tezkor skriptlash</a></td><td>Asosiy sintaksis, avtomatlashtirish</td></tr>
<tr><td>13</td><td><a href="#13-debugging-asoslari-gdb">Debugging asoslari (GDB)</a></td><td>Breakpoint, step, xotirani ko'rish</td></tr>
</table>

---

## 1. Dastur qanday bajariladi

```
Manba kod (.c)  →  Kompilyator  →  Assembly (.s)  →  Object fayl (.o)  →  Bog'lovchi (linker)  →  Bajariluvchi fayl (binary)
```

```bash
gcc main.c -o dastur      # to'g'ridan-to'g'ri bajariluvchi fayl yaratish
clang main.c -o dastur    # Clang orqali ham xuddi shunday
./dastur                  # ishga tushirish
```

CPU faqat **mashina kodini** (0 va 1) tushunadi. C kodi avval assembly'ga, so'ng mashina kodiga aylantiriladi — bu jarayonni 11-bo'limda chuqurroq ko'ramiz.

---

## 2. O'zgaruvchilar va ma'lumot turlari

```c
#include <stdio.h>

int main() {
    int yosh = 25;              // butun son, 4 bayt
    float narx = 19.99;         // kasr son, 4 bayt
    char harf = 'A';            // bitta belgi, 1 bayt
    char ism[] = "Eldor";       // satr (char massivi)

    printf("Yosh: %d, Narx: %.2f, Harf: %c\n", yosh, narx, harf);
    return 0;
}
```

| Tur | O'lcham (odatda) | Misol |
|---|---|---|
| `char` | 1 bayt | `'A'` |
| `int` | 4 bayt | `42` |
| `float` | 4 bayt | `3.14` |
| `double` | 8 bayt | `3.14159265` |
| `long` | 8 bayt (ARM64) | `1000000000L` |

> 🎯 **ARM64 uchun muhim:** `sizeof()` operatori orqali har bir turning aniq o'lchamini tekshirib ko'ring — bu keyinchalik stack tuzilishini tushunishda kerak bo'ladi.

---

## 3. Operatorlar va shart operatorlari

```c
int a = 10, b = 20;

if (a > b) {
    printf("a kattaroq\n");
} else if (a == b) {
    printf("teng\n");
} else {
    printf("b kattaroq\n");
}
```

| Operator | Ma'nosi |
|---|---|
| `==` | teng |
| `!=` | teng emas |
| `>`, `<`, `>=`, `<=` | solishtirish |
| `&&` | mantiqiy VA |
| \|\| | mantiqiy YOKI |
| `!` | inkor (NOT) |

---

## 4. Sikllar (loops)

```c
// for sikli
for (int i = 0; i < 5; i++) {
    printf("i = %d\n", i);
}

// while sikli
int n = 0;
while (n < 5) {
    printf("n = %d\n", n);
    n++;
}

// do-while — kamida bir marta bajariladi
int x = 0;
do {
    printf("x = %d\n", x);
    x++;
} while (x < 3);
```

---

## 5. Funksiyalar

```c
int kupaytir(int a, int b) {
    return a * b;
}

int main() {
    int natija = kupaytir(4, 5);
    printf("Natija: %d\n", natija);
    return 0;
}
```

Funksiyalar — kodni qayta ishlatiladigan bloklarga bo'lish imkonini beradi. Har bir funksiya chaqirilganda **stack frame** yaratiladi — bu tushuncha binary exploitation uchun juda muhim (stack overflow hujumlari aynan shu joyga qaratilgan).

---

## 6. Massivlar va satrlar (arrays & strings)

```c
int sonlar[5] = {1, 2, 3, 4, 5};
printf("Uchinchi element: %d\n", sonlar[2]);   // indeks 0 dan boshlanadi

char ism[20] = "Eldor";
printf("Ism: %s, uzunligi: %lu\n", ism, strlen(ism));
```

> ⚠️ **Xavfsizlik nuqtai nazaridan MUHIM:** C tilida massiv chegaralari **avtomatik tekshirilmaydi**. Agar `sonlar[10]`ga yozsangiz, dastur xotiraning boshqa qismini buzib qo'yishi mumkin — bu aynan **buffer overflow** zaifligining sababi.

---

## 7. Pointerlar (ko'rsatkichlar)

Pointer — bu boshqa o'zgaruvchining **xotiradagi manzilini** saqlaydigan o'zgaruvchi. Bu C tilining eng muhim va binary exploitation uchun eng zarur tushunchasi.

```c
int son = 42;
int *ptr = &son;      // ptr endi son'ning manzilini saqlaydi

printf("Qiymati: %d\n", son);
printf("Manzili: %p\n", (void*)&son);
printf("Pointer orqali: %d\n", *ptr);   // * — manzildagi qiymatni oladi (dereference)

*ptr = 100;            // manzil orqali qiymatni o'zgartirish
printf("Yangi qiymat: %d\n", son);   // 100
```

| Belgi | Ma'nosi |
|---|---|
| `&x` | x'ning manzilini oladi |
| `*ptr` | ptr ko'rsatayotgan manzildagi qiymatni oladi |
| `int *ptr` | ptr — int turidagi ma'lumotga ko'rsatkich |

---

## 8. Xotira boshqaruvi: Stack va Heap

```
Yuqori manzillar
┌─────────────────┐
│      Stack       │  ← funksiya chaqiruvlari, lokal o'zgaruvchilar (avtomatik boshqariladi)
│        ↓          │
│                   │
│        ↑          │
│       Heap        │  ← malloc() bilan qo'lda ajratiladigan xotira
├─────────────────┤
│       BSS         │  ← ishga tushirilmagan global o'zgaruvchilar
├─────────────────┤
│      Data         │  ← ishga tushirilgan global o'zgaruvchilar
├─────────────────┤
│      Text         │  ← dasturning o'zi (mashina kodi)
└─────────────────┘
Past manzillar
```

```c
int *raqam = malloc(sizeof(int));   // heap'da xotira ajratish
*raqam = 42;
printf("%d\n", *raqam);
free(raqam);                        // xotirani bo'shatish — MAJBURIY!
```

> ⚠️ `free()` qilinmagan xotira **memory leak**ka olib keladi. Ikki marta `free()` qilish esa **double-free** zaifligiga sabab bo'ladi — bu haqiqiy CVE'larda tez-tez uchraydigan xato turi.

---

## 9. Struct'lar va ma'lumot tuzilmalari

```c
struct Foydalanuvchi {
    char ism[30];
    int yosh;
    float balans;
};

int main() {
    struct Foydalanuvchi eldor = {"Eldor", 20, 150.50};
    printf("%s, %d yosh\n", eldor.ism, eldor.yosh);
    return 0;
}
```

Struct'lar xotirada ketma-ket joylashadi — bu bilim ELF fayllar va exploit yozishda ma'lumot tuzilmalarini tushunishga yordam beradi.

---

## 10. Fayllar bilan ishlash (I/O)

```c
#include <stdio.h>

int main() {
    FILE *f = fopen("malumot.txt", "w");
    if (f == NULL) {
        printf("Faylni ochib bo'lmadi\n");
        return 1;
    }
    fprintf(f, "Salom, dunyo!\n");
    fclose(f);
    return 0;
}
```

---

## 11. Kompilyatsiya jarayoni (chuqur)

```bash
gcc -E main.c -o main.i       # 1. Preprocessor (macro, #include kengaytiriladi)
gcc -S main.i -o main.s       # 2. Assembly kodga aylantirish
gcc -c main.s -o main.o       # 3. Object fayl (mashina kodi, lekin bog'lanmagan)
gcc main.o -o dastur          # 4. Linker — bajariluvchi ELF fayl yaratadi
```

ARM64'da o'zingizning workflow'ingiz:

```bash
clang mainFayl.c asmFayl.s -o dastur    # C + Assembly birgalikda kompilyatsiya
readelf -h dastur                        # ELF header'ni ko'rish
objdump -d dastur                        # disassemble qilib, assembly ko'rish
```

Bu bilim `06-arm64-asm` va `04-binary-exploitation` bo'limlarida to'g'ridan-to'g'ri qo'llaniladi.

---

## 12. Python — tezkor skriptlash uchun

Python xavfsizlikda **avtomatlashtirish** va **exploit yozish** (pwntools, scapy) uchun ishlatiladi — C o'rnini bosmaydi, balki uni to'ldiradi.

```python
#!/usr/bin/env python3

# Oddiy port skaner namunasi
import socket

def port_tekshir(host, port):
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(0.5)
    natija = s.connect_ex((host, port))
    s.close()
    return natija == 0

for port in [22, 80, 443, 3306]:
    if port_tekshir("127.0.0.1", port):
        print(f"Port {port} ochiq")
```

```bash
python3 skaner.py
```

---

## 13. Debugging asoslari (GDB)

```bash
gdb ./dastur
```

| GDB buyrug'i | Vazifasi |
|---|---|
| `break main` | main funksiyasiga breakpoint qo'yish |
| `run` | dasturni ishga tushirish |
| `next` / `n` | keyingi qatorga o'tish |
| `step` / `s` | funksiya ichiga kirish |
| `print x` | o'zgaruvchi qiymatini ko'rish |
| `info registers` | registrlar holatini ko'rish (ARM64: x0-x30) |
| `x/10x $sp` | stack'dagi 10 ta so'zni hex formatda ko'rish |
| `continue` / `c` | keyingi breakpointgacha davom etish |

> 💡 Siz allaqachon GDB'ni `-x init.gdb` skriptlari orqali `_start`ga breakpoint qo'yib ishlatgansiz — bu ko'nikma shu bo'limning davomi va `04-binary-exploitation`da yanada chuqurlashadi.

---

## ✅ Amaliy topshiriqlar (checklist)

- [ ] "Hello, World" dasturini C'da yozib, `gcc` bilan kompilyatsiya qiling
- [ ] Ikki son yig'indisini hisoblovchi funksiya yozing va uni `main()`dan chaqiring
- [ ] Pointer yordamida ikkita o'zgaruvchi qiymatini almashtiruvchi (`swap`) funksiya yozing
- [ ] `malloc`/`free` yordamida dinamik massiv yarating va to'ldiring
- [ ] Kichik `struct` yaratib, unga 3 ta ma'lumot maydonini qo'shing
- [ ] `gcc -S` bilan o'zingizning oddiy dasturingizni assembly kodga aylantirib ko'ring
- [ ] `objdump -d` bilan kompilyatsiya qilingan faylni disassemble qiling
- [ ] GDB'da oddiy dasturingizga breakpoint qo'yib, `step` va `print` bilan ishlatib ko'ring
- [ ] Python'da oddiy port-skaner skript yozing (yuqoridagi namuna asosida)
- [ ] Ataylab massiv chegarasidan tashqariga yozib (`array[10]` 5 elementli massivda), natijani kuzating

---

## 📚 Qo'shimcha resurslar

| Manba | Tavsif | Havola |
|---|---|---|
| K&R "The C Programming Language" | C tilining klassik kitobi | Kernighan & Ritchie |
| Learn-C.org | Interaktiv, bepul C darsligi | learn-c.org |
| Beej's Guide to C | Tushunarli, bepul PDF qo'llanma | beej.us |
| CS50 (Harvard) | Dasturlash asoslariga kirish kursi | cs50.harvard.edu |
| pwn.college | Xavfsizlikka yo'naltirilgan dasturlash/pwn kursi | pwn.college |

---

<div align="center">

⬅️ **Oldingi:** [02-networking-basics](../02-networking-basics/README.md) &nbsp;&nbsp;|&nbsp;&nbsp; **Keyingi:** [01-beginner](../../01-beginner/README.md) ➡️

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00FF87,50:2C5364,100:0F2027&height=120&section=footer" width="100%"/>

</div>

