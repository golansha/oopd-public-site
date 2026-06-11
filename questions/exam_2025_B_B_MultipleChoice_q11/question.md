---
id: exam_2025_B_B_MultipleChoice_q11
title: LSP Verification
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- SOLID - LSP
skills: []
---

## Question
מחלקת `NetworkConnection` מממשת ממשק כללי לניהול חיבורי רשת ושליחת נתונים. מחלקת `HttpConnection` יורשת ממחלקת `NetworkConnection` ומממשת את פעולות החיבור והשליחה בהתאם לפרוטוקול HTTP.
מה מהדברים הבאים אינו מהווה חלק מתהליך הבדיקה של עמידה בעקרון `Liskov Substitution Principle (LSP)`?

### Options
- הנחה שהירושה תקינה משום שבמושגים מעולם הרשתות `HTTP` מוגדר כסוג של חיבור רשת.
- וידוא שפונקציית ה-`sendData` של `HttpClient` מסוגלת להתמודד עם כל המידע שמחלקת `NetworkConnection` יכולה לשלוח.
- הרצת סדרת בדיקות על מופע `NetworkConnection` ולוודא שהתנהגותן נשמרת גם על מופע `HttpClient`, כולל התייחסות לפלטים ותופעות לוואי.
- יש שתי תשובות אחרות נכונות.

## Answer
LSP is about behavioral subtyping, meaning that objects of a superclass should be replaceable with objects of a subclass without breaking the application. Assuming inheritance is valid based on conceptual definitions (like 'HTTP is a type of network connection') without verifying behavioral compatibility is not part of LSP verification. The other options describe actual behavioral checks.
