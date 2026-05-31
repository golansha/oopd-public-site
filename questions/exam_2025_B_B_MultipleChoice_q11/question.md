---
id: exam_2025_B_B_MultipleChoice_q11
title: Liskov Substitution Principle (LSP) Testing
year: 2025
semester: B
moed: B
type: Multiple Choice
topics:
- SOLID Principles
- Liskov Substitution Principle (LSP)
- Testing
skills:
- Principle Application
- Testing Methodologies
---

## Question
מחלקת NetworkConnection מממשת ממשק כללי לניהול חיבורי רשת ושליחת נתונים. מחלקת HttpConnection יורשת ממחלקת NetworkConnection ומממשת את פעולות החיבור והשליחה בהתאם לפרוטוקול HTTP. מה מהדברים הבאים אינו מהווה חלק מתהליך הבדיקה של עמידה בעקרון Liskov Substitution ?Principle (LSP)

### Options
- הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות HTTP מוגדר כסוג של חיבור רשת.
- וידוא שפונקציית ה-sendData של HttpClient מסוגלת להתמודד עם כל המידע שמחלקת NetworkConnection יכולה לשלוח.
- הרצת סדרת בדיקות על מופע NetworkConnection ולוודא שהתנהגותן נשמרת גם על מופע HttpClient כולל התייחסות לפלטים ותופעות לוואי.
- יש שתי תשובות אחרות נכונות.

## Answer
עיקרון ההחלפה של ליסקוב (LSP) עוסק בתת-טיפוס התנהגותי: אם S הוא תת-טיפוס של T, אז אובייקטים מטיפוס T ניתנים להחלפה באובייקטים מטיפוס S מבלי לשנות את התכונות הרצויות של התוכנית. 'הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות HTTP מוגדר כסוג של חיבור רשת' אינה חלק מתהליך הבדיקה של LSP. LSP דורש אימות באמצעות בדיקות קפדניות (למשל, לוודא שתנאי קדם לא מתחזקים, תנאי בתר לא נחלשים, אינווריאנטים נשמרים, ומתודות מתנהגות כמצופה כאשר תת-טיפוס מוחלף בטיפוס הבסיס). ההנחה הזו היא סמנטית-תיאורית ולא בדיקה התנהגותית.
