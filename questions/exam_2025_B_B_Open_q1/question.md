---
id: exam_2025_B_B_Open_q1
title: High Score List
year: 2025
semester: B
moed: B
type: Open
topics:
- Generic - Streams
skills:
- Java Streams
- Data Processing
- Object-Oriented Programming
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם `Player` שמכילה את הפונקציות הבאות:
`getScore`: מחזירה את כמות הנקודות של השחקן
`getName`: מחזירה את שם השחקן
במהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן.
בהנתן רשימת המופעים, `players`, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות?
אין להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית `ForEach`).

`Public static getHighScoreList(List<Player> players){`

## Answer
```java
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class Player {
    private String name;
    private int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public int getScore() {
        return score;
    }

    public String getName() {
        return name;
    }

    public static List<String> getHighScoreList(List<Player> players) {
        return players.stream()
                .collect(Collectors.groupingBy(
                        Player::getName,
                        Collectors.collectingAndThen(
                                Collectors.maxBy(Comparator.comparingInt(Player::getScore)),
                                opt -> opt.map(Player::getScore).orElse(0)
                        )
                ))
                .entrySet().stream()
                .sorted(Map.Entry.<String, Integer>comparingByValue(Comparator.reverseOrder()))
                .limit(10)
                .map(Map.Entry::getKey)
                .collect(Collectors.toList());
    }
}
```

**Explanation:**
1.  `players.stream()`: Creates a stream from the input list of `Player` objects.
2.  `collect(Collectors.groupingBy(Player::getName, ...))`: Groups players by their name. For each group (each unique player name), it applies a downstream collector.
3.  `Collectors.collectingAndThen(Collectors.maxBy(Comparator.comparingInt(Player::getScore)), opt -> opt.map(Player::getScore).orElse(0))`: This is the downstream collector. It first finds the `Player` object with the maximum score for each name using `maxBy` and `comparingInt(Player::getScore)`. Then, `collectingAndThen` extracts the score from the optional `Player` (or 0 if no player is found, though in this context, there will always be at least one).
    This results in a `Map<String, Integer>` where the key is the player's name and the value is their highest score.
4.  `.entrySet().stream()`: Converts the map into a stream of `Map.Entry` objects.
5.  `.sorted(Map.Entry.<String, Integer>comparingByValue(Comparator.reverseOrder()))`: Sorts the entries by their score (value) in descending order.
6.  `.limit(10)`: Takes only the top 10 entries.
7.  `.map(Map.Entry::getKey)`: Extracts the player's name (key) from each of the top 10 entries.
8.  `.collect(Collectors.toList())`: Collects the names into a `List<String>`.
