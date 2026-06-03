---
id: exam_2025_B_B_MultipleChoice_q5
title: Statechart Diagram Error
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- UML - תרשים Statechart
skills:
- UML Analysis
- State Machine Diagrams
---

## Question
נתון קטע מתרשים הרצף שנפלה בו טעות במיקום אחד
![Image](image_9_1.png)
![Image](image_9_2.png)
![Image](image_10_1.png)
איפה הטעות?

### Options
- מיקום 4
- מיקום 1
- מיקום 2
- מיקום 3

## Answer
הטעות נמצאת במיקום 4. הפעולה `print(num = 2)` צריכה להיות חלק מהפעולה `isAboutToWin()` ולא פעולה נפרדת לאחר מכן. בדרך כלל, פעולות בתוך מצב או מעבר מבוצעות כחלק מהאירוע או התנאי, או כפעולת כניסה/יציאה מהמצב. הצבת `print(num = 2)` כפעולה נפרדת לאחר `isAboutToWin()` אינה תואמת את התחביר הסטנדרטי של תרשימי מצבים.
