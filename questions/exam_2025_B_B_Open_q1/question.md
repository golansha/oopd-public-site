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
- filtering
- mapping
- reducing
- collecting
- distinct
- sorting
- limiting
---

## Question
במערכת נתונה המייצגת משחק, יש מחלקה בשם `Player` שמכילה את הפונקציות הבאות: `getScore`: מחזירה את כמות הנקודות של השחקן `getName`: מחזירה את שם השחקן במהלך המשחק, בכל פעם שאחד השחקנים מקבל נקודות, נוצר מופע חדש של השחקן עם מספר הנקודות המעודכן. המופעים מתווספים לרשימה ובכל שניה מופעל תהליך שמעדכן את מספר הנקודות של כל שחקן על המסך. קצב המשחק גבוה מאד ולכן ייתכן שברשימה יהיו כמה מופעים עבור אותו השחקן ורק המופע עם המספר המקסימלי של נקודות הוא המופע המעודכן. בהנתן רשימת המופעים, `players`, כתוב פונקציה שמחזירה את רשימת שמות עשרת השחקנים (ללא כפילויות) שצברו את מירב הנקודות? אין להשתמש בפונקציות עזר. יש להשתמש ב `Java Streams` בלבד (אין להשתמש בלולאות או בפונקציית `ForEach`). `Public static getHighScoreList(List<Player> players){`

## Answer
הבעיה דורשת למצוא את עשרת השחקנים המובילים עם הניקוד הגבוה ביותר, תוך התחשבות בכך שיכולים להיות מספר אובייקטי `Player` עבור אותו שחקן, ואנו מתעניינים רק באובייקט עם הניקוד המקסימלי. יש להשתמש ב-`Java Streams` בלבד, ללא לולאות או `forEach`.

**שלבים:**
1.  **קיבוץ לפי שם שחקן:** השתמש ב-`Collectors.groupingBy` כדי לקבץ אובייקטי `Player` לפי ה-`name` שלהם.
2.  **מציאת הניקוד המקסימלי לכל שחקן:** בתוך כל קבוצה, השתמש ב-`Collectors.reducing` עם `BinaryOperator.maxBy` ו-`Comparator.comparing(Player::getScore)` כדי למצוא את אובייקט ה-`Player` עם הניקוד המקסימלי עבור אותו שם.
3.  **סינון אופציונליים ריקים:** `reducing` מחזיר `Optional<Player>`, לכן יש לסנן אופציונליים ריקים (אם כי בהקשר זה, לא סביר אם `players` אינה ריקה).
4.  **מיון לפי ניקוד (יורד):** מיין את אובייקטי ה-`Player` שהתקבלו לפי ה-`score` שלהם בסדר יורד.
5.  **הגבלה לעשרת הראשונים:** קח רק את עשרת השחקנים המובילים.
6.  **מיפוי לשמות:** חלץ את ה-`name` של כל `Player`.
7.  **איסוף לרשימה:** אסוף את השמות ל-`List<String>`.

```java
import java.util.Comparator;
import java.util.List;
import java.util.Optional;
import java.util.function.BinaryOperator;
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

public class ExamSolution {
    public static List<String> getHighScoreList(List<Player> players) {
        return players.stream()
                .collect(Collectors.groupingBy(
                        Player::getName,
                        Collectors.reducing(BinaryOperator.maxBy(Comparator.comparing(Player::getScore)))
                ))
                .values() // Get the Optional<Player> values from the map
                .stream()
                .filter(Optional::isPresent) // Filter out empty Optionals
                .map(Optional::get) // Get the Player object from the Optional
                .sorted(Comparator.comparing(Player::getScore).reversed()) // Sort by score descending
                .limit(10) // Take top 10
                .map(Player::getName) // Map to player names
                .collect(Collectors.toList()); // Collect into a List
    }
}
```
