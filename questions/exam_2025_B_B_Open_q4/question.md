---
id: exam_2025_B_B_Open_q4
title: ניהול בחינות - מבנה נתונים גמיש
year: 2025
semester: B
moed: B
type: Open
topics:
- Design Patterns
- Bridge Pattern
- Iterator Pattern
- Data Structures
- Object-Oriented Design
skills:
- Pattern Application
- UML Diagrams
- Code Implementation
- Abstraction
---

## Question
במכללה מסוימת, המשתמשת במערכת הנייל, רוצים מדי פעם לשמור מופעי בחינות במבנה נתונים. אחד השימושים האפשריים במבני הנתונים הוא למשל לשמור את כל מופעי הבחינות שהתקיימו בסמסטר מסוים במחלקת מחשבים. נתונות הדרישות הבאות : • הקליינט יוכל להוסיף בחינות למבנה הנתונים. • לא להיות מוגבלים למבנה נתונים ספציפי. דהיינו, יהיה ניתן להחליף את מבנה הנתונים בלי שיהיה צורך לשנות את הקוד של הקליינט שניגש לנתונים. • הקליינט יוכל לעבור על כל מופעי הבחינות, בלי להיות תלוי כלל במבנה הנתונים הספציפי שבו השתמשו. הניחו כי למחלקה Exam יש פונקציה מופשטת check. נרצה שהקוד הבא יעבוד בצורה תקינה : public void checkAllExams(ExamContainer examContainer){ for (Exam exam: examContainer){ exam.check(); } } יש לתכנן את המחלקה ExamContainer כך שמבנה הנתונים הפנימי שלה יהיה ניתן להחלפה ללא צורך לקמפל מחדש את הקוד שלה. ניתן להשתמש במחלקות המוגדרות באופן מובנה בשפת Java. השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. ממש פונקציה ראשית שבה מאתחלים מופע של ExamContainer המתבסס על רשימה מקושרת (LinkedList) ומוסיפים למבנה הנתונים שלושה מופעים של בחינה (מסוגים לבחירתך).

## Answer
**תבניות העיצוב:** Bridge Pattern, Iterator Pattern

**הסבר:**
1.  **Bridge Pattern:** נדרש לאפשר החלפה של מבנה הנתונים הפנימי של `ExamContainer` (לדוגמה, מ-`LinkedList` ל-`ArrayList`) מבלי לשנות את קוד הלקוח. תבנית ה-Bridge מפרידה את ההפשטה (`ExamContainer`) מהמימוש שלה (מבנה הנתונים בפועל), כך ששניהם יכולים להשתנות באופן בלתי תלוי. `ExamContainer` יחזיק הפניה לממשק `ExamDataStructure`.
2.  **Iterator Pattern:** נדרש לאפשר ללקוח לעבור על כל הבחינות ב-`ExamContainer` מבלי להיות תלוי במבנה הנתונים הספציפי. תבנית ה-Iterator מספקת דרך לגשת לאלמנטים של אובייקט אגרגציה באופן סדרתי מבלי לחשוף את הייצוג הפנימי שלו. `ExamContainer` יממש את הממשק `Iterable<Exam>` ויספק `Iterator<Exam>`.

**תרשים מחלקות (UML):**
```mermaid
classDiagram
    abstract class Exam {
        +check()
    }

    interface ExamDataStructure {
        +addExam(exam: Exam)
        +createIterator(): Iterator<Exam>
    }

    class LinkedListExamDataStructure {
        -exams: List<Exam>
        +addExam(exam: Exam)
        +createIterator(): Iterator<Exam>
    }

    class ArrayListExamDataStructure {
        -exams: List<Exam>
        +addExam(exam: Exam)
        +createIterator(): Iterator<Exam>
    }

    class ExamContainer {
        -dataStructure: ExamDataStructure
        +ExamContainer(dataStructure: ExamDataStructure)
        +addExam(exam: Exam)
        +iterator(): Iterator<Exam>
    }

    ExamContainer "1" --> "1" ExamDataStructure : uses (Bridge)
    ExamDataStructure <|.. LinkedListExamDataStructure
    ExamDataStructure <|.. ArrayListExamDataStructure
    ExamContainer ..|> Iterable : implements
    Iterable <|-- Iterator : creates

    class OpenExam
    class MixedExam
    class ScrambledExam
    Exam <|-- OpenExam
    Exam <|-- MixedExam
    Exam <|-- ScrambledExam
```

**קוד המחלקות:**

```java
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;
import java.util.ArrayList;

// Assuming Exam and its subclasses (OpenExam, MixedExam, ScrambledExam) are defined as in 3A
// For completeness, defining them here again:

abstract class Exam {
    String title;

    public Exam(String title) {
        this.title = title;
    }

    public String getTitle() {
        return title;
    }

    public abstract void check();
}

class OpenExam extends Exam {
    public OpenExam(String title) {
        super(title);
    }

    @Override
    public void check() {
        System.out.println("Checking OpenExam: " + title);
    }
}

class MixedExam extends Exam {
    public MixedExam(String title) {
        super(title);
    }

    @Override
    public void check() {
        System.out.println("Checking MixedExam: " + title);
    }
}

class ScrambledExam extends Exam {
    public ScrambledExam(String title) {
        super(title);
    }

    @Override
    public void check() {
        System.out.println("Checking ScrambledExam: " + title);
    }
}

// Implementor Interface for Bridge Pattern
interface ExamDataStructure {
    void addExam(Exam exam);
    Iterator<Exam> createIterator();
}

// Concrete Implementor 1: LinkedList
class LinkedListExamDataStructure implements ExamDataStructure {
    private List<Exam> exams = new LinkedList<>();

    @Override
    public void addExam(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> createIterator() {
        return exams.iterator();
    }
}

// Concrete Implementor 2: ArrayList (for demonstration of flexibility)
class ArrayListExamDataStructure implements ExamDataStructure {
    private List<Exam> exams = new ArrayList<>();

    @Override
    public void addExam(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> createIterator() {
        return exams.iterator();
    }
}

// Abstraction for Bridge Pattern, also implements Iterable for Iterator Pattern
class ExamContainer implements Iterable<Exam> {
    private ExamDataStructure dataStructure;

    public ExamContainer(ExamDataStructure dataStructure) {
        this.dataStructure = dataStructure;
    }

    public void addExam(Exam exam) {
        dataStructure.addExam(exam);
    }

    @Override
    public Iterator<Exam> iterator() {
        return dataStructure.createIterator();
    }
}

// Main class to demonstrate usage
public class Main {

    // Client code as provided in the question
    public static void checkAllExams(ExamContainer examContainer) {
        for (Exam exam : examContainer) {
            exam.check();
        }
    }

    public static void main(String[] args) {
        // Initialize ExamContainer with LinkedList implementation
        System.out.println("Initializing with LinkedListExamDataStructure:");
        ExamContainer container = new ExamContainer(new LinkedListExamDataStructure());

        // Add three exams of different types
        container.addExam(new OpenExam("Midterm 1"));
        container.addExam(new MixedExam("Final Exam"));
        container.addExam(new ScrambledExam("Quiz 3"));

        // Client code checks all exams without knowing the underlying data structure
        checkAllExams(container);

        System.out.println("\nInitializing with ArrayListExamDataStructure (demonstrating flexibility):");
        ExamContainer anotherContainer = new ExamContainer(new ArrayListExamDataStructure());
        anotherContainer.addExam(new OpenExam("Pop Quiz"));
        anotherContainer.addExam(new MixedExam("Semester Project"));
        checkAllExams(anotherContainer);
    }
}
```
