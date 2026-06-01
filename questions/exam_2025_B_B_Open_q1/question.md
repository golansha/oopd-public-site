---
id: exam_2025_B_B_Open_q1
title: פונקציה למציאת עשרת השחקנים בעלי הניקוד הגבוה ביותר
year: 2025
semester: B
moed: B
type: Open
topics:
- Java Streams
- Object-Oriented Programming
- Data Processing
skills:
- Stream API usage
- functional programming
- data aggregation
- filtering
- sorting
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם `Player` שמכילה את הפונקציות הבאות: `getScore`: מחזירה את כמות הנקודות של השחקן `getName`: מחזירה את שם השחקן במהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן. בהנתן רשימת המופעים, `players`, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות? אין להשתמש בפונקציות עזר. יש להשתמש ב `Java Streams` בלבד (אין להשתמש בלולאות או בפונקציית `ForEach`). `Public static getHighScoreList(List<Player> players){`

## Answer
הפתרון דורש שימוש ב-`Java Streams` כדי לקבץ את השחקנים לפי שמם, למצוא את הניקוד המקסימלי לכל שחקן, למיין את השחקנים לפי הניקוד בסדר יורד, להגביל לעשרת השחקנים המובילים ולבסוף לאסוף את שמותיהם לרשימה.

```java
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

// Assume Player class exists with getName() and getScore() methods
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

public class GameAnalyzer {

    public static List<String> getHighScoreList(List<Player> players) {
        return players.stream()
                // Group players by name and for each name, find the player with the max score
                .collect(Collectors.groupingBy(
                        Player::getName,
                        Collectors.collectingAndThen(
                                Collectors.maxBy(Comparator.comparingInt(Player::getScore)),
                                opt -> opt.orElse(null) // Handle case where a name might have no players (shouldn't happen with groupingBy)
                        )
                ))
                .values().stream() // Get the unique players (with max scores) from the map values
                .filter(java.util.Objects::nonNull) // Filter out any nulls if orElse(null) was hit
                .sorted(Comparator.comparingInt(Player::getScore).reversed()) // Sort by score descending
                .limit(10) // Take the top 10
                .map(Player::getName) // Map to player names
                .collect(Collectors.toList()); // Collect into a list
    }

    public static void main(String[] args) {
        List<Player> players = List.of(
                new Player("Alice", 100),
                new Player("Bob", 150),
                new Player("Alice", 120), // Alice's max score is 120
                new Player("Charlie", 80),
                new Player("Bob", 130),
                new Player("David", 200),
                new Player("Eve", 110),
                new Player("Frank", 170),
                new Player("Grace", 90),
                new Player("Heidi", 160),
                new Player("Ivan", 190),
                new Player("Judy", 140),
                new Player("Karen", 210),
                new Player("Liam", 70)
        );

        List<String> topPlayers = getHighScoreList(players);
        System.out.println("Top 10 Players by Score: " + topPlayers);
        // Expected output (order might vary for same scores, but names should be correct):
        // [Karen, David, Ivan, Frank, Heidi, Bob, Judy, Alice, Eve, Grace]
    }
}
```
