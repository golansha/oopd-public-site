---
id: exam_2025_B_B_MultipleChoice_q17
title: Weather Station - HiLoDataImp Activation Order
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Design Patterns
- System Architecture
- Call Flow
- Weather Station Case Study
skills:
- System Analysis
- Call Stack Understanding
- Architectural Flow
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה HiLoDataImp המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת HiLoDataImp. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- Nimbus1_0Clock, AlarmClock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, PersistantImp
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, HiLoProxy
- AlarmClock, Nimbus1_0Clock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy

## Answer
הסדר ההגיוני ביותר, מהעקיף ביותר לכי ביותר, הוא: `Nimbus1_0Clock` (השעון הראשי שמפעיל את המערכת), `AlarmClock` (רכיב שמגיב לשעון ומפעיל פעולות במועדים קבועים), `TemperatureSensor` (החיישן שקורא את הנתונים), `Nimbus1_0Temperature` (מעבד ראשוני של נתוני הטמפרטורה), `TemperatureHiLo` (מעבד נתונים נוסף הקשור לחישוב גבוה/נמוך), ולבסוף `HiLoProxy` (ה-Proxy שמתווך ל-`HiLoDataImp` ומפעיל אותו). סדר זה משקף זרימה טיפוסית של נתונים ופעולות במערכת ניטור.
