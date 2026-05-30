---
id: exam_2025_B_B_MultipleChoice_q10
title: SRP Violation in Invoice Class
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- SRP
skills:
- Applying SRP to class design
---

## Question
נתונה מחלקה בשם Invoice שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון SRP?

### Options
- public boolean checkClubMembership() - פעולה שבודקת אם הלקוח של החשבונית הוא חבר מועדון
- public boolean isEmpty() - פעולה שבודקת אם בחשבונית אין פריטים לחיוב
- public double getTotalAmount() - פעולה שמחשבת את הסכום הכולל של הפריטים
- public void addItem(double price) - פעולה שמוסיפה פריט לחשבונית

## Answer
עיקרון האחריות היחידה (SRP) קובע שלמחלקה צריכה להיות אחריות אחת בלבד. מחלקת `Invoice` אחראית על ניהול נתוני החשבונית (פריטים, סכום כולל וכו'). הפעולה `checkClubMembership()` בודקת מאפיין של הלקוח הקשור לחשבונית, ולא מאפיין או התנהגות של החשבונית עצמה. אחריות זו שייכת למחלקת `Customer` או לשירות ניהול חברות, ולא למחלקת `Invoice`.
