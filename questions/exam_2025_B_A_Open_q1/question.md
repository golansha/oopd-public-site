---
id: exam_2025_B_A_Open_q1
title: Java Streams - Employee Ratings
year: 2025
semester: B
moed: A
type: Open
language: Hebrew
topics:
- Generic - Streams
skills:
- Programming
- Problem Solving
- Java Streams
---

## Question
חברת שירותים מקבלת דירוגים מלקוחות עבור כל אחד מהעובדים שלה. הנתונים מיוצגים במבנה הבא: `Map<String, List<Integer>> employeeRatings` כאשר: • כל מפתח הוא שם של עובד,(`String`) • כל ערך הוא רשימת הדירוגים (ערכים בין 1 ל־5) שהעובד קיבל מהלקוחות (`<List<Integer`). לדוגמה : `{"Alice" = [5, 4, 4, 5], "Bob" = [3, 2], "Charlie" = [5, 5, 5]}` כתוב פונקציה שמחזירה רשימה של שמות העובדים שהדירוג הממוצע שלהם הוא לפחות 4.5. ניתן להשתמש בפונקציות עזר. יש להשתמש ב Java Streams בלבד (אין להשתמש בלולאות או בפונקציית `ForEach`). כאן יש לענות רק על שאלה 1 (אם כתבת בטעות את פתרון שאלה 1 במקום אחר, ציין זאת כאן במפורש)

## Answer
```java
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class EmployeeRatingAnalyzer {

    public static List<String> getEmployeesWithHighAverageRating(
            Map<String, List<Integer>> employeeRatings, double minAverageRating) {

        return employeeRatings.entrySet().stream()
                .filter(entry -> {
                    List<Integer> ratings = entry.getValue();
                    if (ratings == null || ratings.isEmpty()) {
                        return false; // Skip employees with no ratings
                    }
                    double average = ratings.stream()
                            .mapToDouble(Integer::doubleValue)
                            .average()
                            .orElse(0.0); // Default to 0 if no ratings, though filtered above
                    return average >= minAverageRating;
                })
                .map(Map.Entry::getKey)
                .collect(Collectors.toList());
    }

    public static void main(String[] args) {
        Map<String, List<Integer>> employeeRatings = Map.of(
                "Alice", List.of(5, 4, 4, 5),
                "Bob", List.of(3, 2),
                "Charlie", List.of(5, 5, 5),
                "David", List.of(4, 4, 4, 4)
        );

        List<String> highRatedEmployees = getEmployeesWithHighAverageRating(employeeRatings, 4.5);
        System.out.println("Employees with average rating >= 4.5: " + highRatedEmployees);
        // Expected output: Employees with average rating >= 4.5: [Alice, Charlie]
    }
}
```
**הסבר:**
1.  הפונקציה `getEmployeesWithHighAverageRating` מקבלת מפה של דירוגי עובדים וציון ממוצע מינימלי.
2.  אנו מתחילים עם `employeeRatings.entrySet().stream()` כדי לקבל זרם של זוגות מפתח-ערך (שם עובד ורשימת דירוגים).
3.  אנו משתמשים ב-`.filter()` כדי לסנן את העובדים. בתוך הפילטר:
    *   אנו בודקים אם רשימת הדירוגים אינה ריקה כדי למנוע שגיאות חישוב ממוצע.
    *   אנו יוצרים זרם חדש מתוך רשימת הדירוגים (`ratings.stream()`).
    *   אנו ממפים את הדירוגים ל-`double` באמצעות `mapToDouble(Integer::doubleValue)`.
    *   אנו מחשבים את הממוצע באמצעות `average().orElse(0.0)`.
    *   העובד נשמר בזרם אם הממוצע שלו גדול או שווה ל-`minAverageRating`.
4.  לאחר הסינון, אנו משתמשים ב-`.map(Map.Entry::getKey)` כדי להפוך כל זוג מפתח-ערך לשם העובד בלבד.
5.  לבסוף, אנו אוספים את שמות העובדים המסוננים לרשימה באמצעות `collect(Collectors.toList())`.
