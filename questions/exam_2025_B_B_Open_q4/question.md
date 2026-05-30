---
id: exam_2025_B_B_Open_q4
title: Exam Management System - Data Structure Flexibility (Iterator/Composite Pattern)
year: 2025
semester: B
moed: B
type: Open
topics:
- Design Patterns
- Iterator Pattern
- Composite Pattern
- Data Structures
- Polymorphism
- Dependency Inversion Principle
skills:
- Design Pattern Application
- UML Diagramming
- Code Structure
- Java Collections
---

## Question
במכללה מסוימת, המשתמשת במערכת הנייל, רוצים מדי פעם לשמור מופעי בחינות במבנה נתונים. אחד השימושים האפשריים במבני הנתונים הוא למשל לשמור את כל מופעי הבחינות שהתקיימו בסמסטר מסוים במחלקת מחשבים.נתונות הדרישות הבאות :הקליינט יוכל להוסיף בחינות למבנה הנתונים.לא להיות מוגבלים למבנה נתונים ספציפי. דהיינו, יהיה ניתן להחליף את מבנה הנתונים בלי שיהיה צורך לשנות את הקוד של הקליינט שניגש לנתונים.הקליינט יוכל לעבור על כל מופעי הבחינות, בלי להיות תלוי כלל במבנה הנתונים הספציפי שבו השתמשו.הניחו כי למחלקה Exam יש פונקציה מופשטת check. נרצה שהקוד הבא יעבוד בצורה תקינה :public void checkAllExams(ExamContainer examContainer){for (Exam exam: examContainer){exam.check();}}יש לתכנן את המחלקה ExamContainer כך שמבנה הנתונים הפנימי שלה יהיה ניתן להחלפה ללא צורך לקמפל מחדש את הקוד שלה. ניתן להשתמש במחלקות המוגדרות באופן מובנה בשפת Java.השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. ממש פונקציה ראשית שבה מאתחלים מופע של ExamContainer המתבסס על רשימה מקושרת (LinkedList) ומוסיפים למבנה הנתונים שלושה מופעים של בחינה (מסוגים לבחירתך).

## Answer
תבניות העיצוב המתאימות ביותר לדרישות אלו הן **Iterator Pattern** ו-**Adapter Pattern** (עבור התאמת מבני נתונים קיימים).

**הסבר:**
*   **Iterator Pattern:** הדרישה שהקליינט יוכל לעבור על כל מופעי הבחינות מבלי להיות תלוי במבנה הנתונים הפנימי מצביעה ישירות על תבנית ה-Iterator. ה-`ExamContainer` צריך לממש את ממשק `Iterable` של Java, מה שיאפשר ללקוח להשתמש בלולאת `for-each` (כפי שמוצג בדוגמת הקוד `checkAllExams`).
*   **Adapter Pattern:** הדרישה שניתן יהיה להחליף את מבנה הנתונים הפנימי (למשל, מ-`LinkedList` ל-`ArrayList` או אחר) מבלי לשנות את קוד הלקוח, מצביעה על כך ש-`ExamContainer` צריך להוות מעין מתאם (Adapter) בין מבנה הנתונים הפנימי לבין הממשק הציבורי שלו (שכולל את `Iterable` ואת שיטת ההוספה).

**תרשים מחלקות (UML Conceptual Diagram):**
```mermaid
classDiagram
    direction LR

    class Exam {
        <<abstract>>
        +check()
    }

    class OpenExam {
        +check()
    }

    class MixedExam {
        +check()
    }

    class ScrambledExam {
        +check()
    }

    interface Iterable<Exam> {
        +iterator():Iterator<Exam>
    }

    interface Collection<Exam> {
        +add(exam:Exam)
        // ... other collection methods
    }

    class ExamContainer {
        -exams:List<Exam>
        +add(exam:Exam)
        +iterator():Iterator<Exam>
    }

    Exam <|-- OpenExam
    Exam <|-- MixedExam
    Exam <|-- ScrambledExam

    Iterable <|.. ExamContainer
    Collection <|.. ExamContainer
    ExamContainer o-- "1" List<Exam> : contains

    note for ExamContainer "Implements Iterable and Collection interfaces to provide a unified interface for clients, adapting the internal List." 
```

**קוד עבור המחלקות (מבנה בלבד):**

```java
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

// Assume Exam class and its subtypes (OpenExam, MixedExam, ScrambledExam) are defined as follows:
abstract class Exam {
    private String id;

    public Exam(String id) {
        this.id = id;
    }

    public String getId() {
        return id;
    }

    public abstract void check(); // Abstract method as per question

    @Override
    public String toString() {
        return "Exam(" + id + ")";
    }
}

class OpenExam extends Exam {
    public OpenExam(String id) { super(id); }
    @Override
    public void check() {
        System.out.println("Checking Open Exam: " + getId());
    }
}

class MixedExam extends Exam {
    public MixedExam(String id) { super(id); }
    @Override
    public void check() {
        System.out.println("Checking Mixed Exam: " + getId());
    }
    // ... other MixedExam specific methods
}

class ScrambledExam extends Exam {
    public ScrambledExam(String id) { super(id); }
    @Override
    public void check() {
        System.out.println("Checking Scrambled Exam: " + getId());
    }
    // ... other ScrambledExam specific methods
}

// ExamContainer class implementing Iterable and acting as an Adapter
class ExamContainer implements Iterable<Exam> {
    private List<Exam> exams; // The internal data structure

    // Constructor allows injecting different List implementations
    public ExamContainer(List<Exam> initialExams) {
        this.exams = initialExams;
    }

    // Method to add exams (part of the client requirements)
    public void add(Exam exam) {
        exams.add(exam);
    }

    // Implementation of the Iterable interface
    @Override
    public Iterator<Exam> iterator() {
        return exams.iterator();
    }
}

public class Main {

    // The client code provided in the question
    public static void checkAllExams(ExamContainer examContainer) {
        for (Exam exam : examContainer) {
            exam.check();
        }
    }

    public static void main(String[] args) {
        // Initialize ExamContainer with a LinkedList (as requested)
        List<Exam> linkedListForExams = new LinkedList<>();
        ExamContainer container = new ExamContainer(linkedListForExams);

        // Add three exam instances of different types
        container.add(new OpenExam("OE001"));
        container.add(new MixedExam("ME002"));
        container.add(new ScrambledExam("SE003"));

        System.out.println("--- Checking all exams ---");
        checkAllExams(container);

        // Demonstrate flexibility: if we wanted to use ArrayList, we'd just change the initialization:
        // List<Exam> arrayListForExams = new ArrayList<>();
        // ExamContainer anotherContainer = new ExamContainer(arrayListForExams);
        // The client code (checkAllExams) would remain unchanged.
    }
}
```
