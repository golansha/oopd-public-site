---
id: exam_2025_B_B_Open_q3
title: ניהול בחינות - הוספת פעולות
year: 2025
semester: B
moed: B
type: Open
topics:
- Design Patterns
- Visitor Pattern
- Object-Oriented Design
skills:
- Pattern Application
- UML Diagrams
- Code Implementation
---

## Question
במערכת לניהול בחינות ישנה מחלקה מופשטת Exam המייצגת בחינה. ישנם מספר תתי סוגים שונים של בחינות: MixedExam, OpenExam, ScrambledExam וכן הלאה. סעיף א (10 נקודות) נתבקשנו להוסיף למערכת תמיכה בהוספה עתידית של פעולות שניתן להפעיל על מופעים של בחינות, אך אינן תחת האחריות הישירה של Exam. להלן שתי פעולות לדוגמא: • פעולה שבודקת האם יש חשד להעתקות במחברות של בחינה. הפעולה תומכת ב- MixedExam-וב ScrambledExam • פעולה שמבצעת בדיקות סטטיסטיות לא שגרתיות על מופע של בחינה מסומת. הפעולה תומכת ב OpenExam-וב ScrambledExam חשוב להדגיש כי עבור סוגים שונים של בחינות יש דרך שונה לבצע את הפעולות. הערה: מערכת ניהול בדיקת הבחינות הולכת ומתפתחת משנה לשנה, ויש צפי להוספת סוגי בחינות חדשות בעתיד. השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. אין צורך לממש את תוכן הפעולות עצמן, אלא רק את התבנית שמאפשרת להפעיל אותן.

## Answer
**תבנית העיצוב:** Visitor Pattern

**הסבר:**
תבנית ה-Visitor מאפשרת להוסיף פעולות חדשות למבנה אובייקטים קיים (כמו היררכיית המחלקות `Exam`) מבלי לשנות את המחלקות עצמן. זה מתאים לדרישה שפעולות חדשות אינן תחת האחריות הישירה של `Exam` ושיש צפי להוספת סוגי בחינות חדשות בעתיד, מה שהופך את המערכת לגמישה וקלה להרחבה.

**תרשים מחלקות (UML):**
```mermaid
classDiagram
    abstract class Exam {
        +accept(visitor: ExamVisitor)
    }

    class OpenExam {
        +accept(visitor: ExamVisitor)
    }
    class MixedExam {
        +accept(visitor: ExamVisitor)
    }
    class ScrambledExam {
        +accept(visitor: ExamVisitor)
    }

    interface ExamVisitor {
        +visit(exam: OpenExam)
        +visit(exam: MixedExam)
        +visit(exam: ScrambledExam)
    }

    class CheatingDetectionVisitor {
        +visit(exam: OpenExam)
        +visit(exam: MixedExam)
        +visit(exam: ScrambledExam)
    }

    class StatisticalAnalysisVisitor {
        +visit(exam: OpenExam)
        +visit(exam: MixedExam)
        +visit(exam: ScrambledExam)
    }

    Exam <|-- OpenExam
    Exam <|-- MixedExam
    Exam <|-- ScrambledExam

    ExamVisitor <|.. CheatingDetectionVisitor
    ExamVisitor <|.. StatisticalAnalysisVisitor

    Exam "1" --> "1" ExamVisitor : uses >
```

**קוד המחלקות:**

```java
// 1. Element Interface (Exam)
abstract class Exam {
    String title;

    public Exam(String title) {
        this.title = title;
    }

    public String getTitle() {
        return title;
    }

    // The accept method is crucial for the Visitor pattern
    public abstract void accept(ExamVisitor visitor);
}

// 2. Concrete Elements
class OpenExam extends Exam {
    public OpenExam(String title) {
        super(title);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
}

class MixedExam extends Exam {
    public MixedExam(String title) {
        super(title);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
}

class ScrambledExam extends Exam {
    public ScrambledExam(String title) {
        super(title);
    }

    @Override
    public void accept(ExamVisitor visitor) {
        visitor.visit(this);
    }
}

// 3. Visitor Interface
interface ExamVisitor {
    void visit(OpenExam exam);
    void visit(MixedExam exam);
    void visit(ScrambledExam exam);
    // Add new visit methods for new Exam types as they are introduced
}

// 4. Concrete Visitors (for specific operations)
class CheatingDetectionVisitor implements ExamVisitor {
    @Override
    public void visit(OpenExam exam) {
        // Logic for cheating detection for OpenExam
        System.out.println("Performing cheating detection for Open Exam: " + exam.getTitle());
    }

    @Override
    public void visit(MixedExam exam) {
        // Logic for cheating detection for MixedExam
        System.out.println("Performing cheating detection for Mixed Exam: " + exam.getTitle());
    }

    @Override
    public void visit(ScrambledExam exam) {
        // Logic for cheating detection for ScrambledExam
        System.out.println("Performing cheating detection for Scrambled Exam: " + exam.getTitle());
    }
}

class StatisticalAnalysisVisitor implements ExamVisitor {
    @Override
    public void visit(OpenExam exam) {
        // Logic for statistical analysis for OpenExam
        System.out.println("Performing statistical analysis for Open Exam: " + exam.getTitle());
    }

    @Override
    public void visit(MixedExam exam) {
        // Logic for statistical analysis for MixedExam
        System.out.println("Performing statistical analysis for Mixed Exam: " + exam.getTitle());
    }

    @Override
    public void visit(ScrambledExam exam) {
        // Logic for statistical analysis for ScrambledExam
        System.out.println("Performing statistical analysis for Scrambled Exam: " + exam.getTitle());
    }
}

// Example Usage (Client Code)
public class ExamClient {
    public static void main(String[] args) {
        List<Exam> exams = List.of(
                new OpenExam("Math Midterm"),
                new MixedExam("Physics Final"),
                new ScrambledExam("Chemistry Quiz")
        );

        ExamVisitor cheatingDetector = new CheatingDetectionVisitor();
        ExamVisitor statsAnalyzer = new StatisticalAnalysisVisitor();

        System.out.println("--- Running Cheating Detection ---");
        for (Exam exam : exams) {
            exam.accept(cheatingDetector);
        }

        System.out.println("\n--- Running Statistical Analysis ---");
        for (Exam exam : exams) {
            exam.accept(statsAnalyzer);
        }
    }
}
```
