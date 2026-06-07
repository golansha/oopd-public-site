---
id: exam_2024_B_B_MultipleChoice_q17
title: Decorator Pattern Implementation
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Design patterns - General
skills: []
---

## Question
הדיאגרמה הבאה מתארת מערכת לבנית סוכה, כאשר יש את המחלקה הבסיסית לבנית סוכה `SukkaImpl` , וישנן תוספות לסוכה הבסיסית שהן : `PaperChain`, `UshpizinPoster`, `BubbleLights`.
![Image](image_16_1.png)
?`SukkahDecorator` אשר נמצאת במחלקה `decorate(); String` מה יהיה המימוש של המתודה

### Options
- `itsSukkah.decorate()`
- `super.decorate()`
- אין לה מימוש, היא אבסטרקטית
- הפונקציה מפעילה בכל פעם פונקציה `decorate` של אחד הבנים שלה

## Answer
In the Decorator pattern, the `SukkahDecorator` class holds a reference to the `Sukkah` it decorates (its `itsSukkah` field). The `decorate()` method of the decorator should delegate the call to the `decorate()` method of its wrapped component. Therefore, the implementation should be `itsSukkah.decorate()`. This allows the decorator to add its own behavior before or after calling the wrapped component's method, or simply pass through the call.
