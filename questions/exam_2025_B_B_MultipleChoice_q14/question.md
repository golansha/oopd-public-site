---
id: exam_2025_B_B_MultipleChoice_q14
title: Design Patterns in Weather Monitoring System
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- Observer Pattern
- Adapter Pattern
- UML Diagrams
skills:
- Pattern Identification
- UML Interpretation
---

## Question
להלן תרשים מחלקות מתוך מקרה בוחן תחנת מזג האוויר. ![Image](image_13_1.png) מהן תבניות העיצוב שבאות לידי ביטוי בתרשים?

### Options
- Adapter-ו Observer
- Bridge-ו Observer
- Bridge- AlarmClock
- Proxy-ו Observer

## Answer
בתרשים באות לידי ביטוי שתי תבניות עיצוב:
1.  **Observer Pattern:** ממשק `X` עם מתודת `update(data:int)` מייצג את ה-Observer. המחלקות `MonitoringScreen` ו-`MS_TemperatureX` מממשות את `X` (או `MS_TemperatureX` מממשת `X` ומשתמשת ב-`MonitoringScreen`). המחלקה `Y` היא ה-Subject, עם מתודות `add(x:X)`, `removeX(x:X)` ו-`notifyX(data:int)`, המאפשרות להרשמה, הסרה ועדכון של אובייקטי `X`.
2.  **Adapter Pattern:** המחלקה `MS_TemperatureX` פועלת כ-Adapter. היא מממשת את ממשק `X` (ה-Target) ומקבלת בבנאי שלה אובייקט `MonitoringScreen` (ה-Adaptee). כאשר נקראת מתודת `update` על `MS_TemperatureX`, היא מתרגמת את הקריאה למתודה `displayTemperature` של אובייקט `MonitoringScreen` הפנימי. בכך, היא מאפשרת לאובייקט `MonitoringScreen` (שאינו תואם ישירות לממשק `X`) להשתלב במנגנון ה-Observer.
