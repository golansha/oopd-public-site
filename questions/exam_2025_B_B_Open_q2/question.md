---
id: exam_2025_B_B_Open_q2
title: Package Design Principle Violation
year: 2025
semester: B
moed: B
type: Open
topics:
- UML - תרשים מחלקות
- Package design - Coupling
- SOLID - DIP
skills:
- UML Analysis
- Package Design Principles
- Refactoring
---

## Question
(2 נקודות) איזה עיקרון בעיצוב חבילות מופר בתרשים שלפניך?
(5 נקודות) כיצד ניתן לתקן זאת ללא העברה של מחלקות מחבילה לחבילה? שרטט תרשים חדש. אין צורך לשרטט מחדש חלקים בתרשים שלא השתנו. הסבר כיצד השינוי פותר את ההפרה.
![Image](image_4_1.png)

## Answer
**א. העיקרון המופר:**
עיקרון ה-Acyclic Dependencies Principle (ADP) מופר. עיקרון זה קובע כי גרף התלויות בין חבילות צריך להיות חסר מעגלים (DAG). בתרשים, יש תלות מעגלית בין חבילות P1, P2 ו-P3:
P1 -> P2 (דרך A->H)
P2 -> P3 (דרך J->D)
P3 -> P1 (דרך D->C)

**ב. תיקון התרשים:**
כדי לתקן את ההפרה ללא העברת מחלקות, ניתן להשתמש בעקרון ה-Dependency Inversion Principle (DIP). נהפוך את התלות מ-P3 ל-P1 על ידי יצירת ממשק בחבילה P1, ו-P3 תהיה תלויה בממשק זה במקום ישירות במחלקה C מ-P1.

**שלבי התיקון:**
1.  **יצירת ממשק:** בחבילה P1, ניצור ממשק חדש, לדוגמה `IP1Service`.
2.  **הטמעת הממשק:** מחלקה `C` בחבילה P1 תטמיע את הממשק `IP1Service`.
3.  **היפוך תלות:** מחלקה `D` בחבילה P3 תהיה תלויה בממשק `IP1Service` (שנמצא ב-P1) במקום ישירות במחלקה `C`.

**תרשים מתוקן (השינויים מסומנים):**

```mermaid
classDiagram
    direction LR

    package P1 {
        class A
        class B
        interface IP1Service
        class C {
            <<implements>>
        }
        C ..|> IP1Service
        A --> H
    }

    package P2 {
        class H
        class I
        class J
        class K
        H --> I
        H --> J
        J --> D
    }

    package P3 {
        class D
        class E
        class F
        class G
        D --> IP1Service
        D --> E
        F --> G
    }

    P1 <.. P2 : uses
    P2 <.. P3 : uses
    P3 <.. P1 : uses (via interface)

    A -- B
    C -- B
    H -- I
    H -- J
    J -- K
    D -- E
    F -- G

```

**הסבר כיצד השינוי פותר את ההפרה:**
התיקון שובר את התלות המעגלית. במקום ש-P3 תהיה תלויה ישירות ב-P1 (דרך D->C), P3 תלויה כעת בממשק `IP1Service` שנמצא גם הוא ב-P1. מכיוון שממשקים הם בדרך כלל יציבים יותר ואינם משתנים בתדירות גבוהה כמו מימושים, זה יוצר תלות בכיוון אחד (P3 תלויה ב-P1 דרך הממשק, אך P1 אינה תלויה ב-P3). בכך, גרף התלויות הופך ל-DAG, וה-ADP נשמר.
