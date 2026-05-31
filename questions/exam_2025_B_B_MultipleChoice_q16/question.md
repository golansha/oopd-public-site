---
id: exam_2025_B_B_MultipleChoice_q16
title: Weather Monitoring System - HiLoDataImp Activation Sequence
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- System Architecture
- Event Handling
- Data Flow
skills:
- System Analysis
- Sequence Analysis
---

## Question
במערכת לניטור מזג האוויר שנלמדה בכיתה ישנה מחלקה HiLoDataImp המחשבת את ערך המדידה המינימלי/מקסימלי היומי של חישן בכל פעם שמתקבלת מדידה חדשה. הפעלת המופע של המחלקה תלויה ברצף של פעולות של מופעים של מחלקות אחרות. מהו סדר המחלקות (מהעקיף ביותר עד הישיר ביותר) של המחלקות המעורבות בהפעלת HiLoDatalmp. התייחס לסדר שבו נקראות הפונקציות של המחלקות.

### Options
- Nimbus1_0Clock, AlarmClock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, Temperature Sensor, TemperatureHiLo, PersistantImp
- Nimbus1_0Clock, AlarmClock, Nimbus1_0Temperature, TemperatureSensor, TemperatureHiLo, HiLoProxy
- AlarmClock, Nimbus1_0Clock, TemperatureSensor, Nimbus1_0Temperature, TemperatureHiLo, HiLoProxy

## Answer
הסדר הנכון של המחלקות, מהעקיף ביותר ועד הישיר ביותר, המעורבות בהפעלת `HiLoDataImp` (או ה-`HiLoProxy` שלה) במערכת ניטור מזג האוויר הוא כדלקמן:
1.  **Nimbus1_0Clock:** השעון הראשי של המערכת, שמספק את אות הזמן הבסיסי.
2.  **AlarmClock:** מקבל את אותות הזמן מהשעון ויוצר אירועי אזעקה במועדים מוגדרים (לדוגמה, כל דקה או שעה).
3.  **TemperatureSensor:** חיישן הטמפרטורה, שמבצע קריאה בפועל של הטמפרטורה כאשר הוא מופעל (לרוב על ידי ה-AlarmClock או רכיב אחר).
4.  **Nimbus1_0Temperature:** רכיב שמקבל את נתוני הטמפרטורה הגולמיים מהחיישן ומעבד אותם (לדוגמה, מבצע המרה או סינון).
5.  **TemperatureHiLo:** רכיב שאחראי על חישוב וניהול ערכי המינימום והמקסימום היומיים של הטמפרטורה, על בסיס הנתונים המעובדים מ-Nimbus1_0Temperature.
6.  **HiLoProxy:** פרוקסי ל-`HiLoDataImp`, שמקבל את הנתונים מ-TemperatureHiLo ומעביר אותם ל-`HiLoDataImp` בפועל, תוך כדי טיפול בפעולות נוספות כמו רישום או אבטחה. `HiLoDataImp` היא המחלקה שמבצעת את החישוב הסופי של המינימום/מקסימום.

האפשרות הראשונה מציגה את הרצף הלוגי והתקין של זרימת הנתונים והפעלת הפונקציות במערכת זו.
