---
id: exam_2025_B_B_MultipleChoice_q12
title: חתימת פונקציית `copy` עם Generics
year: 2025
semester: B
moed: B
type: Multiple Choice
topics: []
skills: []
---

## Question
נתון הקוד של הפונקציה `copy` המעתיקה את האלמנטים הנמצאים ברשימה `src` לתוך הרשימה `dest`. בקוד הושמטו הטיפוסים של `src`,`dest`
`public static <T> void copy(dest, src){ for (int i=0; i<src.size(); i++) dest.set(i,src.get(i)); }`
מהי חתימת הפונקציה שתעבור קומפילציה ותעבוד באופן נכון?

### Options
- `public static <T> void copy (List<? super T> dest, List<? extends T> src)`
- `public static <T> void copy (List<? extends T> dest, List<? extends T> src)`
- `public static <T> void copy (List<? super T> dest, List<? super T> src)`
- `public static <T> void copy (List<? extends T> dest, List<? super T> src)`

## Answer
עבור פונקציית `copy` שמעתיקה אלמנטים מ-`src` ל-`dest`, יש להשתמש ב-`PECS` (Producer Extends, Consumer Super). `src` היא 'מפיקה' (Producer) של אלמנטים, ולכן צריכה להיות `List<? extends T>`. `dest` היא 'צורכת' (Consumer) של אלמנטים, ולכן צריכה להיות `List<? super T>`. החתימה הנכונה היא `public static <T> void copy (List<? super T> dest, List<? extends T> src)`.
