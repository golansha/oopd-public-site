---
id: exam_2025_B_B_MultipleChoice_q12
title: Generics and Wildcards for Copy Function
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- Java Generics
- Wildcards
- PECS (Producer Extends, Consumer Super)
skills:
- Java Generics application
- Compiler error prediction
---

## Question
נתון הקוד של הפונקציה copy המעתיקה את האלמנטים הנמצאים ברשימה src לתוך הרשימה dest. בקוד הושמטו הטיפוסים של src,dest```javapublic static <T> void copy(dest, src){    for (int i=0; i<src.size(); i++)        dest.set(i,src.get(i));}```מהי חתימת הפונקציה שתעבור קומפילציה ותעבוד באופן נכון?

### Options
- public static <T> void copy (List<? super T> dest, List<? extends T> src)
- public static <T> void copy (List<? extends T> dest, List<? extends T> src)
- public static <T> void copy (List<? super T> dest, List<? super T> src)
- public static <T> void copy (List<? extends T> dest, List<? super T> src)

## Answer
הפונקציה `copy` מקבלת אלמנטים מ-`src` ושמה אותם ב-`dest`. לפי עקרון PECS (Producer Extends, Consumer Super):
*   `src` הוא 'מפיק' (Producer) של אלמנטים, ולכן צריך להשתמש ב-`<? extends T>`.
*   `dest` הוא 'צרכן' (Consumer) של אלמנטים, ולכן צריך להשתמש ב-`<? super T>`.

לכן, החתימה הנכונה היא `public static <T> void copy (List<? super T> dest, List<? extends T> src)`.
