---
id: exam_2025_B_B_Open_q1
title: Java Streams - High Score List
year: 2025
semester: B
moed: B
type: Open
topics:
- Java Streams
- Data Processing
- Functional Programming
- Object-Oriented Programming
skills:
- Java Programming
- Stream API usage
- Problem Solving
- Data Aggregation
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם Player שמכילה את הפונקציות הבאות:getScore: מחזירה את כמות הנקודות של השחקןgetName: מחזירה את שם השחקןבמהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן.בהנתן רשימת המופעים, players, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות?אין להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית ForEach).Public static getHighScoreList(List<Player> players){

## Answer
```javaimport java.util.List;import java.util.Comparator;import java.util.stream.Collectors;public class Player {    private String name;    private int score;    public Player(String name, int score) {        this.name = name;        this.score = score;    }    public String getName() {        return name;    }    public int getScore() {        return score;    }    // For demonstration/testing purposes    @Override    public String toString() {        return "Player{" +            "name='" + name + '\'' +            ", score=" + score +            '}';    }    public static List<String> getHighScoreList(List<Player> players) {        return players.stream()            .collect(Collectors.groupingBy(Player::getName,                Collectors.maxBy(Comparator.comparingInt(Player::getScore))))            .values().stream()            .filter(java.util.Optional::isPresent)            .map(java.util.Optional::get)            .sorted(Comparator.comparingInt(Player::getScore).reversed())            .limit(10)            .map(Player::getName)            .collect(Collectors.toList());    }}```
