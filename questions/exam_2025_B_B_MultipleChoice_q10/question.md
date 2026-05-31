---
id: exam_2025_B_B_MultipleChoice_q10
title: SRP ו-Invoice Class
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- Single Responsibility Principle (SRP)
- Class Design
skills:
- Principle Application
- Class Responsibility
---

## Question
נתונה מחלקה בשם Invoice שמייצגת חשבונית. לפניך מספר פעולות הקשורות למחלקה. איזו מהפונקציות הבאות אינה שייכת למחלקה על פי עקרון SRP?

### Options
- פעולה שבודקת אם הלקוח של החשבונית הוא חבר מועדון - public boolean checkClubMembership)(
- פעולה שבודקת אם בחשבונית אין פריטים לחיוב - public boolean isEmpty)(
- פעולה שמחשבת את הסכום הכולל של הפריטים - public double getTotalAmount)(
- פעולה שמוסיפה פריט לחשבונית - public void addItem(double price(

## Answer
עיקרון האחריות היחידה (SRP) קובע שלמחלקה צריכה להיות רק סיבה אחת לשינוי. מחלקת `Invoice` אחראית על ניהול פרטי החשבונית (פריטים, סכום כולל וכו'). הפונקציה `checkClubMembership()` בודקת מידע הקשור ללקוח ולתוכנית מועדון, וזו אחריות שונה מאחריות החשבונית עצמה. לכן, פעולה זו אינה שייכת למחלקת `Invoice` לפי SRP, ועדיף שתהיה במחלקה נפרדת כמו `Customer` או `MembershipService`.
