---
id: exam_2025_B_B_MultipleChoice_q10
title: הפרת SRP במחלקת `Invoice`
year: 2025
semester: B
moed: B
type: Multiple Choice
topics: []
skills: []
---

## Question
נתונה מחלקה בשם `Invoice` שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון `SRP`?

### Options
- פעולה שבודקת אם הלקוח של החשבונית הוא חבר מועדון - `public boolean checkClubMembership()`
- פעולה שבודקת אם בחשבונית אין פריטים לחיוב - `public boolean isEmpty()`
- פעולה שמחשבת את הסכום הכולל של הפריטים - `public double getTotalAmount()`
- פעולה שמוסיפה פריט לחשבונית - `public void addItem(double price)`

## Answer
עקרון `SRP` (Single Responsibility Principle) קובע שלמחלקה צריכה להיות אחריות אחת ויחידה. מחלקת `Invoice` אחראית על ניהול פרטי החשבונית (הוספת פריטים, חישוב סכום כולל, בדיקה אם ריקה). בדיקת חברות במועדון (`checkClubMembership()`) היא אחריות שקשורה ללקוח או למערכת ניהול לקוחות, ולא ישירות לחשבונית עצמה. לכן, פעולה זו מפרה את `SRP`.
