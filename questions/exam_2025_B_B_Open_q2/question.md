---
id: exam_2025_B_B_Open_q2
title: עקרונות עיצוב חבילות ותיקון תרשים
year: 2025
semester: B
moed: B
type: Open
topics:
- Package Design Principles
- Acyclic Dependencies Principle (ADP)
- Dependency Inversion Principle (DIP)
skills:
- Identifying design principle violations
- refactoring
- UML diagramming
---

## Question
(2 נקודות) איזה עיקרון בעיצוב חבילות מופר בתרשים שלפניך?
(5 נקודות) כיצד ניתן לתקן זאת ללא העברה של מחלקות מחבילה לחבילה? שרטט תרשים חדש. אין צורך לשרטט מחדש חלקים בתרשים שלא השתנו. הסבר כיצד השינוי פותר את ההפרה.
![Image](image_4_1.png)

## Answer
**חלק 1: זיהוי העיקרון המופר**
התרשים מציג תלות מחזורית בין חבילות:
*   `P1` תלוי ב-`P2` (דרך `A` -> `H`).
*   `P2` תלוי ב-`P3` (דרך `J` -> `D`).
*   `P3` תלוי ב-`P1` (דרך `D` -> `C`).
זה יוצר מחזור: `P1 -> P2 -> P3 -> P1`.
העיקרון המופר הוא **Acyclic Dependencies Principle (ADP)**, הקובע כי גרף התלויות בין חבילות או רכיבים חייב להיות חסר מחזורים.

**חלק 2: תיקון ללא העברת מחלקות ותרשים חדש**
כדי לשבור את המחזור `P1 -> P2 -> P3 -> P1` מבלי להעביר מחלקות בין חבילות, ניתן ליישם את עקרון היפוך התלויות (Dependency Inversion Principle - DIP). התלות הבעייתית היא `P3` התלוי ב-`P1` (באופן ספציפי, `D` התלוי ב-`C`). ניתן להפוך תלות זו על ידי הצגת ממשק ב-`P3` ש-`C` (או מחלקה חדשה ב-`P1` ש-`C` תלוי בה) תממש.

**שלבי התיקון:**
1.  **הגדרת ממשק ב-`P3`:** ניצור ממשק, למשל `IDependency`, בתוך חבילה `P3`. ממשק זה יצהיר על המתודות ש-`D` זקוק להן מ-`C`.
2.  **שינוי `D` ב-`P3`:** נשנה את `D` ב-`P3` כך שיתבסס על `IDependency` במקום על `C`.
3.  **מימוש הממשק ב-`P1`:** נגרום ל-`C` ב-`P1` לממש את `IDependency`.

כעת, התלויות הן:
*   `P1 -> P2` (A -> H)
*   `P2 -> P3` (J -> D)
*   `P1 -> P3` (כי `C` מממש את `IDependency` מ-`P3`)

המחזור `P1 -> P2 -> P3 -> P1` נשבר. גרף התלויות החדש הוא `P1 -> P2 -> P3` ו-`P1 -> P3`, והוא חסר מחזורים.

**תרשים מחלקות מתוקן (חלקי, מציג את השינויים):**
```mermaid
classDiagram
    direction LR
    package P1 {
        class A
        class C
    }
    package P2 {
        class H
        class J
        class K
    }
    package P3 {
        interface IDependency {
            +methodNeededByD()
        }
        class D
        class E
        class F
        class G
    }

    A --> H
    J --> D
    C ..|> IDependency : implements
    D --> IDependency

    P1 --> P2
    P2 --> P3
    P1 --> P3
```

**הסבר כיצד השינוי פותר את ההפרה:**
על ידי הצגת ממשק `IDependency` ב-`P3`, המחלקה `D` תלויה כעת בהפשטה (`IDependency`) הנמצאת בחבילה שלה (`P3`). המימוש הקונקרטי (`C`) נמצא ב-`P1` ותלוי ב-`IDependency` (מ-`P3`). זה הופך את כיוון התלות המקורי מ-`P3 -> P1` ל-`P1 -> P3`, ובכך שובר את המחזור. התלויות `P1 -> P2` ו-`P2 -> P3` נשארות כפי שהיו. גרף התלויות הכולל של החבילות הופך להיות חסר מחזורים, ובכך עומד בעיקרון ה-ADP.
