---
id: exam_2025_B_B_MultipleChoice_q8
title: SRP Disadvantage
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
מהו אינו יתרון של יישום עיקרון האחריות היחידה (SRP) בתכנון מחלקות בתוכנה?

### Options
- הקוד נהיה יעיל יותר ודורש פחות משאבים.
- הקוד נהיה קל יותר לתחזוקה.
- הקוד נהיה קל יותר ללמידה עבור מתכנתים חדשים.
- ניתן לחלק את העבודה על המחלקות בין יותר מתכנתים במקביל.

## Answer
SRP focuses on maintainability, readability, and parallel development by ensuring each class has only one reason to change. It does not inherently make the code more efficient or require fewer resources; in fact, it might lead to more classes and potentially more overhead, though this is usually negligible compared to the benefits.
