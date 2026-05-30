---
id: exam_2025_B_B_Open_q4
title: Exam Container Design with Strategy and Iterator
year: 2025
semester: B
moed: B
type: Open
topics:
- Design Patterns
- Object-Oriented Design
- Strategy Pattern
- Iterator Pattern
skills:
- Design Pattern Application
- UML Diagramming
- Java Programming
---

## Question
במכללה מסוימת, המשתמשת במערכת הנייל, רוצים מדי פעם לשמור מופעי בחינות במבנה נתונים. אחד השימושים האפשריים במבני הנתונים הוא למשל לשמור את כל מופעי הבחינות שהתקיימו בסמסטר מסוים במחלקת מחשבים.נתונות הדרישות הבאות :הקליינט יוכל להוסיף בחינות למבנה הנתונים.לא להיות מוגבלים למבנה נתונים ספציפי. דהיינו, יהיה ניתן להחליף את מבנה הנתונים בלי שיהיה צורך לשנות את הקוד של הקליינט שניגש לנתונים.הקליינט יוכל לעבור על כל מופעי הבחינות, בלי להיות תלוי כלל במבנה הנתונים הספציפי שבו השתמשו.הניחו כי למחלקה Exam יש פונקציה מופשטת check. נרצה שהקוד הבא יעבוד בצורה תקינה :```javapublic void checkAllExams(ExamContainer examContainer){    for (Exam exam: examContainer){        exam.check();    }}```יש לתכנן את המחלקה ExamContainer כך שמבנה הנתונים הפנימי שלה יהיה ניתן להחלפה ללא צורך לקמפל מחדש את הקוד שלה. ניתן להשתמש במחלקות המוגדרות באופן מובנה בשפת Java.השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות.צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. ממש פונקציה ראשית שבה מאתחלים מופע של ExamContainer המתבסס על רשימה מקושרת (LinkedList) ומוסיפים למבנה הנתונים שלושה מופעים של בחינה (מסוגים לבחירתך).

## Answer
התבניות המתאימות ביותר לפתרון בעיה זו הן **תבנית האסטרטגיה (Strategy Pattern)** ו**תבנית האיטרטור (Iterator Pattern)**.

**הסבר:**
*   **תבנית האסטרטגיה:** מאפשרת להחליף את מבנה הנתונים הפנימי של `ExamContainer` (לדוגמה, `LinkedList` או `ArrayList`) מבלי לשנות את קוד הלקוח. `ExamContainer` יחזיק הפניה לממשק `ExamDataStructure`, ויוכל לקבל מימושים שונים של ממשק זה.
*   **תבנית האיטרטור:** מאפשרת ללקוח לעבור על אוסף הבחינות בתוך `ExamContainer` באופן אחיד, מבלי לחשוף את המבנה הפנימי של אוסף הנתונים. `ExamContainer` יממש את הממשק `Iterable<Exam>`, ובכך יאפשר שימוש בלולאת `for-each` כפי שנדרש.

**תרשים מחלקות (UML Diagram):**
```mermaid
classDiagram
    direction LR

    class Exam <<abstract>> {
        +String examId
        +check()
    }

    class MixedExam
    class OpenExam
    class ScrambledExam

    interface ExamDataStructure {
        +add(Exam exam)
        +iterator(): Iterator<Exam>
    }

    class LinkedListExamDataStructure {
        -List<Exam> exams
        +add(Exam exam)
        +iterator(): Iterator<Exam>
    }

    class ArrayListExamDataStructure {
        -List<Exam> exams
        +add(Exam exam)
        +iterator(): Iterator<Exam>
    }

    class ExamContainer {
        -ExamDataStructure dataStructure
        +ExamContainer(ExamDataStructure dataStructure)
        +addExam(Exam exam)
        +iterator(): Iterator<Exam>
    }

    Exam <|-- MixedExam
    Exam <|-- OpenExam
    Exam <|-- ScrambledExam

    ExamDataStructure <|.. LinkedListExamDataStructure
    ExamDataStructure <|.. ArrayListExamDataStructure

    ExamContainer o-- ExamDataStructure : uses >
    ExamContainer ..|> Iterable<Exam>
    Iterator <|.. ExamContainer.ExamIterator
```

**קוד עבור המחלקות (Java Code Structure):**

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

// Assuming Exam and its subtypes (MixedExam, OpenExam, ScrambledExam) are defined,
// and Exam has an abstract check() method as per problem description.
abstract class Exam {
    private String examId;

    public Exam(String examId) {
        this.examId = examId;
    }

    public String getExamId() {
        return examId;
    }

    public abstract void check(); // Abstract method as per problem description
}

class MixedExam extends Exam {
    public MixedExam(String examId) { super(examId); }
    @Override public void check() { System.out.println("Checking MixedExam " + getExamId()); }
}

class OpenExam extends Exam {
    public OpenExam(String examId) { super(examId); }
    @Override public void check() { System.out.println("Checking OpenExam " + getExamId()); }
}

class ScrambledExam extends Exam {
    public ScrambledExam(String examId) { super(examId); }
    @Override public void check() { System.out.println("Checking ScrambledExam " + getExamId()); }
}


// Strategy Interface for internal data structure
interface ExamDataStructure {
    void add(Exam exam);
    Iterator<Exam> iterator();
}

// Concrete Strategy 1: LinkedList implementation
class LinkedListExamDataStructure implements ExamDataStructure {
    private List<Exam> exams = new LinkedList<>();

    @Override
    public void add(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> iterator() {
        return exams.iterator();
    }
}

// Concrete Strategy 2: ArrayList implementation (example, for flexibility)
class ArrayListExamDataStructure implements ExamDataStructure {
    private List<Exam> exams = new ArrayList<>();

    @Override
    public void add(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> iterator() {
        return exams.iterator();
    }
}

// Context: ExamContainer, implementing Iterable for Iterator pattern
class ExamContainer implements Iterable<Exam> {
    private ExamDataStructure dataStructure; // Strategy reference

    public ExamContainer(ExamDataStructure dataStructure) {
        this.dataStructure = dataStructure;
    }

    public void addExam(Exam exam) {
        dataStructure.add(exam);
    }

    // Iterator Pattern implementation
    @Override
    public Iterator<Exam> iterator() {
        return dataStructure.iterator();
    }
}

// Main class for demonstration
public class Main {
    public static void checkAllExams(ExamContainer examContainer) {
        for (Exam exam : examContainer) {
            exam.check();
        }
    }

    public static void main(String[] args) {
        // Initialize ExamContainer with a LinkedList-based data structure strategy
        ExamContainer container = new ExamContainer(new LinkedListExamDataStructure());

        // Add three exam instances of different types
        container.addExam(new MixedExam("MIX-2023-001"));
        container.addExam(new OpenExam("OPEN-2023-002"));
        container.addExam(new ScrambledExam("SCRAM-2023-003"));

        // Demonstrate iteration and checking using the provided client code structure
        System.out.println("Checking all exams in the container:");
        checkAllExams(container);

        // Example of changing strategy (not explicitly required in main, but shows flexibility)
        // ExamContainer container2 = new ExamContainer(new ArrayListExamDataStructure());
        // container2.addExam(new MixedExam("MIX-2024-001"));
        // System.out.println("\nChecking exams in a new container with ArrayList strategy:");
        // checkAllExams(container2);
    }
}
```
