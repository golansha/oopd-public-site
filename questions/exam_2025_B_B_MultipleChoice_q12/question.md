---
id: exam_2025_B_B_MultipleChoice_q12
title: Generics - Wildcards
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Generic - Streams
skills: []
---

## Question
נתון הקוד של הפונקציה `copy` המעתיקה את האלמנטים הנמצאים ברשימה `src` לתוך הרשימה `dest`. בקוד הושמטו הטיפוסים של `src,dest`
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
This follows the PECS (Producer Extends, Consumer Super) principle. The `src` list is a producer of `T` (we `get` from it), so it should use `? extends T`. The `dest` list is a consumer of `T` (we `set` into it), so it should use `? super T`. This allows for maximum flexibility in the types that can be passed to the method.
