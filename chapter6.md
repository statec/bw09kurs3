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
- Führen Sie die if-Abfrage aus und geben Sie `a` in der Konsole aus.
- Ändern Sie anschließend die Bedingung von "FALSE" auf "TRUE" und führen Sie die Abfrage erneut aus. 
- Schauen Sie sich wieder `a` in der Konsole an.


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
# Ausgabe
a

# Ändere Bedingung zu TRUE und geben erneut a aus.
if(___){
    a <- text_if} else { a<- text_else }
# Ausgabe
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

--- type:NormalExercise lang:r xp:100 skills:1 key:fe02cb131f
## 3. if-Bedingung
Ihnen ist wieder eine if-Abfrage gegeben, nur die Bedingung fehlt. 

Wenn die Variable `note` kleiner oder gleich 4 ist, soll ausgegeben werden "Die Prüfung ist bestanden", sonst soll ausgegeben werden "Die Prüfung muss wiederholt werden"

*** =instructions
- setzen Sie die Bedingung für die if-Abfrage.
- Füllen Sie die Lücken im Code, indem Sie die jewilige Ausgabe in `print("___")` einfügen.

*** =hint
- Für die Vergleichsoperatoren schauen Sie in die Vorlesung.
- 

*** =pre_exercise_code
```{r}
note = 3
success = "Die Prüfung ist bestanden"
```

*** =sample_code
```{r}
# Abfrage der Note
if(note ___){
    print("___")}else{print("___")}

```

*** =solution
```{r}
# Abfrage
if(note <= 4){
    print("Die Prüfung ist bestanden")}else{print("Die Prüfung muss wiederholt werden")}

```

*** =sct
```{r}
test_output_contains("success")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:9dcf2f1327
## 4. if-Abfrage selber schreiben
Nun sollen Sie ihre erste eigene if-Abfrage schreiben. Gegeben sind die Variablen a und b. Die Variable c soll die Differenz von a und b sein. Da c keine negative Zahl werden soll, muss vorher getestet werden, ob a oder b größer ist.

Schauen Sie in die Vorlesung oder in den "Hint" um zu sehen, wie das Gerüst aufgebaut ist.


*** =instructions
- Schreiben Sie eine if-Abfrage, die abfragt ob `a` kleiner gleich `b` ist.
- Wenn das der Fall ist, setzen Sie `c` auf `b-a`.
- Falls nicht, greift der else-Teil: dann soll c = a-b sein.

*** =hint
- `if(Bedingung){c <- ___}else{c <- ___}`

*** =pre_exercise_code
```{r}
a = 2
b = 5
```

*** =sample_code
```{r}
# schreiben Sie eine if-Abfrage

    
# Geben Sie das Ergebnis c aus.

```

*** =solution
```{r}
# schreiben Sie eine if-Abfrage
if(a <= b){
    c <- b-a} else{ c <- a-b }
    
# Geben Sie das Ergebnis c aus.
c
```

*** =sct
```{r}
test_output_contains("c")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:4cc9a15a6f
## 5. if Abfrage
Gegeben ist ihnen eine Variable `a`. Wenn `a` ungleich null ist, dann soll eine Zahl `b` durch `a` geteilt werden. 


*** =instructions
- Schreiben Sie eine if-Abfrage die TRUE ist, wenn `a` ungleich Null ist.
- Wenn das der Fall ist, soll `b` durch `a` geteilt werden.

*** =hint
- `if(Bedingung){___}`
*** =pre_exercise_code
```{r}
a <- 2
b <- 10
c <- b/a

```

*** =sample_code
```{r}
# Falls a nicht gleich 0, soll b durch a gerechnet werden.


```

*** =solution
```{r}
# Falls a nicht gleich 0, soll b/a gerechnet werden.
if(a != 0){
    b/a} 

```

*** =sct
```{r}
test_output_contains("c")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:4ed9623928
## 6. for-Schleife
Gegeben ist ihnen ein Vektor `fib`. Sie sollen nun mit Hilfe einer for-Schleife einen Vektor Summe erstellen, der jeweils aus der Summe zweier im Vektor benachbarter Zahlen steht. 

Tipp: der erste Wert in Summe `summe[1]` soll gleich 2 sein, da `fib[1]+fib[2]` 1+1 = 2 ergibt. 

*** =instructions
- Setzen Sie die Indexvariable.
- Erstellen Sie den Vektor `summe`.

*** =hint

*** =pre_exercise_code
```{r}
fib <- c(1,1,2,3,5,8,13,21)
summe <- c()
```

*** =sample_code
```{r}
# Berechnen Sie den Verktor "summe" in einer for-Schleife.
for(___ in 2:8){
    summe[___] <- ___ + ___}
# Geben Sie "summe" in der Konsole aus.


```

*** =solution
```{r}
# Berechnen Sie den Verktor "summe" in einer for-Schleife.
for(i in 2:8){
    summe[i-1] <- fib[i] + fib[i-1]}
# Geben Sie "summe" in der Konsole aus.
summe

```

*** =sct
```{r}
test_output_contains("summe")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:6e2eab47f2
## 7. While-Schleife
Hier sehen Sie eine While-Schleife, die die Fakultät von `zahl` berechnet. Füllen Sie die Lücken im vorgegebenen Code.

Tipp:
- Denken Sie daran - um einen Teil des Codes auszuprobieren, können Sie diesen Teil markieren und gleichzeitig `Strg` und `Enter` betätigen.

*** =instructions
- Ergänzen Sie den Code so, dass in der whileschleife die Fakultät der `zahl` berechnet wird und in `fak` gespeichert wird.

*** =hint
- Die Fakultät berechnet sich bsp. für 4! = 1\*2\*3*4 

*** =pre_exercise_code
```{r}
ergebnis <- 120

```

*** =sample_code
```{r}
# Testen Sie ihre Schleife mit der Zahl 5
i <- 1
zahl <- ___
fak <- 1
# while 
while(i <= ___){
  fak <- ___*___
  i <- ___
}
# Ergebnis Ausgabe
print(fak)


```

*** =solution
```{r}
# Testen Sie ihre Schleife mit der Zahl 5
i <- 1
zahl <- 5
fak <- 1
# while 
while(i <= zahl){
  fak <- fak * i
  i <- i+1
}
print(fak)

```

*** =sct
```{r}
test_output_contains("ergebnis")
test_error()

```
