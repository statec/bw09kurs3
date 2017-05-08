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

--- type:NormalExercise lang:r xp:100 skills:1 key:a545b07906
## 2. if-Abfrage
Gegeben ist ihnen im Beispielcode eine if-Abfrage. Führen Sie diese aus.

Tipp: Wenn Sie bestimmte Codeabschnitte, also mehrere Zeilen auf einmal, in der Konsole ausführen möchten, markieren Sie den gewünschten Codeabschnitt und drücken Sie gleichzeitig `Strg` und `Enter`.


*** =instructions
- Führen Sie die if-Abfrage aus und geben Sie a in der Konsole aus.
- Ändern Sie anschließend die Bedingung von "FALSE" auf "TRUE" und führen Sie die Abfrage erneut aus. 
- Schauen Sie sich wieder a in der Konsole an.


*** =hint

*** =pre_exercise_code
```{r}
text_if <- "ich bin in der if-Abfrage enstanden"
text_else <- "ich bin in dem else-Teil entstanden"

```

*** =sample_code
```{r}
# Führe die Abfrage durch und gebe a in der Konsole aus.
if(FALSE){
    a <- text_if} else { a<- text_else }
a
# Ändere Bedingung zu TRUE und geben erneut a aus.
if(___){
    a <- text_if} else { a<- text_else }
a
```

*** =solution
```{r}
# Führe if-Abfrage aus und gebe a aus.
if(FALSE){
    a <- text_if} else { a<- text_else }
print(a)

# Ändere Bedingung zu TRUE und geben erneut a aus.
if(TRUE){
    a <- text_if} else { a<- text_else }
print(a)


```

*** =sct
```{r}
test_output_contains("text_if")
test_output_contains("text_else")
test_error()

```
