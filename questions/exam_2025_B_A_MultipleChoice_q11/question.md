---
id: exam_2025_B_A_MultipleChoice_q11
title: Inversion of Control (IoC)
year: 2025
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- Frameworks - Dependency injection
skills:
- Software Architecture
- Framework Concepts
---

## Question
סמן את המשפט הנכון ביותר לגבי `Inversion Of Control` – היפוך שליטה :

### Options
- יש שתי תשובות אחרות נכונות
- משמעות העיקרון : במקום שהקוד שלנו יקרא לפונקציות של ספריות חיצוניות, `Framework` חיצוני קורא לקוד שלנו.
- על ידי שימוש ב `annotations` אנו מספקים ל `framework` ייוויס"י שמודיעים לו כיצד להפעיל את הקוד שלנו.
- משמעות העיקרון הוא: היפוך השליטה מהפרטים לכלל שמאחד אותם, במקום שתהליך יהיה תלוי בפרטים, הוא יהיה תלוי בהפשטה.

## Answer
היפוך שליטה (Inversion of Control - IoC) הוא עקרון עיצוב שבו זרימת השליטה של תוכנית הפוכה בהשוואה לתכנות מסורתי. במקום שהקוד שלנו יקרא לספריות או רכיבים חיצוניים, ה-Framework או ה-Container הם אלה שקוראים לקוד שלנו (באמצעות קריאות חוזרות, אירועים, או הזרקת תלויות). האפשרות השנייה, "משמעות העיקרון : במקום שהקוד שלנו יקרא לפונקציות של ספריות חיצוניות, `Framework` חיצוני קורא לקוד שלנו", מתארת באופן מדויק את מהות ה-IoC. האפשרות השלישית מתארת כיצד IoC מיושם לעיתים קרובות (לדוגמה, באמצעות Dependency Injection), אך אינה ההגדרה הבסיסית של העיקרון עצמו. האפשרות הרביעית מתארת את עקרון ה-DIP (Dependency Inversion Principle), שהוא קשור אך אינו זהה ל-IoC.
