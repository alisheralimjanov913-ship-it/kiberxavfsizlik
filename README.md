# kiberxavfsizlik---

```mermaid
flowchart TD
    A[Hujjat va Xabar] --> B[Xesh funksiyasi SHA-256]
    B --> C[Xesh qiymat H]
    C --> D[Yopiq kalit bilan imzolash]
    D --> E[Elektron raqamli imzo S]

    E --> F[Yuborish]
    A --> F

    F --> G[Qabul qiluvchi]

    G --> H[Xabarni xeshlash SHA-256]
    H --> I[Yangi xesh H1]

    G --> J[Imzoni ochish ochiq kalit bilan]
    J --> K[Xesh H2]

    I --> L{H1 = H2?}
    K --> L

    L -- Ha --> M[Imzo haqiqiy]
    L -- Yo‘q --> N[Imzo haqiqiy emas]
```
```mermaid
flowchart TD
    A[Dasturni ishga tushirish] --> B[generate_keys funksiyasini chaqirish]

    B --> C[RSA yopiq kalitni yaratish\npublic_exponent = 65537\nkey_size = 2048]
    C --> D[Yopiq kalitdan\nochiq kalitni olish]

    D --> E[private.pem faylini ochish\n-yazish rejimi-]
    E --> F[Yopiq kalitni PEM formatda\nsaqlash\n-PKCS8, shifrlanmagan-]

    F --> G[public.pem faylini ochish\n-yazish rejimi-]
    G --> H[Ochiq kalitni PEM formatda\nsaqlash\n-SubjectPublicKeyInfo-]

    H --> I[Kalitlar yaratildi\nxabarini chiqarish]
    I --> J[Dasturni yakunlash]
```
```mermaid
flowchart TD
    A[Start]
    B[Xabar kiritish]
    C[sign_message funksiyasini chaqirish]
    D[private.pem faylini o'qish]
    E[Yopiq kalitni yuklash]
    F[Xabarni UTF-8 ga o'tkazish]
    G[RSA bilan imzolash]
    H[SHA-256 + PKCS1v1.5]
    I[Imzoni HEX formatga o'tkazish]
    J[Imzoni ekranga chiqarish]
    K[End]

    A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K
```
```mermaid
flowchart TD
    A[Dasturni ishga tushirish] --> B[Foydalanuvchidan xabar kiritish]
    B --> C[Foydalanuvchidan imzo HEX kiritish]

    C --> D[verify message funksiyasini chaqirish]
    D --> E[Imzoni HEX baytga o‘tkazish]
    E --> F[public pem faylini ochish o‘qish rejimi]
    F --> G[Ochiq kalitni xotiraga yuklash]

    G --> H[Xabarni UTF-8 formatga o‘tkazish]
    H --> I[Xabarni SHA-256 bilan xeshlash]

    I --> J[RSA bilan imzoni tekshirish PKCS1v1.5 padding]
    J --> K[Natijani aniqlash: IMZO TO‘G‘RI / NOTO‘G‘RI]

    K --> L[Natijani foydalanuvchiga chiqarish]
    L --> M[Dasturni yakunlash]

