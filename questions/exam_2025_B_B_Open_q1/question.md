---
id: exam_2025_B_B_Open_q1
title: Java Streams - High Score List
year: 2025
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Generic - Streams
skills: []
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם `Player` שמכילה את הפונקציות הבאות:
* `getScore`: מחזירה את כמות הנקודות של השחקן
* `getName`: מחזירה את שם השחקן

במהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן.

בהנתן רשימת המופעים, `players`, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות?
אין להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית `ForEach`).

כאן יש לענות רק על שאלה 1 (אם כתבת בטעות את פתרון שאלה 1 במקום אחר, ציין זאת כאן במפורש)

## Answer
פתרון:
```java
public static List<String> getHighScoreList(List<Player> players){
    return players.stream()
        .sorted(Comparator.comparing(Player::getScore).reversed())
        .map(Player::getName)
        .distinct()
        .limit(10)
        .collect(Collectors.toList());
}
```
