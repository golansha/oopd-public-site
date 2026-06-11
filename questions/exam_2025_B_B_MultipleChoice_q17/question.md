---
id: exam_2025_B_B_MultipleChoice_q17
title: WMS - HiLoDataImp Activation Order
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- WMS - אתחול
- WMS - Proxy
- WMS - Persistence
skills: []
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה `HiLoDataImp` המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת `HiLoDatalmp`. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- `Nimbus1_0Clock`, `AlarmClock`, `TemperatureSensor`, `Nimbus1_0Temperature`, `TemperatureHiLo`, `HiLoProxy`
- `Nimbus1_0Clock`, `AlarmClock`, `Nimbus1_0Temperature`, `TemperatureSensor`, `TemperatureHiLo`, `PersistantImp`
- `Nimbus1_0Clock`, `AlarmClock`, `Nimbus1_0Temperature`, `TemperatureSensor`, `TemperatureHiLo`, `HiLoProxy`
- `AlarmClock`, `Nimbus1_0Clock`, `TemperatureSensor`, `Nimbus1_0Temperature`, `TemperatureHiLo`, `HiLoProxy`

## Answer
The correct order from the most indirect (outermost) to the most direct (innermost) component involved in activating `HiLoDataImp` in the WMS system is typically: `Nimbus1_0Clock` (the main application clock), which triggers `AlarmClock` (for scheduled events), which then interacts with `TemperatureSensor` (to get data), which might involve `Nimbus1_0Temperature` (a specific temperature reading component), then `TemperatureHiLo` (to calculate high/low), and finally `HiLoProxy` (which might delegate to `HiLoDataImp` for persistence or actual calculation). This sequence represents the flow of control from scheduling to data processing and persistence.
