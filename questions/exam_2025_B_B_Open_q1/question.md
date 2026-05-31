---
id: exam_2025_B_B_Open_q1
title: רשימת שחקנים עם ניקוד גבוה
year: 2025
semester: B
moed: B
type: Open
topics:
- Java Streams
- Data Processing
- Object-Oriented Programming
skills:
- Stream API
- Functional Programming
- Data Aggregation
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם Player שמכילה את הפונקציות הבאות: getScore: מחזירה את כמות הנקודות של השחקן getName: מחזירה את שם השחקן במהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן. בהנתן רשימת המופעים, players, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות? אין להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית ForEach).

## Answer
```java
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.Optional;
import java.util.stream.Collectors;

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
        return "Player{" +
               "name='" + name + '\'' +
               ", score=" + score +
               '}';
    }
}

public class HighScoreManager {

    public static List<String> getHighScoreList(List<Player> players) {
        return players.stream()
                .collect(Collectors.groupingBy(
                        Player::getName, // Group by player name
                        Collectors.mapping(
                                Player::getScore, // Map to scores
                                Collectors.reducing(0, Integer::max) // Find max score for each player
                        )
                ))
                .entrySet().stream() // Stream of Map.Entry<String, Integer> (playerName, maxScore)
                .sorted(Map.Entry.<String, Integer>comparingByValue(Comparator.reverseOrder())) // Sort by max score descending
                .limit(10) // Take top 10
                .map(Map.Entry::getKey) // Get player names
                .collect(Collectors.toList()); // Collect to a list
    }

    public static void main(String[] args) {
        List<Player> players = List.of(
                new Player("Alice", 100),
                new Player("Bob", 150),
                new Player("Alice", 120), // Alice's score updated
                new Player("Charlie", 80),
                new Player("Bob", 130),
                new Player("David", 200),
                new Player("Eve", 90),
                new Player("Frank", 110),
                new Player("Grace", 160),
                new Player("Heidi", 70),
                new Player("Ivan", 190),
                new Player("Judy", 140),
                new Player("Karen", 170)
        );

        List<String> highScores = getHighScoreList(players);
        System.out.println("Top 10 High Score Players: " + highScores);
        // Expected output (order might vary for same scores, but names should be correct):
        // Top 10 High Score Players: [David, Ivan, Karen, Grace, Bob, Judy, Alice, Frank, Eve, Charlie]
    }
}
```

**Explanation:**
1.  **`players.stream()`**: Start a stream from the input list of `Player` objects.
2.  **`collect(Collectors.groupingBy(Player::getName, ...))`**: Group the players by their name. For each group (each unique player name), we need to find their maximum score.
3.  **`Collectors.mapping(Player::getScore, Collectors.reducing(0, Integer::max))`**: This is the downstream collector for `groupingBy`. It first maps each `Player` object in a group to its `score` (using `Player::getScore`). Then, for these scores, it uses `Collectors.reducing(0, Integer::max)` to find the maximum score. `0` is the identity for `Integer::max` (assuming scores are non-negative).
    *   The result of this step is a `Map<String, Integer>` where the key is the player's name and the value is their highest score.
4.  **`.entrySet().stream()`**: Convert the map into a stream of `Map.Entry<String, Integer>` objects so we can sort them.
5.  **`.sorted(Map.Entry.<String, Integer>comparingByValue(Comparator.reverseOrder()))`**: Sort these entries based on their score (value) in descending order. `Comparator.reverseOrder()` ensures the highest scores come first.
6.  **`.limit(10)`**: Take only the top 10 entries after sorting.
7.  **`.map(Map.Entry::getKey)`**: From the top 10 entries, extract only the player names (the keys).
8.  **`.collect(Collectors.toList())`**: Collect the resulting player names into a `List<String>`.
