---
id: exam_2024_B_B_Open_q4
title: Observer Pattern Initialization
year: 2024
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Design patterns - General
- WMS - Observer
- WMS - אתחול
skills: []
---

## Question
פורטל החדשות "תבנית השבועיי מציע תכנים במגוון רחב של נושאים (Subject). המשתמשים (User) יכולים להרשם לקבלת עדכונים בנושאים שונים. בכל פעם שיש כתבה חדשה בנושא מסויים, כל המשתמשים שנרשמו אליו יקבלו עדכון. כל משתמש מבצע פעולה שונה לאחר קבלת עדכון. ניתן להניח כי קיים כבר מימוש לנושא Subject1 ולמשתמש User1 ואין צורך לממש אותם.
על מנת להקל על המשתמשים לבחור נושאים, הוקמו מועדוני חברים (Club). משתמש יכול להצטרף כחבר למועדון ואף ייתכן שמועדון אחד יצטרף כחבר למועדון אחר. מועדון יכול להירשם לתכנים עבור החברים שהצטרפו אליו. בכל פעם שהמועדון מקבל עדכון הוא מעדכן את החברים שהצטרפו אליו.
על מנת לפשט את תהליך הרישום, הפורטל הגדיר קטגוריות רישום (Category). קטגוריה יכולה להכיל מספר נושאים ואף ייתכן שקטגוריה אחת תכיל קטגוריה אחרת. רישום משתמש לקטגוריה תוביל להוספתו לקבלת עדכונים בכל הנושאים ששייכים אליה באופן ישיר או עקיף.
נתון העיצוב המממש את הדרישות שתוארו לעיל :
![Image](image_8_1.png)
סעיף א (10 נקודות)
כתוב את הקוד שמאתחל את המערכת הבאה :
• קטגוריה בשם 'טכנולוגיה' שמכילה את הנושאים הבאים
Ο קטגוריה בשם 'מחשבים' שמכילה את הנושאים הבאים
נושא מטיפוס 'AI'
נושא מטיפוס 'BI'
ס נושא מטיפוס 'רובוטיקה'
• נושא מטיפוס 'תכנים לילדים'
• מועדון משתמשים בשם Club1 שמכיל את המשתמשים הבאים
Ο מועדון משתמשים מטיפוס Club2 שמכיל את המשתמשים הבאים
משתמש מטיפוס User1
משתמש מטיפוס User2
משתמש מטיפוס User3
מועדון Club1 יירשם לנושא 'תכנים לילדים'
מועדון Club2 יירשם לקטגוריה 'מחשבים'
משתמש User3 יירשם לקטגוריה 'טכנולוגיה'
כאן יש לענות רק על שאלה 4א (אם כתבת בטעות את פתרון שאלה 4א במקום אחר, ציין זאת כאן במפורש)
תשובה:

## Answer
```java
public static void main(String[] args) {
Category computers = new Category();
Category technology = new Category();
// Assuming Children is a Category for 'תכנים לילדים'
Category children = new Category(); 

computers.addICategory(new AI());
computers.addICategory(new BI());
technology.addICategory(new Robotics());
technology.addICategory(computers);

Club club1 = new Club();
Club club2 = new Club();

club1.addObserver(club2);
User user1 = new User(); // Assuming User1, User2, User3 are instances of User
User user2 = new User();
User user3 = new User();

club2.addObserver(user1);
club2.addObserver(user2);
club1.addObserver(user3);

children.addObserver(club1);
computers.addObserver(club2);
technology.addObserver(user3);
}
```
