---
id: exam_2025_B_B_MultipleChoice_q6
title: State Diagram Error - Turtle and Hare
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- State Diagrams
- UML
- System Behavior
- Sequence Diagrams
skills:
- State Diagram Analysis
- Error Identification
- UML Interpretation
---

## Question
נתונים תרשימי המצבים עבור מקרה הבוחן 'הצב והארנב' שנלמד בכיתה.![Image](image_9_1.png)נתון קטע מתרשים הרצף שנפלה בו טעות במיקום אחד![Image](image_10_1.jpeg)איפה הטעות?

### Options
- מיקום 3
- מיקום 4
- מיקום 1
- מיקום 2

## Answer
הטעות נמצאת במיקום 3, ספציפית ב-`tm(300)` שמופיע לאחר `win()`. ברגע שמתרחשת פעולת `win()`, המירוץ מסתיים, והצב או הארנב עוברים למצב סיום. הפעלת טיימר נוסף (`tm(300)`) לאחר `win()` אינה הגיונית בהקשר של סיום המירוץ ואינה תואמת את תרשימי המצבים שבהם `win()` מוביל ישירות לפעולת `printWin()` ולמצב סיום.
