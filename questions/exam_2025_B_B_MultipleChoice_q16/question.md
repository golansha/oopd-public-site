---
id: exam_2025_B_B_MultipleChoice_q16
title: Template Method Implementation
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- Template Method Pattern
- Object-Oriented Programming
skills:
- Design Pattern Understanding
- Implementation Concepts
---

## Question
כיצד יש לממש את תבנית העיצוב template method?

### Options
- ליצור מימושים שונים במחלקות היורשות לפונקציה מופשטת שנקראת מתוך פונקציה במחלקת הבסיס.
- לתאם בין מחלקות נתונות לממשק שהגדרנו ושאין לשנותו.
- להגדיר במחלקות היורשות פונקציות שקוראות לפונקציה מופשטת של מחלקת הבסיס.
- ליצור פונקציה במחלקות היורשות, שהמימוש שלה יופיע במחלקת הבסיס.

## Answer
תבנית ה-Template Method (מתודת תבנית) ממומשת על ידי הגדרת שלד של אלגוריתם במתודה של מחלקת בסיס (ה'מתודה התבניתית'), כאשר חלק מהשלבים באלגוריתם מוגדרים כמתודות מופשטות (או 'ווים' - hooks) שמומשות על ידי המחלקות היורשות. כך, המחלקות היורשות יכולות לספק מימושים שונים לשלבים ספציפיים באלגוריתם מבלי לשנות את מבנה האלגוריתם הכללי.
