---
id: exam_2024_B_B_Open_q1
title: ממשקים ומחלקות
year: 2024
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Package design - Cohesion
- Package design - Coupling
skills: []
---

## Question
נתונים שני ממשקים `IB` `IA` ושלוש מחלקות `E D C`
כתוב לצד כל סעיף, האם הוא תקין/לא תקין. על כל תשובה נכונה תתווסף חצי נקודה (0.5+). על כל תשובה לא נכונה תרד חצי נקודה (0.5-). סעיף שלא ייענה לא ישפיע על הציון (0). לדוגמא סטודנט שיענה נכון על חמישה סעיפים, ובנוסף יענה לא נכון על שלושה סעיפים יקבל סהייכ ציון של נקודה אחת על השאלה.
1. `IA implements IB`
2. `IA extends IB`
3. `IA implements C`
4. `IA extends C`
5. `D extends IB`
6. `D implements C`
7. `C extends D`
8. `C extends D implements IA, IB`
9. `C implements IA, IB extends D`
10. `C implements IA, IB extends D, E`

## Answer
תשובה:
2, 7, 8 תקינים. השאר לא תקינים.
