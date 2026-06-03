---
id: exam_2025_B_B_MultipleChoice_q9
title: SRP in Invoice Class
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID - SRP
skills:
- SOLID Principles
- Class Design
---

## Question
נתונה מחלקה בשם `Invoice` שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון SRP?

### Options
- פעולה שבודקת אם הלקוח של החשבונית הוא חבר מועדון - `public boolean checkClubMembership()`
- פעולה שבודקת אם בחשבונית אין פריטים לחיוב - `public boolean isEmpty()`
- פעולה שמחשבת את הסכום הכולל של הפריטים - `public double getTotalAmount()`
- פעולה שמוסיפה פריט לחשבונית - `public void addItem(double price)`

## Answer
עיקרון האחריות היחידה (SRP) קובע שלמחלקה צריכה להיות רק סיבה אחת להשתנות. מחלקת `Invoice` אחראית על ניהול פרטי החשבונית (הוספת פריטים, חישוב סכום, בדיקת ריקות). בדיקת חברות במועדון (`checkClubMembership`) היא אחריות שקשורה ללקוח או למערכת ניהול לקוחות, ולא ישירות לחשבונית עצמה. לכן, פונקציה זו מפרה את SRP.
