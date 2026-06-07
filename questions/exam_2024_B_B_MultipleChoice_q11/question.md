---
id: exam_2024_B_B_MultipleChoice_q11
title: ISP Impact
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- SOLID - ISP
- Package design - Cohesion
- Package design - Coupling
skills: []
---

## Question
כיצד משפיע עקרון הפרדת הממשקים (ISP) על פיתוח תוכנה?

### Options
- כל התשובות נכונות
- עקרון ISP מקדם יצירת ממשקים קטנים
- עקרון ISP מצמצם את התלויות בין מחלקות/ממשקים
- עקרון ISP מגדיל את מספר הממשקים.

## Answer
The Interface Segregation Principle (ISP) promotes creating small, client-specific interfaces rather than large, general-purpose ones. This leads to smaller interfaces and reduces dependencies between classes, as clients only depend on the methods they actually use. Therefore, it promotes creating small interfaces and reduces coupling. The option 'כל התשובות נכונות' (all answers are correct) is the best fit as ISP indeed promotes small interfaces and reduces coupling, even if it might increase the *number* of interfaces.
