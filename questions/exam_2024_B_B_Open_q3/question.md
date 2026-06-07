---
id: exam_2024_B_B_Open_q3
title: Generic Intersect Sets
year: 2024
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Generic - Streams
- Package design - Cohesion
skills: []
---

## Question
כתוב פונקציה גנרית המקבלת שתי קבוצות קלט `set2` `set1` וקבוצת פלט `output`. הפונקציה תוסיף לקבוצת הפלט את כל האיברים שנמצאים בשתי קבוצות הקלט (חיתוך הקבוצות). אין להשתמש ב `Casting` או ב `instanceOf`. על הפונקציה לתמוך בהפעלה עם קבוצות מטיפוסים שונים שמתקיים עבורם תנאי מסויים.
לדוגמא הקוד הבא יעבור קומפילציה עבור טיפוסים מתאימים `A B C`
```java
Set<A> aSet = new HashSet<>();
Set<B> bSet = new HashSet<>();
Set<C> cSet = new HashSet<>();

intersect(a, b, c)
intersect(b, a, c)
```
מה צריך להתקיים עבור הטיפוסים `A,B,C` על מנת שהפונקציה תעבור קומפילציה?
השלם את טיפוסי הפרמטרים ואת הקוד של הפונקציה כאן (ניתן להשתמש בפונקציה `Set contains` המקבלת איבר ומחזירה `true` אם הוא שייך לקבוצה):
```java
public static <T> void intersect(
 set1,
 set2,
 output) {
}
```

## Answer
תשובה :
`A` ו `B` צריכים לרשת מ `C`
תשובה :
```java
public static <T> void intersect(Set<? extends T> set1,
 Set<? extends T> set2,
 Set<? super T> set3){
 for (T t: set1) {
 if (set2.contains(t)) {
 set3.add(t);
 }
 }
}
```
