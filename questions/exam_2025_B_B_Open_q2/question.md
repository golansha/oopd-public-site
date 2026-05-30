---
id: exam_2025_B_B_Open_q2
title: Package Design Principles - Violation and Correction
year: 2025
semester: B
moed: B
type: Open
topics:
- SOLID Principles
- Package Design
- Dependency Management
- UML
skills:
- Architectural Analysis
- Design Correction
- UML Diagramming
- Principle Application
---

## Question
(2 נקודות) איזה עיקרון בעיצוב חבילות מופר בתרשים שלפניך?(5 נקודות) כיצד ניתן לתקן זאת ללא העברה של מחלקות מחבילה לחבילה? שרטט תרשים חדש. אין צורך לשרטט מחדש חלקים בתרשים שלא השתנו. הסבר כיצד השינוי פותר את ההפרה.![Image](image_4_1.png)

## Answer
העיקרון המופר הוא **עיקרון היציבות המשותפת (Common Closure Principle - CCP)**.עיקרון CCP קובע כי מחלקות שמשתנות יחד מאותה סיבה צריכות להיות באותה חבילה. בתרשים, P1 תלוי ב-P2 (דרך A->H, C->J) ו-P3 תלוי ב-P2 (דרך D->J, F->K). בנוסף, P2 תלוי ב-P3 (דרך H->D). זה יוצר תלות מעגלית בין P2 ל-P3, וגם P1 תלוי בהם. אם P2 או P3 משתנים, זה עלול להשפיע על P1, מה שמקשה על תחזוקה ופריסה.התיקון יתבצע על ידי היפוך התלות המעגלית בין P2 ל-P3 באמצעות **עיקרון היפוך התלויות (Dependency Inversion Principle - DIP)**. במקום ש-P2 יתלה ישירות ב-P3, נגדיר ממשק ב-P2 ש-P3 יממש.כדי לתקן זאת ללא העברת מחלקות, נבצע את השינויים הבאים:1.  **הגדרת ממשק ב-P2:** ניצור ממשק חדש, למשל `IP3Service`, בתוך חבילה P2. הממשק יכיל את הפונקציונליות ש-H ב-P2 צריכה מ-D ב-P3 (למשל, מתודה `doSomethingD()`).2.  **מימוש הממשק ב-P3:** המחלקה D ב-P3 תממש את הממשק `IP3Service` שהוגדר ב-P2.3.  **היפוך התלות:** המחלקה H ב-P2 תתלה בממשק `IP3Service` (שנמצא באותה חבילה P2), ולא ישירות במחלקה D מ-P3. את המימוש של `IP3Service` (שהוא D) ניתן להזריק ל-H בזמן ריצה.תרשים מתוקן (רק החלקים שהשתנו):```mermaidgraph TD    subgraph P1        A --> B        C --> J    end    subgraph P2        H --> IP3Service(I)        J --> K        IP3Service(I)["interface IP3Service"]    end    subgraph P3        D -- implements --> IP3Service(I)        E        F --> G    end    H --> IP3Service(I)    D -- implements --> IP3Service(I)```הסבר:השינוי פותר את ההפרה בכך שהוא מונע תלות ישירה של P2 ב-P3 עבור הפונקציונליות ש-H צריכה מ-D. כעת, P2 תלוי בממשק `IP3Service` שנמצא בתוכו, ו-P3 תלוי בממשק זה (מממש אותו). זה שובר את התלות המעגלית ומאפשר ל-P2 ו-P3 להשתנות באופן עצמאי יותר, תוך שמירה על עיקרון CCP עבור כל חבילה בנפרד. P1 עדיין תלוי ב-P2 וב-P3, אך התלות המעגלית נשברה.
