---
id: exam_2025_B_B_MultipleChoice_q10
title: SRP Violation in Invoice Class
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- Single Responsibility Principle (SRP)
- Object-Oriented Design
skills:
- SRP Application
- Code Analysis
---

## Question
נתונה מחלקה בשם Invoice שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון SRP?

### Options
- public boolean checkClubMembership()
- public boolean isEmpty()
- public double getTotalAmount()
- public void addItem(double price)

## Answer
הפונקציה `public boolean checkClubMembership()` אינה שייכת למחלקת `Invoice` על פי עיקרון האחריות היחידה (SRP). תפקידה של מחלקת `Invoice` הוא לנהל את פרטי החשבונית (פריטים, סכומים, סטטוס). בדיקת חברות במועדון היא אחריות של מחלקת `Customer` או שירות ניהול חברות, ולא של החשבונית עצמה. שאר הפונקציות (בדיקת ריקות, חישוב סכום כולל, הוספת פריט) קשורות ישירות לניהול החשבונית.
