---
id: exam_2024_B_B_MultipleChoice_q15
title: Stream Intermediate Operations Count
year: 2024
semester: B
moed: B
type: Multiple Choice
language: Hebrew
topics:
- Generic - Streams
skills: []
---

## Question
נתון הקוד הבא:
```java
Map<String, Integer> wordsHistorgram = books.stream()
.flatMap(b->b.stream())
.map(s -> s.toLowerCase())
.collect(groupingBy(identity()))
.entrySet().stream()
.collect(toMap(e->e.getKey(), e -> e.getValue().size())));
```
כמה פעולות ביניים של `Stream` יש בסך הכל בקוד הנ"ל?

### Options
- 2
- 3
- 4
- 5

## Answer
Let's break down the stream operations: 1. `books.stream()`: Source. 2. `.flatMap(b->b.stream())`: Intermediate operation. 3. `.map(s -> s.toLowerCase())`: Intermediate operation. 4. `.collect(groupingBy(identity()))`: Terminal operation (creates a `Map`). 5. `.entrySet().stream()`: Source (creates a new stream from the map's entry set). 6. `.collect(toMap(e->e.getKey(), e -> e.getValue().size()))`: Terminal operation. So, in the first stream pipeline, there are 2 intermediate operations (`flatMap` and `map`). In the second stream pipeline, there are no intermediate operations before the terminal `collect`. Therefore, the total number of intermediate operations is 2.
