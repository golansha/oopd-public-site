---
id: exam_2025_B_B_MultipleChoice_q16
title: Template Method Implementation
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- WMS - Template method
- Design patterns - General
skills: []
---

## Question
כיצד יש לממש את תבנית העיצוב `template method`?

### Options
- ליצור מימושים שונים במחלקות היורשות לפונקציה מופשטת שנקראת מתוך פונקציה במחלקת הבסיס.
- לתאם בין מחלקות נתונות לממשק שהגדרנו ושאין לשנותו.
- להגדיר במחלקות היורשות פונקציות שקוראות לפונקציה מופשטת של מחלקת הבסיס.
- ליצור פונקציה במחלקות היורשות, שהמימוש שלה יופיע במחלקת הבסיס.

## Answer
The Template Method pattern defines the skeleton of an algorithm in a superclass but lets subclasses override specific steps of the algorithm without changing its structure. This is achieved by having a template method (often final) in the superclass that calls abstract or hook methods, which are then implemented by subclasses.
