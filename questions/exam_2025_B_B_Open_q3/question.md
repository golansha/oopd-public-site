---
id: exam_2025_B_B_Open_q3
title: Exam Operations
year: 2025
semester: B
moed: B
type: Open
topics:
- Design patterns - General
- SOLID - OCP
- UML - תרשים מחלקות
skills:
- Design Patterns
- Object-Oriented Design
- UML Modeling
---

## Question
במערכת לניהול בחינות ישנה מחלקה מופשטת `Exam` המייצגת בחינה. ישנם מספר תתי סוגים שונים של בחינות: `MixedExam`, `OpenExam`, `ScrambledExam` וכן הלאה.

**סעיף א (10 נקודות)**
נתבקשנו להוסיף למערכת תמיכה בהוספה עתידית של פעולות שניתן להפעיל על מופעים של בחינות, אך אינן תחת האחריות הישירה של `Exam`. להלן שתי פעולות לדוגמא :
*   פעולה שבודקת האם יש חשד להעתקות במחברות של בחינה. הפעולה תומכת ב-`MixedExam`-וב `ScrambledExam`
*   פעולה שמבצעת בדיקות סטטיסטיות לא שגרתיות על מופע של בחינה מסומת. הפעולה תומכת ב-`OpenExam`-וב `ScrambledExam`
חשוב להדגיש כי עבור סוגים שונים של בחינות יש דרך שונה לבצע את הפעולות.

הערה: מערכת ניהול בדיקת הבחינות הולכת ומתפתחת משנה לשנה, ויש צפי להוספת סוגי בחינות חדשות בעתיד.

השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. אין צורך לממש את תוכן הפעולות עצמן, אלא רק את התבנית שמאפשרת להפעיל אותן.

**סעיף ב (10 נקודות)**
במכללה מסוימת, המשתמשת במערכת הנייל, רוצים מדי פעם לשמור מופעי בחינות במבנה נתונים. אחד השימושים האפשריים במבני הנתונים הוא למשל לשמור את כל מופעי הבחינות שהתקיימו בסמסטר מסוים במחלקת מחשבים.
נתונות הדרישות הבאות :
*   הקליינט יוכל להוסיף בחינות למבנה הנתונים.
*   לא להיות מוגבלים למבנה נתונים ספציפי. דהיינו, יהיה ניתן להחליף את מבנה הנתונים בלי שיהיה צורך לשנות את הקוד של הקליינט שניגש לנתונים.
*   הקליינט יוכל לעבור על כל מופעי הבחינות, בלי להיות תלוי כלל במבנה הנתונים הספציפי שבו השתמשו.
הניחו כי למחלקה `Exam` יש פונקציה מופשטת `check`. נרצה שהקוד הבא יעבוד בצורה תקינה :
```java
public void checkAllExams(ExamContainer examContainer){
    for (Exam exam: examContainer){
        exam.check();
    }
}
```
יש לתכנן את המחלקה `ExamContainer` כך שמבנה הנתונים הפנימי שלה יהיה ניתן להחלפה ללא צורך לקמפל מחדש את הקוד שלה. ניתן להשתמש במחלקות המוגדרות באופן מובנה בשפת Java.

השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. ממש פונקציה ראשית שבה מאתחלים מופע של `ExamContainer` המתבסס על רשימה מקושרת (`LinkedList`) ומוסיפים למבנה הנתונים שלושה מופעים של בחינה (מסוגים לבחירתך).

## Answer
**סעיף א: תבנית Visitor**

**שם תבנית העיצוב:** Visitor Pattern

**הסבר:** תבנית ה-Visitor מאפשרת להוסיף פעולות חדשות למבנה אובייקטים (כמו היררכיית `Exam`) מבלי לשנות את המחלקות של האובייקטים עצמם. זה עונה על הדרישה להוסיף פעולות שאינן תחת אחריות `Exam` ולתמוך בהוספת סוגי בחינות חדשים בעתיד (Open/Closed Principle).

**תרשים מחלקות (UML):**
```mermaid
classDiagram
    direction LR

    class Exam <<abstract>> {
        +accept(visitor:ExamVisitor)
    }
    class OpenExam {
        +accept(visitor:ExamVisitor)
    }
    class MixedExam {
        +accept(visitor:ExamVisitor)
    }
    class ScrambledExam {
        +accept(visitor:ExamVisitor)
    }

    interface ExamVisitor {
        +visit(exam:OpenExam)
        +visit(exam:MixedExam)
        +visit(exam:ScrambledExam)
    }

    class PlagiarismChecker {
        +visit(exam:MixedExam)
        +visit(exam:ScrambledExam)
    }
    class StatisticalAnalyzer {
        +visit(exam:OpenExam)
        +visit(exam:ScrambledExam)
    }

    Exam <|-- OpenExam
    Exam <|-- MixedExam
    Exam <|-- ScrambledExam

    ExamVisitor <|.. PlagiarismChecker
    ExamVisitor <|.. StatisticalAnalyzer

    Exam "1" --> "1" ExamVisitor : uses
    OpenExam "1" --> "1" ExamVisitor : uses
    MixedExam "1" --> "1" ExamVisitor : uses
    ScrambledExam "1" --> "1" ExamVisitor : uses

```

**קוד עבור המחלקות:**

