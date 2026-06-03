---
id: exam_2025_B_B_MultipleChoice_q16
title: WMS HiLoDataImp Dependencies
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- WMS - Proxy
- WMS - AlarmClock
- WMS - Persistence
- WMS - Observer
skills:
- System Architecture
- Dependency Analysis
- Weather Monitoring System
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה `HiLoDataImp` המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת `HiLoDataImp`. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- Nimbus1_0Clock, AlarmClock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, PersistantImp
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, HiLoProxy
- AlarmClock, Nimbus1_0Clock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy

## Answer
הסדר הנכון של המחלקות, מהעקיף ביותר לשימוש הישיר ביותר ב-`HiLoDataImp`, משקף את זרימת הנתונים והתלויות במערכת ניטור מזג האוויר. ה-`Nimbus1_0Clock` הוא המקור לאירועי זמן. ה-`AlarmClock` מגיב לשעון ומפעיל את ה-`TemperatureSensor`. ה-`TemperatureSensor` קורא נתונים ומעדכן את ה-`Nimbus1_0Temperature`. ה-`TemperatureHiLo` הוא ה-Observer שמקבל את הנתונים מה-`Nimbus1_0Temperature` ומעדכן את ה-`HiLoDataImp` דרך ה-`HiLoProxy` (שמטפל ב-Persistence). לכן, הסדר הוא: `Nimbus1_0Clock` -> `AlarmClock` -> `TemperatureSensor` -> `Nimbus1_0Temperature` -> `TemperatureHiLo` -> `HiLoProxy` (שמכיל את `HiLoDataImp`).
