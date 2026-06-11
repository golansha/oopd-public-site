---
id: exam_2025_B_B_MultipleChoice_q14
title: Dependency Injection Definition
year: 2025
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Frameworks - Dependency injection
skills: []
---

## Question
`Dependency Injection` - "הזרקת תלויות"
סמן מהמשפטים הבאים את הנכון ביותר:

### Options
- `Dependency Injection` הוא שיטה מובנית לאתחול אובייקטים המזריקה עבורם את השדות שהם תלויים בהם.
- ישנן שתי תשובות אחרות נכונות.
- כדי להזריק תלויות באמצעות `Dependency Injection`, השדות המוזרקים חייבים להיות מוגדרות כממשקים.
- אם מזריקים למחלקה שדה מסוג ממשק, שאותו מממשות כמה מחלקות, יש דו משמעות ולא ניתן להגדיר מאיזה מחלקה יהיה האובייקט שיוזרק.

## Answer
Dependency Injection is a technique where an object receives its dependencies from an external source rather than creating them itself. This external source (injector) is responsible for instantiating and providing the required dependencies, often through constructors, setter methods, or field injection. The other options contain inaccuracies: dependencies don't *have* to be interfaces (though it's good practice), and DI frameworks handle ambiguity when multiple implementations exist (e.g., by naming or primary annotations).
