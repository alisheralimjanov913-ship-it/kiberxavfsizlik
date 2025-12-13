# kiberxavfsizlik---

```mermaid
flowchart TD
    A[Hujjat va Xabar] --> B[Xesh funksiyasi SHA-256]
    B --> C[Xesh qiymat H]
    C --> D[Yopiq kalit bilan imzolash]
    D --> E[Elektron raqamli imzo S]
…    J --> K[Xesh H2]

    I --> L{H1 = H2?}
    K --> L

    L -- Ha --> M[Imzo haqiqiy]
    L -- Yo‘q --> N[Imzo haqiqiy emas]
```
