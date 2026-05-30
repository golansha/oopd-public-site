---
id: exam_2025_B_B_MultipleChoice_q11
title: LSP Violation Testing
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- LSP
skills:
- Applying LSP
- Testing for LSP
---

## Question
מחלקת NetworkConnection מממשת ממשק כללי לניהול חיבורי רשת ושליחת נתונים. מחלקת HttpConnection יורשת ממחלקת NetworkConnection ומממשת את פעולות החיבור והשליחה בהתאם לפרוטוקול HTTP. מה מהדברים הבאים אינו מהווה חלק מתהליך הבדיקה של עמידה בעקרון Liskov Substitution Principle (LSP)?

### Options
- הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות HTTP מוגדר כסוג של חיבור רשת.
- וידוא שפונקציית ה-sendData של HttpClient מסוגלת להתמודד עם כל המידע שמחלקת NetworkConnection יכולה לשלוח.
- הרצת סדרת בדיקות על מופע NetworkConnection ולוודא שהתנהגותן נשמרת גם על מופע HttpClient כולל התייחסות לפלטים ותופעות לוואי.
- יש שתי תשובות אחרות נכונות.

## Answer
עיקרון ההחלפה של ליסקוב (LSP) עוסק בתאימות התנהגותית של תתי-מחלקות למחלקות הבסיס שלהן. 'הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות HTTP מוגדר כסוג של חיבור רשת' היא הנחה קונספטואלית, ולא חלק מתהליך בדיקה בפועל של התנהגות. LSP דורש בדיקה אמפירית שהתנהגות תת-הטיפוס תואמת את ציפיות טיפוס הבסיס, ולא רק הסתמכות על הגדרה מילונית או קונספטואלית.
