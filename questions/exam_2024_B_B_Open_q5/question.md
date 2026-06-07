---
id: exam_2024_B_B_Open_q5
title: Strategy Pattern for News Retrieval
year: 2024
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Design patterns - General
- WMS - Strategy
skills: []
---

## Question
סעיף ב (10 נקודות)
יש דרכים שונות להשיג ידיעות שמהן מופקות החדשות בכל נושא. הניחו כי הפונקציה `getNews` מקבלת מחרוזת ומחזירה קבוצה של מחרוזות. לדוגמא יש אפשרות שהמימוש של `getNews` יהיה מבוסס על ביצוע ראיון (`interview`) ויש אפשרות אחרת שהמימוש יהיה מבוסס על קבלת ידיעות מסוכנות ידיעות בינלאומיות (`agency`). בחלק מהנושאים נרצה לממש התנהגות המבוססת על שתיים או יותר דרכים להשגת ידיעות. דוגמא אחת היא להפעיל שתי דרכים ואיחוד של התוצאות. דוגמא אחרת היא להפעיל את שתי הדרכים ולהשאיר רק מה שמופיע בתוצאה של הפעלת הדרך הראשונה אבל לא בתוצאה של הדרך השניה (כלומר חיסור התוצאות). ייתכנו דרכים נוספות להשיג ידיעות ואפשרויות שונות לייצר ידיעות בהתבסס על דרכים בסיסיות.
השתמש בתבניות עיצוב שנלמדו בכיתה על מנת לממש את המערכת המתוארת על פי הדרישות. צייר תרשים מחלקות המבוסס על תבניות עיצוב שלמדת שתומך בדרישות. כתוב את שם תבניות העיצוב שהשתמשת בהן. כתוב את הקוד עבור המחלקות שציירת. אין צורך לממש את הדרכים הקונקרטיות (ראיון וסוכנות), אך יש צורך לממש את הדרכים הנגזרות מהן (איחוד וחיסור שלהן)
כאן יש לענות רק על שאלה 4ב (אם כתבת בטעות את פתרון שאלה 4ב במקום אחר, ציין זאת כאן במפורש)
תשובה : תבנית עיצוב Strategy
![Image](image_10_1.png)
```java
public class Subject extends Observable{
Strategy strategy;
public void setStrategy(Strategy strategy){
this.strategy = strategy;
}
public Set<String> getNews(String s){
return strategy.getNews(s);
}
}
public interface Strategy {
public abstract Set<String> getNews(String s);
}
public class UnionStrategy implements Strategy{
Strategy strategy1;
Strategy strategy2;
public UnionStrategy(Strategy strategy1, Strategy strategy2) {
this.strategy1 = strategy1;
this.strategy2 = strategy2;
}
@Override
public Set<String> getNews(String s) {
Set<String> set = new HashSet<>();
set.addAll(strategy1.getNews(s));
set.addAll(strategy2.getNews(s));
return set;
}
}
public class SubtractionStrategy implements Strategy{
Strategy strategy1;
Strategy strategy2;
public SubtractionStrategy(Strategy strategy1, Strategy strategy2) {
this.strategy1 = strategy1;
this.strategy2 = strategy2;
}
@Override
public Set<String> getNews(String s) {
Set<String> set1 = strategy1.getNews(s);
Set<String> set2 = strategy2.getNews(s);
return set1.stream()
.filter(e -> set2.contains(e))
.collect(Collectors.toSet());
}
}
```

## Answer
The Strategy pattern is used here. The `Subject` class has a `Strategy` object, which can be set dynamically. Different concrete `Strategy` implementations (like `Interview`, `Agency`, `UnionStrategy`, `SubtractionStrategy`) provide different ways to retrieve news. `UnionStrategy` combines results from two strategies, and `SubtractionStrategy` filters results based on another strategy. This allows the `Subject` to vary its news retrieval algorithm independently from clients that use it.

```java
public class Subject extends Observable{
Strategy strategy;
public void setStrategy(Strategy strategy){
this.strategy = strategy;
}
public Set<String> getNews(String s){
return strategy.getNews(s);
}
}
public interface Strategy {
public abstract Set<String> getNews(String s);
}
public class UnionStrategy implements Strategy{
Strategy strategy1;
Strategy strategy2;
public UnionStrategy(Strategy strategy1, Strategy strategy2) {
this.strategy1 = strategy1;
this.strategy2 = strategy2;
}
@Override
public Set<String> getNews(String s) {
Set<String> set = new HashSet<>();
set.addAll(strategy1.getNews(s));
set.addAll(strategy2.getNews(s));
return set;
}
}
public class SubtractionStrategy implements Strategy{
Strategy strategy1;
Strategy strategy2;
public SubtractionStrategy(Strategy strategy1, Strategy strategy2) {
this.strategy1 = strategy1;
this.strategy2 = strategy2;
}
@Override
public Set<String> getNews(String s) {
Set<String> set1 = strategy1.getNews(s);
Set<String> set2 = strategy2.getNews(s);
return set1.stream()
.filter(e -> !set2.contains(e)) // Corrected to remove elements present in set2
.collect(Collectors.toSet());
}
}
```
