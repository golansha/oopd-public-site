---
id: exam_2024_B_B_Open_q2
title: AOP Aspect Counting
year: 2024
semester: B
moed: B
type: Open
language: Hebrew
topics:
- Frameworks - AOP
skills: []
---

## Question
ישנה פונקציה בשם `call_to_sod` (המוגדרת בחבילה `PkgA` ויש לה פרמטר יחיד מטיפוס `String`) שבתוך הקוד שלה קוראת מספר פעמים לפונקציה אחרת – הפונקציה `sod` (המוגדרת גם היא בחבילה הנ"ל, ויש לה פרמטר יחיד מטיפוס `Integer`). רוצים שבסיום הפעלת הפונקציה `call_to_sod` יודפס על המסך מספר הפעמים (בסך הכל) שהפונקציה `sod` הופעלה.
אסור לשנות/להוסיף דבר בתוך הפונקציות הנ"ל או במחלקות שבהן הן מוגדרות, ולכן נכתוב Aspect.
עליכם להשלים את כתיבת ה Aspect : יש להוסיף Pointcut אחד או יותר ו- Advice אחד או יותר.
מותר להוסיף דברים נוספים במחלקת ה Aspect
```java
Public Aspect Counting{
}
```

## Answer
```java
Public Aspect Counting {
int counter;
@Pointcut("execution(* PkgA.*.call_to_sod(String))")
private void selectCallToSod() {
}
@Pointcut("execution(* PkgA.*.sod(Integer))")
private void selectSod() {
}
@Before("selectCallToSod()")
public void beforeAdvice(JoinPoint jp) {
counter=0;
}
@After("selectCallToSod()")
public void afterAdvice(JoinPoint jp) {
System.out.println(counter);
}
@Before("selectSod()")
public void beforeSod(JoinPoint jp) {
counter++;
}
}
```
ניתן להשתמש גם ב Around
```java
@Around("selectCallToSod()")
public void aroundAdvice(ProceedingJoinPoint pjp) throws Throwable {
counter=0;
pjp.proceed(pjp.getArgs());
System.out.println(counter);
}
```
