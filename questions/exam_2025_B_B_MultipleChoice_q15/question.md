---
id: exam_2025_B_B_MultipleChoice_q15
title: Template Method Implementation
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- WMS - Template method
- Design patterns - General
skills:
- Design Patterns
- Inheritance
- Polymorphism
---

## Question
כיצד יש לממש את תבנית העיצוב `template method`?

### Options
- ליצור מימושים שונים במחלקות היורשות לפונקציה מופשטת שנקראת מתוך פונקציה במחלקת הבסיס.
- לתאם בין מחלקות נתונות לממשק שהגדרנו ושאין לשנותו.
- להגדיר במחלקות היורשות פונקציות שקוראות לפונקציה מופשטת של מחלקת הבסיס.
- ליצור פונקציה במחלקות היורשות, שהמימוש שלה יופיע במחלקת הבסיס.

## Answer
תבנית ה-Template Method מגדירה את השלד של אלגוריתם בפעולה של מחלקת בסיס, אך מאפשרת למחלקות יורשות לשנות שלבים מסוימים באלגוריתם מבלי לשנות את המבנה הכללי שלו. זה מושג על ידי קריאה לפונקציות מופשטות (או 'ווים' - hook methods) מתוך פונקציית ה-template method במחלקת הבסיס, כאשר המימוש הספציפי של פונקציות אלו ניתן במחלקות היורשות.
