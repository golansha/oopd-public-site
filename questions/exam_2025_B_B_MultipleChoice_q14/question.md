---
id: exam_2025_B_B_MultipleChoice_q14
title: WMS Design Patterns
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- WMS - Observer
- WMS - Bridge
- UML - תרשים מחלקות
skills:
- Design Patterns
- UML Analysis
- Weather Monitoring System
---

## Question
להלן תרשים מחלקות מתוך מקרה בוחן תחנת מזג האוויר.
![Image](image_13_1.png)
מהן תבניות העיצוב שבאות לידי ביטוי בתרשים?

### Options
- Bridge-ו Observer
- Adapter-ו Observer
- Bridge- AlarmClock
- Proxy-ו Observer

## Answer
התרשים מציג שתי תבניות עיצוב עיקריות:
1.  **Observer Pattern:** המחלקה `Y` (ה-Subject) מכילה רשימה של אובייקטים מסוג `X` (ה-Observers) ומתקשרת איתם באמצעות שיטות `add`, `remove`, ו-`notifyX`. המחלקה `MonitoringScreen` היא `X` (Observer) והיא נרשמת ל-`MS_TemperatureX` (Subject) כדי לקבל עדכונים.
2.  **Bridge Pattern:** המחלקה `TemperatureSensor` (האבסטרקציה) משתמשת בממשק `X` (האימפלמנטור) כדי לבצע את פעולת ה-`update`. זה מאפשר לשנות את הדרך שבה הנתונים מעודכנים (למשל, להחליף את `X` במימוש אחר) מבלי לשנות את `TemperatureSensor`.
