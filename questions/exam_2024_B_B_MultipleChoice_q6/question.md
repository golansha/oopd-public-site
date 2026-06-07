---
id: exam_2024_B_B_MultipleChoice_q6
title: Bridge Pattern Misconceptions
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Design patterns - General
- WMS - Bridge
- SOLID - DIP
- SOLID - ISP
skills: []
---

## Question
מי מבין המשפטים הבאים אינו נכון לגבי תבנית העיצוב Bridge

### Options
- התבנית היא במהותה יישום של עיקרון ISP, כך שכל מחלקה הצורכת מידע מהחומרה תכיר רק את הפונקציות להן היא זקוקה.
- התבנית היא במהותה יישום של טכניקת Dependncy Inversion לצורך הפרדה של רובד ההפשטה מרובד המימוש.
- מימוש תבנית העיצוב בפועל יכול להיות כך : נניח ומחלקה A ירשה ממחלקה אבסטרקטית AA. נגדיר ממשק AAImp, אותו תממש המחלקה AA, והמחלקה A תכיל מצביע ל AAImp.
- מימוש תבנית העיצוב בפועל יכול להיות כך: נניח ומחלקה A ירשה ממחלקה אבסטרקטית AA, נגדיר ממשק AAImp, אותו תממש המחלקה A, והמחלקה AA תכיל מצביע ל AAImp.

## Answer
The Bridge pattern primarily implements the Dependency Inversion Principle (DIP) to decouple an abstraction from its implementation, allowing them to vary independently. It is not fundamentally an application of ISP, which focuses on client-specific interfaces.
