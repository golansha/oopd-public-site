---
id: exam_2025_B_A_MultipleChoice_q8
title: SOLID Principle Violation
year: 2025
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- SOLID - OCP
- SOLID - DIP
skills:
- Object-Oriented Design
- SOLID Principles
---

## Question
במערכת לניהול צי רכבים, יש מחלקת אב `Vehicle` ומספר מחלקות יורשות כגון `Car, Truck` וי `Motorcycle`. קיימת מחלקה `FleetManager` שמכילה מערך של כלי רכב ומספקת פונקציה `activateNavigationForCars` רק על כלי הרכב מסוג `Car` שמפעילה את מערכת הניווט (`GPS`) ```java public void activateNavigationForCars() { for (Vehicle v: vehicles) { if (v instanceof Car) { ((Car) v).activateNavigationSystem(); } } } ``` איזה עיקרון `SOLID` מופר בפונקציה `activateNavigationForCars`?

### Options
- `DIP` כי הפונקציה תלויה במחלקת `Car` קונקרטית במקום בממשק או במחלקת אב
- `OCP` כי הוספת סוגי כלי רכב חדשים תצריך שינוי בקוד הפונקציה
- `SRP` כי הפונקציה אחראית גם על סינון סוג הרכב וגם על הפעלת הניווט
- `LSP` כי מחלקות הירושה אינן מתנהגות בהתאם למחלקת האב

## Answer
הפונקציה `activateNavigationForCars` מפרה את עקרון הפתיחות/סגירות (OCP - Open/Closed Principle). עקרון זה קובע שישויות תוכנה (מחלקות, מודולים, פונקציות) צריכות להיות פתוחות להרחבה, אך סגורות לשינוי. במקרה זה, אם נוסיף סוג חדש של רכב (לדוגמה, `Boat`) שגם לו יש מערכת ניווט, נצטרך לשנות את קוד הפונקציה `activateNavigationForCars` כדי להוסיף בדיקה נוספת (`if (v instanceof Boat)`), וזה מפר את OCP. בנוסף, היא מפרה גם את DIP (Dependency Inversion Principle) בכך שהיא תלויה במחלקה קונקרטית (`Car`) במקום בהפשטה. עם זאת, האפשרות השנייה מתארת את הפרת OCP באופן ישיר וברור.
