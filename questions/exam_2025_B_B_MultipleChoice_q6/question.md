---
id: exam_2025_B_B_MultipleChoice_q6
title: זיהוי טעות בתרשים רצף
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- UML
- Sequence Diagrams
- Modeling Errors
skills:
- UML Interpretation
- Error Detection
---

## Question
נתון קטע מתרשים הרצף שנפלה בו טעות במיקום אחד ![Image](image_10_1.jpeg) איפה הטעות?

### Options
- מיקום 4
- מיקום 1
- מיקום 2
- מיקום 3

## Answer
הטעות נמצאת ב'מיקום 4'. בתרשים רצף, `isAboutToWin()` הוא תנאי שמירה (guard condition) או פעולה. אם הוא תנאי שמירה, הוא צריך להיות על הודעה או על פרגמנט משולב (combined fragment), ולא כפעולה עצמאית לפני פעולות אחרות כמו `print(num = 2)` או `tm(300)`. המיקום הנוכחי שלו כפעולה לפני פעולות אחרות אינו תקין מבחינת סמנטיקה של תרשימי רצף, במיוחד בהשוואה לתרשים המצבים המקורי שבו `isAboutToWin()` הוא תנאי מעבר.
