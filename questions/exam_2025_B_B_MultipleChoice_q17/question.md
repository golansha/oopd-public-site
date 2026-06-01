---
id: exam_2025_B_B_MultipleChoice_q17
title: סדר מחלקות במערכת ניטור מזג אוויר
year: 2025
semester: B
moed: B
type: Multiple Choice
topics: []
skills: []
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה `HiLoDataImp` המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת `HiLoDataImp`. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- `Nimbus1_0Clock`, `AlarmClock`, `TemperatureSensor`, `Nimbus1_0Temperature`, `TemperatureHiLo`, `HiLoProxy`
- `Nimbus1_0Clock`, `AlarmClock`, `Nimbus1_0Temperature`, `TemperatureSensor`, `TemperatureHiLo`, `PersistantImp`
- `Nimbus1_0Clock`, `AlarmClock`, `Nimbus1_0Temperature`, `TemperatureSensor`, `TemperatureHiLo`, `HiLoProxy`
- `AlarmClock`, `Nimbus1_0Clock`, `TemperatureSensor`, `Nimbus1_0Temperature`, `TemperatureHiLo`, `HiLoProxy`

## Answer
הסדר הנכון של המחלקות, מהעקיף ביותר (הגורם הראשוני) ועד הישיר ביותר (האובייקט המושפע ישירות), בהפעלת `HiLoDataImp` במערכת ניטור מזג האוויר הוא:
1.  `Nimbus1_0Clock`: השעון הראשי שמפעיל את המערכת.
2.  `AlarmClock`: מקבל התראות מהשעון ומפעיל פעולות בזמנים קבועים.
3.  `TemperatureSensor`: החיישן שמודד את הטמפרטורה.
4.  `Nimbus1_0Temperature`: אובייקט שמייצג את קריאת הטמפרטורה הספציפית מהחיישן.
5.  `TemperatureHiLo`: מחשב את ערכי המינימום והמקסימום של הטמפרטורה.
6.  `HiLoProxy`: פרוקסי ל-`HiLoDataImp` שמטפל בגישה לנתוני המינימום/מקסימום.
האפשרות הראשונה (והשלישית, שהיא כנראה כפולה בטעות במקור) משקפת את השרשרת הלוגית של הפעלת הפונקציות במערכת.
