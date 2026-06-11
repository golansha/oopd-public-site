---
id: exam_2025_B_B_MultipleChoice_q13
title: Package Design - Release Principles
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Package design - Cohesion
- Package design - Coupling
skills: []
---

## Question
בחברת 'אפליקציות בע"מ' מתלבטים לגבי מבנה החבילות של הגרסה הבאה עבור אפליקציה פופולארית שהם מפתחים. מצד אחד, מרבית הלקוחות שלהם זקוקים רק לחלק מהפונקציונליות. מצד שני, יש סיבה אחת לשינוי שמשפיעה על כל המחלקות שבאפליקציה. אחרי התלבטויות הם החליטו לשחרר חבילה גדולה שכוללת הכול. מה נכון לפי עקרונות ניהול חבילות שלמדנו:

### Options
- קיימת הפרה של עיקרון `CRP`
- קיימת הפרה של עיקרון `CCP`
- עיקרון `CRP` ו-`CCP` מופרים
- אף עיקרון לא מופר

## Answer
The decision to release a large package containing everything, even if most clients only need a part, violates the Common Reuse Principle (CRP) because clients are forced to depend on things they don't use. The fact that one change affects all classes in the application, leading to a single large package, suggests a violation of the Common Closure Principle (CCP), which states that classes that change together should be packaged together. If a single change affects *all* classes, it implies they are not properly grouped into smaller, cohesive units.
