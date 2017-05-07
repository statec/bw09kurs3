---
title       : Einheit 3 - inclass
description : Insert the chapter description here

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:a89b75f3c5
## 1. if-Abfragen
Gegeben ist der vollgende Code:

`a <- 1`

`if(FALSE) {sqrt(-4)} else {a <- 3}`

*** =instructions
- a ist 1
- a ist 3
- a ist nicht definiert

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig! Die if Bedingung wird nicht erfüllt, somit wird der else-Teil ausgeführt."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad))

```
