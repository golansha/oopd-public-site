---
id: exam_2025_B_B_Open_q3
title: Exam Management System - Adding New Operations
year: 2025
semester: B
moed: B
type: Open
topics:
- Design Patterns
- Object-Oriented Design
- Visitor Pattern
skills:
- Design Pattern Application
- UML Diagramming
- Java Programming
---

## Question
במערכת לניהול בחינות ישנה מחלקה מופשטת Exam המייצגת בחינה. ישנם מספר תתי סוגים שונים של בחינות: MixedExam, OpenExam, ScrambledExam וכן הלאה.סעיף א (10 נקודות)נתבקשנו להוסיף למערכת תמיכה בהוספה עתידית של פעולות שניתן להפעיל על מופעים של בחינות, אך אינן תחת האחריות הישירה של Exam. להלן שתי פעולות לדוגמא :פעולה שבודקת האם יש חשד להעתקות במחברות של בחינה. הפעולה תומכת ב- MixedExam-וב ScrambledExamפעולה שמבצעת בדיקות סטטיסטיות לא שגרתיות על מופע של בחינה מסומת. הפעולה תומכת ב OpenExam-וב ScrambledExamחשוב להדגיש כי עבור סוגים שונים של בחינות יש דרך שונה לבצע את הפעולות.הערה: מערכת ניהול בדיקת הבחינות הולכת ומתפתחת משנה לשנה, ויש צפי להוספת סוגי בחינות חדשות בעתיד.השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות.צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. אין צורך לממש את תוכן הפעולות עצמן, אלא רק את התבנית שמאפשרת להפעיל אותן.

## Answer
התבנית המתאימה ביותר לפתרון בעיה זו היא **תבנית המבקר (Visitor Pattern)**.

**הסבר:**
תבנית המבקר מאפשרת להוסיף פעולות חדשות למבנה אובייקטים קיים (היררכיית `Exam`) מבלי לשנות את המחלקות של המבנה עצמו. זה מתאים לדרישה להוסיף פעולות שאינן באחריות ישירה של `Exam` ולצפי להוספת סוגי בחינות ופעולות חדשות בעתיד. כל פעולה חדשה (כמו בדיקת העתקות או ניתוח סטטיסטי) תמומש כמבקר (Visitor) נפרד, וכל סוג בחינה (Element) ידע 'לקבל' מבקר.

**תרשים מחלקות (UML Diagram):**
```mermaid
classDiagram
    direction LR

    class Exam <<abstract>> {
        +String examId
        +accept(ExamVisitor visitor)
    }

    class MixedExam {
        +MixedExam(String examId)
        +accept(ExamVisitor visitor)
    }

    class OpenExam {
        +OpenExam(String examId)
        +accept(ExamVisitor visitor)
    }

    class ScrambledExam {
        +ScrambledExam(String examId)
        +accept(ExamVisitor visitor)
    }

    interface ExamVisitor {
        +visit(MixedExam exam)
        +visit(OpenExam exam)
        +visit(ScrambledExam exam)
    }

    class CheatingDetectorVisitor {
        +visit(MixedExam exam)
        +visit(OpenExam exam)
        +visit(ScrambledExam exam)
    }

    class StatisticalAnalyzerVisitor {
        +visit(MixedExam exam)
        +visit(OpenExam exam)
        +visit(ScrambledExam exam)
    }

    Exam <|-- MixedExam
    Exam <|-- OpenExam
    Exam <|-- ScrambledExam

    ExamVisitor <|.. CheatingDetectorVisitor
    ExamVisitor <|.. StatisticalAnalyzerVisitor

    Exam "1" --> "1" ExamVisitor : uses >
```

**קוד עבור המחלקות (Java Code Structure):**

```java
// Element Interface/Abstract Class
public abstract class Exam {
    private String examId; // Example field

    public Exam(String examId) {
        this.examId = examId;
    }

    public String getExamId() {
        return examId;
    }

    // The key method for the Visitor pattern
    public abstract void accept(ExamVisitor visitor);
}

// Concrete Elements
public class MixedExam extends Exam {
    public MixedExam(String examId) {
        super(examId);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
    // MixedExam specific methods/fields
}

public class OpenExam extends Exam {
    public OpenExam(String examId) {
        super(examId);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
    // OpenExam specific methods/fields
}

public class ScrambledExam extends Exam {
    public ScrambledExam(String examId) {
        super(examId);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
    // ScrambledExam specific methods/fields
}

// Visitor Interface
public interface ExamVisitor {
    void visit(MixedExam exam);
    void visit(OpenExam exam);
    void visit(ScrambledExam exam);
}

// Concrete Visitor 1: Cheating Detector
public class CheatingDetectorVisitor implements ExamVisitor {
    @Override
    public void visit(MixedExam exam) {
        System.out.println("Checking MixedExam " + exam.getExamId() + " for cheating.");
        // Specific logic for MixedExam cheating detection
    }

    @Override
    public void visit(OpenExam exam) {
        System.out.println("Cheating detection not applicable for OpenExam " + exam.getExamId() + ".");
    }

    @Override
    public void visit(ScrambledExam exam) {
        System.out.println("Checking ScrambledExam " + exam.getExamId() + " for cheating.");
        // Specific logic for ScrambledExam cheating detection
    }
}

// Concrete Visitor 2: Statistical Analyzer
public class StatisticalAnalyzerVisitor implements ExamVisitor {
    @Override
    public void visit(MixedExam exam) {
        System.out.println("Statistical analysis not applicable for MixedExam " + exam.getExamId() + ".");
    }

    @Override
    public void visit(OpenExam exam) {
        System.out.println("Performing statistical analysis on OpenExam " + exam.getExamId() + ".");
        // Specific logic for OpenExam statistical analysis
    }

    @Override
    public void visit(ScrambledExam exam) {
        System.out.println("Performing statistical analysis on ScrambledExam " + exam.getExamId() + ".");
        // Specific logic for ScrambledExam statistical analysis
    }
}
```
