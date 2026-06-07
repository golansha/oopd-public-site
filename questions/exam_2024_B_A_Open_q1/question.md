---
id: exam_2024_B_A_Open_q1
title: עיבוד נתונים עם Streams
year: 2024
semester: B
moed: A
type: Open
language: Hebrew
topics:
- Generic - Streams
- Package design - Cohesion
- Design patterns - General
skills: []
---

## Question
נתונה המחלקה `Employee` המייצגת עובד במפעל. במחלקה מוגדרת פונקציה `getSalary` המחזירה את השכר של העובד (מטיפוס `double`) וכמו כן פונקציה `getDepartment` המחזירה את שם המחלקה של העובד (מטיפוס `String`). כתוב פונקציה המקבלת רשימת עובדים לא ריקה והמחזירה את שם המחלקה שהשכר הממוצע בה הוא הגבוה ביותר. אם יש יותר ממחלקה אחת עם שכר ממוצע מקסימלי, הפונקציה תחזיר את שרשור השמות שלהן. על הפונקציה להשתמש בביטויי stream בלבד (ניתן להשתמש ביותר מביטוי אחד). אין להשתמש בלולאות או בפונקציה `forEach`.

## Answer
פתרון:
הערה: שמות המשתנים קוצרו כדי להתאים לגודל הדף. בקוד רצוי להשתמש בשמות מלאים.
הערה: הדרישה היתה לשרשר את השמות, כך שאין חובה להחזיר מחרוזת מעוצבת עם פסיקים.
```java
public static String getMaxAvgSal(List<Employee> employees){
    Map<String, Double> avgSalByDep =
        employees.stream()
                 .collect(groupingBy(Employee::getDepartment,
                                     averagingDouble(Employee::getSalary)));

    double maxAvgSal =
        avgSalByDep.values().stream()
                     .mapToDouble(Double::doubleValue)
                     .max().getAsDouble();

    return avgSalByDep.entrySet().stream()
                       .filter(entry -> entry.getValue().equals(maxAvgSal))
                       .map(Map.Entry::getKey)
                       .collect(joining(","));
}
```
גרסה מקוצרת:
```java
public static String getMaxAvgSal(List<Employee> employees){
    Map<String, Double> avgSalByDep =
        employees.stream()
                 .collect(groupingBy(Employee::getDepartment,
                                     averagingDouble(Employee::getSalary)));

    return avgSalByDep.entrySet().stream()
                       .collect(groupingBy(Map.Entry::getValue,
                                           mapping(Map.Entry::getKey, joining(", "))))
                       .entrySet().stream()
                       .max(Map.Entry.comparingByKey())
                       .map(Map.Entry::getValue)
                       .orElse("");
}
```
