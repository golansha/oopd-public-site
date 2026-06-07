---
id: exam_2024_B_B_MultipleChoice_q10
title: SOLID Principles in Army Management
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- SOLID - LSP
- UML - תרשים מחלקות
skills: []
---

## Question
נתון מבנה המחלקות הבא עבור מערכת לניהול כוח אדם בצבא. מה ניתן לומר על עמידת העיצוב בעקרונות SOLID
![Image](image_13_1.png)

### Options
- אף אחת מהתשובות האחרות אינה נכונה
- העיצוב מפר את עקרון ה DIP מאחר ויש לנו תלות בין שתי מחלקות יורשות. על מנת למנוע את ההפרה יש להגדיר את ההיררכיה הבאה: המפקד צריך לרשת מהחייל והחייל מהאדם.
- העיצוב מפר את עקרון ה SRP מאחר האדם עושה כמה דברים שונים.
- העיצוב מפר את עקרון LSP מאחר והמפקד והחייל מכילים פונקציות פומביות שלא הוגדרו במחלקה הבסיסית. העיצוב נכשל במבחן הזיוף.

## Answer
The design violates the Liskov Substitution Principle (LSP). LSP states that objects of a superclass should be replaceable with objects of its subclasses without breaking the application. Here, `Commander` and `Soldier` are subclasses of `Person`. If `Person` has methods like `eat()` and `drink()`, and `Commander` or `Soldier` introduce new public methods (`command()`, `fight()`) that are not applicable to a generic `Person`, or if they change the behavior of inherited methods in a way that breaks the `Person` contract, then LSP is violated. The option specifically mentions `Commander` and `Soldier` having public functions not defined in the base class, which is a common LSP violation.
