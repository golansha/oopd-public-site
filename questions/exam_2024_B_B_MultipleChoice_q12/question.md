---
id: exam_2024_B_B_MultipleChoice_q12
title: LSP Violation in CodeGenerator
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- SOLID - LSP
skills: []
---

## Question
הפונקציה `generate` במחלקת `CodeGenerator` של תוכנת ה `AI` החדשה "ProgrammerAI"י, מקבלת תיאור של אלגוריתם בתחום של עיבוד תמונה, ובתגובה מחזירה קוד שמממש את האלגוריתם בשפת ג'אווה.
יצרנו תת מחלקה של `CodeGenerator`. איזה מימוש של פונקציית `generate` שלה מפר את - `Liskov Substitution Principle (LSP)`?

### Options
- שתים מהתשובות האחרות נכונות.
- מקבלת כפרמטר תיאור של אלגוריתם בתחום של עיבוד תמונה או טקסט, ומחזירה קוד שמממש את האלגוריתם בשפת ג'אווה או פייתון (לפי מה שנראה לתוכנה מתאים יותר)
- מקבלת כפרמטר תיאור של אלגוריתם בתחום של עיבוד תמונה, ומחזירה קוד שמממש את האלגוריתם בשפת ג'אווה או פייתון (לפי מה שנראה לתוכנה מתאים יותר)
- מקבלת כפרמטר תיאור של אלגוריתם בתחום של עיבוד תמונה או טקסט, ומחזירה קוד שמממש את האלגוריתם בשפת ג'אווה.

## Answer
The Liskov Substitution Principle (LSP) states that objects of a superclass should be replaceable with objects of its subclasses without breaking the application. If the original `generate` method expects a description of an image processing algorithm and returns Java code, a subclass method that accepts *either* image processing *or text* algorithms, or returns *either* Java *or Python* code, violates LSP. This is because the subclass is changing the expected input types (widening) or output types (widening) in a way that a client expecting the superclass behavior might not handle correctly. The options that broaden the input (image or text) or output (Java or Python) types are violations. Since two options describe this, the correct answer is 'שתים מהתשובות האחרות נכונות.' (Two of the other answers are correct).
