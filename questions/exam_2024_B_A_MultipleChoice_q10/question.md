---
id: exam_2024_B_A_MultipleChoice_q10
title: Pointcut ב-AOP
year: 2024
semester: B
moed: A
type: Multiple Choice
language: Hebrew
topics:
- Frameworks - AOP
skills: []
---

## Question
נתון `aspect` שמפעיל `advice` עבור כל פונקציה שמקבלת `String` ו-`long` ומסומנת באנוטציה `Operate`.
באיזה אופן אפשר לכתוב את ה `pointcut` המתאים

### Options
- @Pointcut("execution(* *.*(String, long))") private void f(){ } @Pointcut("@annotation(Operate)") private void g(){ } @Pointcut("f() && g()") private void both() { }
- @Pointcut("execution(* *.*(String))") private void f1(){ } @Pointcut("execution(* *.*(long))") private void f2(){} @Pointcut("@annotation(Operate)") private void g(){} @Pointcut("f1() && f2() && g()") private void both() { }
- @Pointcut("execution(* *.*(String))") private void f1(){ } @Pointcut("execution(* *.*(long))") private void f2(){} @Pointcut("@annotation(Operate)") private void g(){} @Pointcut("f1() || f2() || g()") private void both(){ }
- @Pointcut("execution(* *.*(String, long))") private void f(){ } @Pointcut("@annotation(Operate)") private void g(){} @Pointcut("f() || g()") private void both() { }

## Answer
האפשרות הנכונה היא הראשונה. כדי להתאים לפונקציות שמקבלות `String` ו-`long` *וגם* מסומנות באנוטציה `Operate`, יש צורך לשלב שני `pointcuts` באמצעות אופרטור `&&` (AND):
1.  `@Pointcut("execution(* *.*(String, long))") private void f(){ }` מגדיר `pointcut` שיתאים לכל פונקציה שמקבלת בדיוק `String` ואחריו `long`.
2.  `@Pointcut("@annotation(Operate)") private void g(){ }` מגדיר `pointcut` שיתאים לכל פונקציה המסומנת באנוטציה `Operate`.
3.  `@Pointcut("f() && g()") private void both() { }` משלב את שני ה-`pointcuts` כך שיתאימו רק לפונקציות שמקיימות את שני התנאים יחד.
