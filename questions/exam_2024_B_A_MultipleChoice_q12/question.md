---
id: exam_2024_B_A_MultipleChoice_q12
title: מורכבות תבניות עיצוב
year: 2024
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- Design patterns - General
skills: []
---

## Question
סדר את תבניות העיצוב על פי מורכבות מבנה האובייקטים שהן מייצגות (משמאל לימין, מהמורכב לפשוט)

### Options
- Composite, Decorator, Proxy
- Composite, Proxy, Decorator
- Decorator, Composite, Proxy
- Decorator, Proxy, Composite

## Answer
האפשרות הנכונה היא "Composite, Decorator, Proxy". סדר המורכבות של תבניות אלו, מהמורכבת לפשוטה, הוא:
1.  **Composite (מבנה מורכב):** מאפשר לטפל באובייקטים בודדים ובקומפוזיציות של אובייקטים באופן אחיד. הוא כולל ממשק משותף, אובייקטי עלה (Leaf) ואובייקטים מורכבים (Composite) שיכולים להכיל ילדים, מה שיוצר מבנה רקורסיבי.
2.  **Decorator (עטיפה עם הרחבה):** מוסיף אחריות חדשות לאובייקט באופן דינמי. הוא כולל רכיב (Component), רכיב קונקרטי, Decorator אבסטרקטי ו-Decorators קונקרטיים. הוא עוטף אובייקטים קיימים כדי להוסיף להם פונקציונליות.
3.  **Proxy (עטיפה עם בקרת גישה):** מספק תחליף או מציין מיקום לאובייקט אחר כדי לשלוט בגישה אליו. הוא כולל ממשק Subject, Real Subject ו-Proxy. הוא עטיפה פשוטה יותר מ-Decorator, המשמשת בעיקר לבקרת גישה, טעינה עצלה וכדומה.
