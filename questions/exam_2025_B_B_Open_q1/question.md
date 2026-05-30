---
id: exam_2025_B_B_Open_q1
title: High Score List with Java Streams
year: 2025
semester: B
moed: B
type: Open
topics:
- Java Streams
- Object-Oriented Programming
- Data Processing
skills:
- Problem Solving
- Java Programming
- Stream API usage
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם Player שמכילה את הפונקציות הבאות:getScore: מחזירה את כמות הנקודות של השחקןgetName: מחזירה את שם השחקןבמהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן.בהנתן רשימת המופעים, players, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות?אין להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית ForEach).Public static getHighScoreList(List<Player> players){

## Answer
```java
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.Optional;
import java.util.stream.Collectors;

// Assuming Player class exists with getName() and getScore()
class Player {
    private String name;
    private int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }

    @Override
    public String toString() {
        return "Player{" + "name='" + name + '\'' + ", score=" + score + '}';
    }
}

public class ExamQuestions {

    public static List<String> getHighScoreList(List<Player> players) {
        return players.stream()
                .collect(Collectors.groupingBy(
                        Player::getName,
                        Collectors.mapping(Player::getScore, Collectors.maxBy(Comparator.naturalOrder()))
                )) // Map<String, Optional<Integer>>: Player name -> Max score
                .entrySet().stream()
                .filter(entry -> entry.getValue().isPresent()) // Ensure there's a score
                .sorted(Map.Entry.<String, Optional<Integer>>comparingByValue(
                        Comparator.comparing(Optional::get, Comparator.reverseOrder())) // Sort by Optional<Integer> value in reverse
                )
                .limit(10)
                .map(Map.Entry::getKey) // Get the player name
                .collect(Collectors.toList());
    }
}
```
