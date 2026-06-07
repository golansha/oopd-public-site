---
id: exam_2025_B_A_MultipleChoice_q4
title: Composite vs Composition
year: 2025
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- UML - תרשים מחלקות
skills:
- UML Concepts
- Object-Oriented Design
---

## Question
מה ההבדל בין מימוש קשר `Composite` למימוש קשר `Composition`?

### Options
- בקשר `Composite` יש בבנאי קוד המקשר בין המחלקות המוכלות וב-`Composition` לא.
- בקשר `Composite` יש בבנאי קוד המקשר בין המחלקה המכילה למחלקות המוכלות וב-`Composition` לא.
- אין הבדל בין `Composite` חד כיווני ל-`Composition` חד כיווני, אבל יש הבדל בין `Composite` דו כיווני ל-`Composition` דו כיווני.
- אין הבדל בין `Composite` דו כיווני ל-`Composition` דו כיווני, אבל יש הבדל בין `Composite` חד כיווני ל-`Composition` חד כיווני.

## Answer
האפשרות הראשונה מתארת הבדל שאינו נכון. `Composition` ו-`Aggregation` הם סוגים של קשרי `Association` ב-UML, כאשר `Composition` הוא קשר חזק יותר המצביע על תלות קיום (חלק לא יכול להתקיים ללא השלם). `Composite` הוא תבנית עיצוב (Design Pattern) המאפשרת לטפל באובייקטים בודדים ובקומפוזיציות של אובייקטים באופן אחיד. ההבדל המהותי הוא ש`Composition` מתייחס לקשר מבני בין אובייקטים (חלק-שלם), בעוד ש`Composite` מתייחס לתבנית עיצוב המאפשרת לבנות עצים של אובייקטים ולטפל בהם באופן אחיד. האפשרויות האחרות מבלבלות בין המושגים או מציגות הבדלים שאינם קיימים.
