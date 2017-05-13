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
# Falls a ungleich 0, soll b/a gerechnet werden.
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
Hier sehen Sie eine while-Schleife, die die Fakultät von `zahl` berechnet. Füllen Sie die Lücken im vorgegebenen Code.

Tipp:

- Denken Sie daran - um einen Teil des Codes auszuprobieren, können Sie diesen Teil markieren und gleichzeitig `Strg` und `Enter` betätigen.
- Denken Sie dran, dass keine Endlosschleifen entstehen dürfen.

*** =instructions
- Ergänzen Sie den Code so, dass in der while-Schleife die Fakultät der `zahl` berechnet wird und in `fak` gespeichert wird.

*** =hint
- Die Fakultät berechnet sich bsp. für 4! = 1\*2\*3*4 
- Um die while-Schleife auf jeden Fall terminieren zu lassen, muss sichergestellt werden, dass die Zählvariable `i` in der while-Schleife um eins erhöht wird.

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
# while Schleife zur Fakultätsberechnung
while(i <= ___){
  fak <- ___*i
  i <- ___
}
# Ergebnis Ausgabe
print(fak)


```

*** =solution
```{r}
# Initialisierung der Werte
i <- 1
zahl <- 5
fak <- 1
# Fakultätsberechnung
while(i <= zahl){
  fak <- fak * i
  i <- i+1
}
# Ausgabe des Ergebnisses
print(fak)

```

*** =sct
```{r}
test_output_contains("ergebnis")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:bc6c49a486
## 8. Funktionen
In den Folien haben Sie gesehen, wie man den Absolutwert einer Zahl berechnen kann. Um eine solche Abfrage immer wieder nutzen zu können, ist es sinnvoll, Sie in eine Funktion einzubetten.

Funktionen haben Eingabeparameter und Ausgabeparameter. Als Eingabe soll ein beliebiger `wert` gelesen werden, die Ausgabe soll den Absolutbetrag `absolut_wert` zurück geben.


*** =instructions
- Erstellen Sie eine Funktion `absolut()` mit Eingabeparameter `wert`.
- Die Funktion fragt über eine if-Abfrage ab, ob der Wert negativ ist oder nicht und wandelt ihn zu einer positiven Zahl um (dieser Teil kann vollständig aus den Folien übernommen werden).
- Sie gibt den berechneten `absolut_wert` zurück.
- Testen Sie ihre Funktion an mehreren Beispielen.

*** =hint
- Die Struktur einer Funktion: 
- `neue_funktion <- function(Eingabeparameter){...working ...return (Ausgabeparameter)}`

*** =pre_exercise_code
```{r}
wert1 <- -10
ergebnis <- 10
```

*** =sample_code
```{r}
# Erstellung der Funktion
absolut <- function(wert){
    if(wert<0){
        absolut_wert <- -wert
    }else {
        absolut_wert <- wert
    }
    return(absolut_wert)
}
# Testen Sie ihre Funktion aus, in dem Sie z.B. absolut(-4) testen.
absolut(-4)
# Testen Sie ihre Funktion für "wert1"

```

*** =solution
```{r}
# Erstellung der Funktion
absolut <- function(wert){
    if(wert<0){
        absolut_wert <- -wert
    }else {
        absolut_wert <- wert
    }
    return(absolut_wert)
}
# Testen Sie ihre Funktion aus, in dem Sie z.B. absolut(-4) testen.
absolut(-4)
# Testen Sie ihre Funktion für "wert1"
absolut(wert1)

```

*** =sct
```{r}
test_output_contains("ergebnis")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:c45d01f88e
## 9. Moving Average
In den Folien haben Sie gesehen, wie eine Funktion für den gleitenden 5-er Durchschnitt aussieht. In dieser Aufgabe sollen Sie eine Funktion schreiben, die den gleitenden x-er Durchschnitt für eine beliebige ungerade Zahl x berechnet und zurück gibt. Als Eingabe soll diese Funktion einen vektor `zahlenreihe` und einen Wert `x` erhalten. Es soll davon ausgegangen werden, dass x ein natürliche ungerade Zahl ist (muss nicht extra geprüft werden). 


*** =instructions
- Schreiben Sie eine Funktion `gleitender_durchschnitt`, die als Eingabe einen Vektor `zeitreihe` und einen ungeraden Wert `x` erwartet.
- Die Funktion soll den gleitenden x-er Durchschnitt berechnet. Sie können sich hier weitestgehend an der Funktion aus der Vorlesung orientieren.
- Sie gibt am Ende ein `ergebnis` zurück.

*** =hint
- Die Struktur einer Funktion: 
- `neue_funktion <- function(Eingabeparameter){...working ...return (Ausgabeparameter)}`

*** =pre_exercise_code
```{r}
reihe <- c(11, 12, 13, 16, 18, 20, 33, 66, 54, 67, 89, 102, 133, 150, 120, 110, 60, 78, 90, 101, 50, 37, 21, 2)


```

*** =sample_code
```{r}
# Funktion Berechnung gleitender Durchschnitt
gleitender_durchschnitt <- function(zeitreihe, x){
    laenge <- length(zeitreihe)
    ergebnis <- c()
    n <- (x-1)/2
    for(i in 1:laenge){
        if( i <= n | i >= (laenge-n)){
            ergebnis[i] <- zeitreihe[i]
        }else{
            ergebnis[i] <- mean( zeitreihe [(i - n) : (i + n)])
        }
    }
    return(ergebnis)
}
# Testen Sie ihre Funktion an der Zeitreihe "reihe" für x=7

```

*** =solution
```{r}
# Funktion Berechnung gleitender Durchschnitt
gleitender_durchschnitt <- function(zeitreihe, x){
    laenge <- length(zeitreihe)
    ergebnis <- c()
    n <- (x-1)/2
    for(i in 1:laenge){
        if( i <= n | i >= (laenge-n)){
            ergebnis[i] <- zeitreihe[i]
        }else{
            ergebnis[i] <- mean( zeitreihe [(i - n) : (i + n)])
        }
    }
    return(ergebnis)
}
# Test an reihe mit x=7
gleitender_durchschnitt(reihe, 7)


```

*** =sct
```{r}
#test_output_contains("")

```
