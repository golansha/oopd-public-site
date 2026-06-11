---
id: exam_2025_B_B_MultipleChoice_q10
title: SRP Violation in Invoice Class
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- SOLID - SRP
skills: []
---

## Question
נתונה מחלקה בשם `Invoice` שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון `SRP`?

### Options
- `public boolean checkClubMembership()` - פעולה שבודקת אם הלקוח של החשבונית הוא חבר מועדון
- `public boolean isEmpty()` - פעולה שבודקת אם בחשבונית אין פריטים לחיוב
- `public double getTotalAmount()` - פעולה שמחשבת את הסכום הכולל של הפריטים
- `public void addItem(double price)` - פעולה שמוסיפה פריט לחשבונית

## Answer
The `Invoice` class should primarily be responsible for managing invoice details (items, total amount, etc.). Checking club membership is a responsibility related to customer management or loyalty programs, not the invoice itself. This violates the Single Responsibility Principle (SRP) by giving the `Invoice` class more than one reason to change.
