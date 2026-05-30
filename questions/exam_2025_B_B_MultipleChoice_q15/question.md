---
id: exam_2025_B_B_MultipleChoice_q15
title: Design Patterns in Weather Station Diagram
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- Observer Pattern
- Adapter Pattern
skills:
- UML interpretation
- Design Pattern identification
---

## Question
להלן תרשים מחלקות מתוך מקרה בוחן תחנת מזג האוויר. ![Image](image_13_1.png) מהן תבניות העיצוב שבאות לידי ביטוי בתרשים?

### Options
- Adapter-ו Observer
- Bridge-ו Observer
- Bridge-ו AlarmClock
- Proxy-ו Observer

## Answer
התרשים מציג שתי תבניות עיצוב עיקריות:
1.  **Observer Pattern (תבנית המתבונן):** המחלקה `Y` (שהיא כנראה ה-Subject/Observable) מנהלת רשימה של אובייקטים מסוג `X` (ה-Observer interface) ויש לה מתודות `add`, `remove`, ו-`notifyX`. המחלקות `MonitoringScreen` ו-`MS_TemperatureX` הן מתבוננים (Observers) שמקבלים עדכונים באמצעות מתודת `update`.
2.  **Adapter Pattern (תבנית המתאם):** המחלקה `MS_TemperatureX` מקבלת בבנאי שלה אובייקט מסוג `MonitoringScreen` ומממשת את הממשק `X`. מתודת ה-`update` שלה ככל הנראה מתרגמת את הקריאה למתודות המתאימות ב-`MonitoringScreen` (כמו `displayTemperature` או `displayPressure`). זהו תפקיד קלאסי של מתאם, המאפשר למחלקה בעלת ממשק שונה (MonitoringScreen) לעבוד עם ממשק קיים (X).
