---
id: exam_2025_B_B_MultipleChoice_q11
title: Generics Copy Method
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Generic - Streams
skills:
- Java Generics
- Type Safety
---

## Question
נתון הקוד של הפונקציה `copy` המעתיקה את האלמנטים הנמצאים ברשימה `src` לתוך הרשימה `dest`. בקוד הושמטו הטיפוסים של `src`,`dest`
```java
public static <T> void copy(dest, src){
    for (int i=0; i<src.size(); i++)
        dest.set(i,src.get(i));
}
```
מהי חתימת הפונקציה שתעבור קומפילציה ותעבוד באופן נכון?

### Options
- `public static <T> void copy (List<? super T> dest, List<? extends T> src)`
- `public static <T> void copy (List<? extends T> dest, List<? extends T> src)`
- `public static <T> void copy (List<? super T> dest, List<? super T> src)`
- `public static <T> void copy (List<? extends T> dest, List<? super T> src)`

## Answer
החתימה הנכונה היא `public static <T> void copy (List<? super T> dest, List<? extends T> src)`. זהו יישום של עקרון PECS (Producer-`extends`, Consumer-`super`). הרשימה `src` היא 'מפיקה' (producer) של אובייקטים, ולכן אנו יכולים לקרוא ממנה אובייקטים שהם `T` או תת-טיפוס של `T` (`? extends T`). הרשימה `dest` היא 'צרכנית' (consumer) של אובייקטים, ולכן אנו יכולים להכניס אליה אובייקטים שהם `T` או על-טיפוס של `T` (`? super T`).
