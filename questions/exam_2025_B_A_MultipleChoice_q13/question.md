---
id: exam_2025_B_A_MultipleChoice_q13
title: Design Patterns Identification
year: 2025
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- WMS - Observer
- WMS - Bridge
- Design patterns - General
skills:
- UML Analysis
- Design Patterns Identification
---

## Question
נתון התרשים הבא מתוך תרשימי "מערכת ניטור מזג האוויר"י : ![Image](image_12_1.png) ![Image](image_12_2.png) מהן תבניות העיצוב שבאות לידי ביטוי בתרשים?

### Options
- `Bridge`-ו `Observer`
- `Adapter`-ו `Bridge`
- `Bridge`-ו `Proxy`
- `Proxy`-ו `Observer`

## Answer
התרשים מציג שתי תבניות עיצוב עיקריות:
1.  **Observer Pattern:** המחלקה `ClockListener` (ממשק) והמחלקות המממשות אותה (`ClockImp`, `AlarmClock`) יחד עם המחלקה `Nimbus1_0Clock` (ה-Subject) המכילה רשימה של `ClockListener`ים ומודיעה להם על שינויים (`notifyClockListener()`). זהו יישום קלאסי של תבנית Observer, כאשר `Nimbus1_0Clock` הוא ה-Subject ו-`ClockListener` הוא ה-Observer.
2.  **Bridge Pattern:** תבנית Bridge מפרידה בין הפשטה למימוש שלה, כך שניתן לשנות אותם באופן בלתי תלוי. בתרשים, `AlarmClock` הוא חלק מההפשטה (הוא משתמש ב-`ClockListener` כדי להודיע), ו-`ClockImp` הוא מימוש ספציפי של `ClockListener`. `Nimbus1_0Clock` הוא ה-Abstraction, ו-`ClockListener` הוא ה-Implementor. זהו יישום של Bridge, המאפשר ל-`Nimbus1_0Clock` לעבוד עם כל מימוש של `ClockListener`.

לכן, התבניות הבולטות הן `Bridge` ו-`Observer`.
