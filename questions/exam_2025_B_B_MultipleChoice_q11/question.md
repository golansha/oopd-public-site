---
id: exam_2025_B_B_MultipleChoice_q11
title: LSP Violation Check
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- Liskov Substitution Principle (LSP)
- Polymorphism
- Testing
skills:
- LSP Application
- Code Analysis
- Design Principles
---

## Question
מחלקת NetworkConnection מממשת ממשק כללי לניהול חיבורי רשת ושליחת נתונים. מחלקת HttpConnection יורשת ממחלקת NetworkConnection ומממשת את פעולות החיבור והשליחה בהתאם לפרוטוקול HTTP. מה מהדברים הבאים אינו מהווה חלק מתהליך הבדיקה של עמידה בעקרון Liskov Substitution Principle (LSP)? הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות HTTP מוגדר כסוג של חיבור רשת.

### Options
- נתון הקוד של הפונקציה copy המעתיקה את האלמנטים הנמצאים ברשימה src לתוך הרשימה dest. בקוד הושמטו הטיפוסים של src,dest
- וידוא שפונקציית ה-sendData של HttpClient מסוגלת להתמודד עם כל המידע שמחלקת NetworkConnection יכולה לשלוח.
- הרצת סדרת בדיקות על מופע NetworkConnection ולוודא שהתנהגותן נשמרת גם על מופע HttpClient כולל התייחסות לפלטים ותופעות לוואי.
- יש שתי תשובות אחרות נכונות.

## Answer
האפשרות "נתון הקוד של הפונקציה copy המעתיקה את האלמנטים הנמצאים ברשימה src לתוך הרשימה dest. בקוד הושמטו הטיפוסים של src,dest" אינה קשורה כלל לבדיקת עמידה בעקרון LSP עבור המחלקות `NetworkConnection` ו-`HttpConnection`. שתי האפשרויות האחרות (וידוא יכולת טיפול בנתונים והרצת בדיקות על מופעים חלופיים) הן בדיוק מה שנדרש כדי לבדוק עמידה ב-LSP.
