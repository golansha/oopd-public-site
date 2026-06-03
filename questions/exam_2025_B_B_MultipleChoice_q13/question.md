---
id: exam_2025_B_B_MultipleChoice_q13
title: Dependency Injection Definition
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Frameworks - Dependency injection
skills:
- Dependency Injection
- Software Design
---

## Question
Dependency Injection - "הזרקת תלויות"
סמן מהמשפטים הבאים את הנכון ביותר:

### Options
- Dependency Injection הוא שיטה מובנית לאתחול אובייקטים המזריקה עבורם את השדות שהם תלויים בהם.
- ישנן שתי תשובות אחרות נכונות.
- כדי להזריק תלויות באמצעות Dependency Injection, השדות המוזרקים חייבים להיות מוגדרות כממשקים.
- אם מזריקים למחלקה שדה מסוג ממשק, שאותו מממשות כמה מחלקות, יש דו משמעות ולא ניתן להגדיר מאיזה מחלקה יהיה האובייקט שיוזרק.

## Answer
המשפט הראשון מתאר בצורה מדויקת את Dependency Injection: זוהי טכניקה שבה אובייקטים מקבלים את התלויות שלהם (שדות, פרמטרים) מבחוץ, במקום ליצור אותן בעצמם. זה מקדם צימוד רפוי (loose coupling) וקלות בבדיקות. שדות מוזרקים לא חייבים להיות ממשקים (אף שזה מומלץ), וניתן לפתור דו-משמעות בהזרקה של ממשקים באמצעות קונפיגורציה או שימוש באנוטציות כמו `@Named`.