```java
// Exam.java
public abstract class Exam {
    public abstract void accept(ExamVisitor visitor);
    public abstract void check(); // Existing abstract method
}

// OpenExam.java
public class OpenExam extends Exam {
    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }

    @Override
    public void check() {
        System.out.println("Checking Open Exam");
    }
}

// MixedExam.java
public class MixedExam extends Exam {
    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }

    @Override
    public void check() {
        System.out.println("Checking Mixed Exam");
    }
}

// ScrambledExam.java
public class ScrambledExam extends Exam {
    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }

    @Override
    public void check() {
        System.out.println("Checking Scrambled Exam");
    }
}

// ExamVisitor.java (Interface)
public interface ExamVisitor {
    void visit(OpenExam exam);
    void visit(MixedExam exam);
    void visit(ScrambledExam exam);
}

// PlagiarismChecker.java
public class PlagiarismChecker implements ExamVisitor {
    @Override
    public void visit(OpenExam exam) {
        // Not supported for OpenExam as per problem description
    }

    @Override
    public void visit(MixedExam exam) {
        System.out.println("Checking Mixed Exam for plagiarism.");
    }

    @Override
    public void visit(ScrambledExam exam) {
        System.out.println("Checking Scrambled Exam for plagiarism.");
    }
}

// StatisticalAnalyzer.java
public class StatisticalAnalyzer implements ExamVisitor {
    @Override
    public void visit(OpenExam exam) {
        System.out.println("Performing statistical analysis on Open Exam.");
    }

    @Override
    public void visit(MixedExam exam) {
        // Not supported for MixedExam as per problem description
    }

    @Override
    public void visit(ScrambledExam exam) {
        System.out.println("Performing statistical analysis on Scrambled Exam.");
    }
}
```

**סעיף ב: תבנית Iterator ו-Strategy**

**שמות תבניות העיצוב:** Iterator Pattern, Strategy Pattern

**הסבר:**
*   **Iterator Pattern:** מאפשר גישה סדרתית לאלמנטים של אוסף (כמו מבנה נתונים של בחינות) מבלי לחשוף את הייצוג הפנימי שלו. זה עונה על הדרישה שהקליינט יוכל לעבור על כל מופעי הבחינות בלי להיות תלוי במבנה הנתונים הספציפי.
*   **Strategy Pattern:** מאפשר להגדיר משפחה של אלגוריתמים, לעטוף כל אחד מהם במחלקה נפרדת, ולגרום להם להיות ניתנים להחלפה. במקרה זה, ה-`ExamContainer` יכול להשתמש באסטרטגיה שונה לייצוג מבנה הנתונים הפנימי (למשל, `LinkedListStrategy`, `ArrayListStrategy`), מה שמאפשר להחליף את מבנה הנתונים הפנימי ללא שינוי בקוד הקליינט.

**תרשים מחלקות (UML):**
```mermaid
classDiagram
    direction LR

    interface ExamContainerStrategy {
        +addExam(exam:Exam)
        +getExams():Iterator<Exam>
    }

    class LinkedListStrategy {
        +addExam(exam:Exam)
        +getExams():Iterator<Exam>
    }

    class ArrayListStrategy {
        +addExam(exam:Exam)
        +getExams():Iterator<Exam>
    }

    class ExamContainer {
        -strategy:ExamContainerStrategy
        +ExamContainer(strategy:ExamContainerStrategy)
        +addExam(exam:Exam)
        +iterator():Iterator<Exam>
    }

    interface Iterator<Exam> {
        +hasNext():boolean
        +next():Exam
    }

    ExamContainer "1" --> "1" ExamContainerStrategy : uses
    ExamContainerStrategy <|.. LinkedListStrategy
    ExamContainerStrategy <|.. ArrayListStrategy
    ExamContainer "1" --> "1" Iterator : creates

    class Exam {
        +check()
    }

    Iterator "1" --> "*" Exam : iterates over

```

**קוד עבור המחלקות:**

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

// Exam.java (from part A, with check() method)
public abstract class Exam {
    public abstract void check();
}

// OpenExam, MixedExam, ScrambledExam (concrete Exam types from part A)
// ... (definitions as in part A)

// ExamContainerStrategy.java
public interface ExamContainerStrategy {
    void addExam(Exam exam);
    Iterator<Exam> getExamsIterator();
}

// LinkedListStrategy.java
public class LinkedListStrategy implements ExamContainerStrategy {
    private List<Exam> exams = new LinkedList<>();

    @Override
    public void addExam(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> getExamsIterator() {
        return exams.iterator();
    }
}

// ArrayListStrategy.java
public class ArrayListStrategy implements ExamContainerStrategy {
    private List<Exam> exams = new ArrayList<>();

    @Override
    public void addExam(Exam exam) {
        exams.add(exam);
    }

    @Override
    public Iterator<Exam> getExamsIterator() {
        return exams.iterator();
    }
}

// ExamContainer.java
public class ExamContainer implements Iterable<Exam> {
    private ExamContainerStrategy strategy;

    public ExamContainer(ExamContainerStrategy strategy) {
        this.strategy = strategy;
    }

    public void addExam(Exam exam) {
        strategy.addExam(exam);
    }

    @Override
    public Iterator<Exam> iterator() {
        return strategy.getExamsIterator();
    }
}

// Main.java (for initialization and demonstration)
public class Main {
    public static void main(String[] args) {
        // Initialize ExamContainer with LinkedListStrategy
        ExamContainer examContainer = new ExamContainer(new LinkedListStrategy());

        // Add three exams of different types
        examContainer.addExam(new OpenExam());
        examContainer.addExam(new MixedExam());
        examContainer.addExam(new ScrambledExam());

        // The client code from the question, which now works correctly
        checkAllExams(examContainer);

        System.out.println("\nSwitching to ArrayListStrategy:");
        // Demonstrate changing strategy (e.g., for a new container)
        ExamContainer anotherExamContainer = new ExamContainer(new ArrayListStrategy());
        anotherExamContainer.addExam(new OpenExam());
        anotherExamContainer.addExam(new OpenExam());
        checkAllExams(anotherExamContainer);
    }

    public static void checkAllExams(ExamContainer examContainer) {
        for (Exam exam : examContainer) {
            exam.check();
        }
    }
}
```
