---
id: exam_2024_B_B_MultipleChoice_q8
title: Observer vs AlarmClock
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Design patterns - General
- WMS - Observer
- WMS - AlarmClock
skills: []
---

## Question
אם ננסה להקביל בין תבנית ה-observer לתבנית alarmClock מה יהיה נכון להגיד?

### Options
- .Observable במחלקת `notifyObservers` מקבילה לפונקציה `AlarmClock` במחלקת `tic` הפונקציה
- .Observable במחלקת `update` מקבילה לפונקציה `alarmListener` במחלקה `wakeup` הפונקציה
- .TemperatureSensor במחלקת `check` מקבילה לפונקציה `alarmListener` במחלקת `tic` הפונקציה
- יש שתי תשובות אחרות נכונות.

## Answer
In the Observer pattern, `notifyObservers` is called by the `Observable` to inform its `Observers` of a change. In the AlarmClock system, the `tic` method of `AlarmClock` is responsible for notifying `AlarmListeners` (observers) when the alarm goes off. Therefore, `notifyObservers` in `Observable` is analogous to `tic` in `AlarmClock`.
