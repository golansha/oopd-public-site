---
id: exam_2025_B_B_MultipleChoice_q12
title: Generics - PECS Rule
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Java Generics
- Wildcards
- PECS (Producer-Extends, Consumer-Super)
skills:
- Type Safety
- API Design
---

## Question
נתון הקוד של הפונקציה copy המעתיקה את האלמנטים הנמצאים ברשימה src לתוך הרשימה dest. בקוד הושמטו הטיפוסים של src,dest public static <T> void copy(dest, src){ for (int i=0; i<src.size(); i++) dest.set(i,src.get(i)); } מהי חתימת הפונקציה שתעבור קומפילציה ותעבוד באופן נכון?

### Options
- public static <T> void copy (List<? super T> dest, List<? extends T> src)
- public static <T> void copy (List<? extends T> dest, List<? extends T> src)
- public static <T> void copy (List<? super T> dest, List<? super T> src)
- public static <T> void copy (List<? extends T> dest, List<? super T> src)

## Answer
החתימה הנכונה היא `public static <T> void copy (List<? super T> dest, List<? extends T> src)`. זהו יישום של כלל PECS (Producer-Extends, Consumer-Super):
*   הרשימה `src` היא 'מפיקה' (Producer) של אובייקטים מטיפוס `T` (קוראים ממנה באמצעות `src.get(i)`). לכן, יש להשתמש ב-`? extends T` כדי לאפשר קריאה של `T` או תת-טיפוסים שלו.
*   הרשימה `dest` היא 'צורכת' (Consumer) של אובייקטים מטיפוס `T` (כותבים אליה באמצעות `dest.set(i, ...)`). לכן, יש להשתמש ב-`? super T` כדי לאפשר כתיבה של `T` או תת-טיפוסים שלו.
