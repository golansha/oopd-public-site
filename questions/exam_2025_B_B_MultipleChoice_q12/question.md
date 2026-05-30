---
id: exam_2025_B_B_MultipleChoice_q12
title: Generics - Copy Function Signature
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Java Generics
- Wildcards
- PECS (Producer Extends Consumer Super)
skills:
- Java Programming
- Generics Usage
- Type Safety
---

## Question
נתון הקוד של הפונקציה copy המעתיקה את האלמנטים הנמצאים ברשימה src לתוך הרשימה dest. בקוד הושמטו הטיפוסים של src,dest. מהי חתימת הפונקציה שתעבור קומפילציה ותעבוד באופן נכון?```javapublic static <T> void copy(dest, src){for (int i=0; i<src.size(); i++)dest.set(i,src.get(i));}```

### Options
- public static <T> void copy (List<? super T> dest, List<? extends T> src)
- public static <T> void copy (List<? extends T> dest, List<? extends T> src)
- public static <T> void copy (List<? super T> dest, List<? super T> src)
- public static <T> void copy (List<? extends T> dest, List<? super T> src)

## Answer
החתימה הנכונה היא `public static <T> void copy (List<? super T> dest, List<? extends T> src)`. זה תואם לעיקרון PECS (Producer Extends, Consumer Super):
*   `src` הוא 'מפיק' (Producer) – אנו קוראים ממנו (`src.get(i)`), ולכן הוא צריך להיות `List<? extends T>`. זה מאפשר לקבל רשימה של `T` או כל תת-טיפוס של `T`.
*   `dest` הוא 'צרכן' (Consumer) – אנו כותבים אליו (`dest.set(i, ...)`), ולכן הוא צריך להיות `List<? super T>`. זה מאפשר לכתוב לתוכו `T` או כל תת-טיפוס של `T`, כל עוד הרשימה יכולה להכיל סוג-על של `T`.
