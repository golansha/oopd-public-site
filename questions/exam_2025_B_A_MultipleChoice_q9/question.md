---
id: exam_2025_B_A_MultipleChoice_q9
title: Generics with Multiple Bounds
year: 2025
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- Generic - Streams
skills:
- Java Generics
- Programming
---

## Question
נניח כי עליכם לכתוב פונקציית חיפוש גנרית שעובדת רק על אובייקטים שניתנים למיון(`Comparable`) וגם ניתנים לבקרה (`Auditable`) במערכת שלנו יש את המודול הבא: ```java class Auditable { void audit ; () } ``` מהי ההצהרה הנכונה עבור פונקצית החיפוש :

### Options
- `public <T extends Auditable & Comparable<T>> void search(List<T> list, T element)`
- `public <T extends Comparable<T> & Auditable> void search(List<T> list, T element)`
- `public <T extends Comparable & Auditable> void search(List<T> list, T element)`
- `public <T extends Object & Comparable<T> & Auditable> void search(List<T> list, T element)`

## Answer
כאשר מגדירים גנריקה עם מספר גבולות (Multiple Bounds) ב-Java, יש להשתמש בתו `&`. בנוסף, אם אחד הגבולות הוא מחלקה (כמו `Auditable`) והשני הוא ממשק (כמו `Comparable`), המחלקה חייבת להופיע ראשונה ברשימת הגבולות. עם זאת, במקרה של שני ממשקים או ממשק ומחלקה, הסדר אינו משנה מבחינת קומפילציה, אך מקובל לשים את המחלקה ראשונה אם קיימת. האפשרות הנכונה היא `public <T extends Comparable<T> & Auditable> void search(List<T> list, T element)`. למרות ש-`Auditable` היא מחלקה ו-`Comparable` הוא ממשק, ב-Java ניתן לרשום את הממשק ראשון. חשוב ש-`Comparable` יהיה `Comparable<T>` כדי שההשוואה תהיה עם אותו טיפוס `T`.
