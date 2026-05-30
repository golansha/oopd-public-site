---
id: exam_2025_B_B_MultipleChoice_q14
title: Dependency Injection Definition
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Dependency Injection
- IoC
- Software Architecture
skills:
- DI Understanding
- Design Concepts
---

## Question
Dependency Injection - "הזרקת תלויות" סמן מהמשפטים הבאים את הנכון ביותר:

### Options
- Dependency Injection הוא שיטה מובנית לאתחול אובייקטים המזריקה עבורם את השדות שהם תלויים בהם.
- ישנן שתי תשובות אחרות נכונות.
- כדי להזריק תלויות באמצעות Dependency Injection, השדות המוזרקים חייבים להיות מוגדרות כממשקים.
- אם מזריקים למחלקה שדה מסוג ממשק, שאותו מממשות כמה מחלקות, יש דו משמעות ולא ניתן להגדיר מאיזה מחלקה יהיה האובייקט שיוזרק.

## Answer
המשפט הנכון ביותר הוא: "Dependency Injection הוא שיטה מובנית לאתחול אובייקטים המזריקה עבורם את השדות שהם תלויים בהם." זהו התיאור המדויק ביותר של DI, שבו התלויות (dependencies) של אובייקט מסופקות לו מבחוץ (מוזרקות) במקום שהוא ייצור אותן בעצמו. שאר האפשרויות שגויות או לא מדויקות: שדות מוזרקים לא חייבים להיות ממשקים (אף שזה מומלץ), ומסגרות DI יודעות לטפל במקרים של ריבוי מימושים לממשק באמצעות הגדרות קונפיגורציה.
