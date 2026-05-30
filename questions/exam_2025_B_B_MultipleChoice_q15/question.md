---
id: exam_2025_B_B_MultipleChoice_q15
title: Weather Station Design Patterns
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- Observer Pattern
- Adapter Pattern
- UML
skills:
- Design Pattern Identification
- UML Analysis
---

## Question
להלן תרשים מחלקות מתוך מקרה בוחן תחנת מזג האוויר.![Image](image_13_1.png)מהן תבניות העיצוב שבאות לידי ביטוי בתרשים?

### Options
- Adapter-ו Observer
- Bridge-ו Observer
- Bridge-ו AlarmClock
- Proxy-ו Observer

## Answer
התרשים מציג שתי תבניות עיצוב עיקריות:
1.  **Observer Pattern:** המחלקה `Y` היא ה-Subject (נושא) עם מתודות `add(x:X)`, `notifyX(data:int)`, `removeX(x:X)`. הממשק `X` עם המתודה `update(data:int)` הוא ה-Observer (צופה). `MonitoringScreen` ו-`MS_TemperatureX` הם מימושים או משתמשים ב-`X` כ-Observer.
2.  **Adapter Pattern:** המחלקה `MS_TemperatureX` מקבלת בבנאי שלה `MonitoringScreen` ויש לה מתודת `update(data:int)`. נראה שהיא מתאימה את הממשק של `MonitoringScreen` (שמציג נתונים) לממשק `X` (שמצפה למתודת `update`). כלומר, `MS_TemperatureX` משמשת כמתאם (Adapter) כדי ש-`MonitoringScreen` יוכל לתפקד כ-Observer.

לכן, התשובה הנכונה היא Adapter-ו Observer.
