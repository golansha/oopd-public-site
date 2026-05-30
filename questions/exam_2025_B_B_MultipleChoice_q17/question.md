---
id: exam_2025_B_B_MultipleChoice_q17
title: Order of Operations in Weather Station (HiLoDataImp)
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- System Architecture
- Call Stack
- Weather Station Example
skills:
- System understanding
- Call flow analysis
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה HiLoDataImp המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת HiLoDataImp. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, HiLoProxy
- Nimbus1_0Clock, AlarmClock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, PersistantImp
- AlarmClock, Nimbus1_0Clock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy

## Answer
הסדר ההגיוני ביותר של קריאת פונקציות, מהגורם העקיף ביותר ועד לגורם הישיר ביותר המפעיל את `HiLoDataImp` (או את `TemperatureHiLo` המשתמש בה), הוא כדלקמן:
1.  **Nimbus1_0Clock:** השעון הראשי שמפעיל את מחזור המדידות.
2.  **AlarmClock:** רכיב שמשתמש בשעון כדי לתזמן ולהפעיל אירועים ספציפיים, כמו קריאת טמפרטורה.
3.  **Nimbus1_0Temperature:** רכיב ספציפי שאחראי על קריאת טמפרטורה עבור מערכת Nimbus 1.0. רכיב זה יתחיל את הקריאה מהחיישן.
4.  **TemperatureSensor:** החיישן הפיזי/דרייבר שמספק את נתוני הטמפרטורה הגולמיים. `Nimbus1_0Temperature` יקרא לו.
5.  **TemperatureHiLo:** הרכיב שמקבל את נתוני הטמפרטורה ומחשב את המינימום/מקסימום היומי. זהו הרכיב שבו `HiLoDataImp` תופעל או תהיה חלק ממנו.
6.  **HiLoProxy:** פרוקסי שעוטף את `TemperatureHiLo` (לדוגמה, לצורך רישום, שמירה במטמון או גישה מרחוק) או פרוקסי שאחראי על פלט/אחסון הנתונים של `TemperatureHiLo` לאחר העיבוד. אם הוא עוטף את `TemperatureHiLo`, הוא יקרא לו. אם הוא מקבל את הפלט, הוא יהיה השלב האחרון בשרשרת.

בהתאם לאפשרויות, הסדר `Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, HiLoProxy` הוא המתאים ביותר.
