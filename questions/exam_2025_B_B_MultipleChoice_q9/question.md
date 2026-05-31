---
id: exam_2025_B_B_MultipleChoice_q9
title: Bridge Pattern ו-DIP
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- Bridge Pattern
- Dependency Inversion Principle (DIP)
skills:
- Pattern Application
- Principle Application
---

## Question
סמן את התשובה הנכונה ביותר

### Options
- תבנית העיצוב Bridge משמשת לפתרון בעיית DIP
- תבנית העיצוב Bridge משמשת לפתרון בעיית ISP
- תבנית העיצוב Bridge משמשת לפתרון בעיית LSP
- תבנית העיצוב Bridge משמשת לפתרון בעיית SRP

## Answer
תבנית ה-Bridge מפרידה הפשטה מהמימוש שלה, ומאפשרת לשניהם להשתנות באופן בלתי תלוי. זהו יישום ישיר של עיקרון ה-Dependency Inversion Principle (DIP), הקובע שמודולים ברמה גבוהה לא צריכים להיות תלויים במודולים ברמה נמוכה, אלא ששניהם צריכים להיות תלויים בהפשטות. ה-Bridge משיג זאת על ידי כך שגם ההפשטה וגם המימוש שלה תלויים בממשק (ממשק ה-Implementor).
