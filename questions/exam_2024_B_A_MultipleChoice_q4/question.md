---
id: exam_2024_B_A_MultipleChoice_q4
title: יחסי ירושה וקומפוזיציה ב-UML
year: 2024
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- UML - תרשים מחלקות
- Package design - Coupling
skills: []
---

## Question
נתונים שני ממשקים `IB` `IA` ומחלקה `C`.
איזו מהשורות הבאות יכולה לעבור קומפילציה?
![Image](image_12_1.png)

### Options
- IA extends IB
- IA implements IB
- C extends IA
- שאר התשובות אינן נכונות

## Answer
האפשרות הנכונה היא `IA extends IB`. במודל UML, ממשק יכול להרחיב (extends) ממשק אחר. `IA` ו-`IB` שניהם ממשקים, ולכן `IA extends IB` הוא יחס ירושה חוקי בין ממשקים. `implements` משמש למחלקה המממשת ממשק, ו-`extends` משמש למחלקה היורשת ממחלקה אחרת או לממשק היורש מממשק אחר.
