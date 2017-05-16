---
title       : Einheit 3 - homework
description : If Abfragen, Schleifen und Funktionen

--- type:NormalExercise lang:r xp:100 skills:1 key:e390410b37
## 1. if Abfragen
In `wurf` und `wurf2` sind die Ergebnisse eines Würfelwurfes gespeichert. Bei einer Zahl die echt größer als 1 und echt kleiner als 5 ist, gewinnt man. 


*** =instructions
- Schreiben Sie eine if Abfrage, der die Variable `gewonnen` im Fall eines Sieges auf TRUE und sonst auf FALSE setzt. 
*** =hint
- if(Bedingung1 & Bedingung2){do something}else{do something else}

*** =pre_exercise_code
```{r}
wurf <- 3

```

*** =sample_code
```{r}
# Fragen Sie in einer if-Abfrage ab, ob der wurf gewonnen oder verloren hat und setzen Sie das ergebnis dementsprechend
if(wurf > 1 & wurf <5){
    gewonnen <- TRUE}else {
    gewonnen <- FALSE
    }


```

*** =solution
```{r}
# Fragen Sie in einer if-Abfrage ab, ob der wurf gewonnen oder verloren hat und setzen Sie das ergebnis dementsprechend
if(wurf > 1 & wurf <5){
    gewonnen <- TRUE}else {
    gewonnen <- FALSE
    }


```

*** =sct
```{r}
test_object("gewonnen")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:027490dfc9
## 2. for-Schleife
Gegeben ist ein Vektor `v`. Sie sollen mit Hilfe einer for-Schleife einen Vektor `r` erstellen, der die Elemente von v in umgekehrter Reihenfolge enthält. Der leere Vektor r existiert bereits.

Der Aufbau einer for Schleife:


- `for(Bedingung){Führe das aus}`.

*** =instructions
- Erstellen Sie in einer for Schleife einen Vektor r, welcher die Elemente von v in umgekehrter Reihenfolge enthält.
- Denken Sie daran, dass sie die Funktion `length(vector)` benutzen können, um die Länge eines Vektors zu erhalten.


*** =hint
- Mit `vektor[i]` bekommt man den i-ten Wert des Vektors.
- Lassen Sie innerhalb der Schleife eine Variable runter zählen.

*** =pre_exercise_code
```{r}
v <- c(2,4,6,8,9,11,23,33,45,46,47,48)
r <- c()

```

*** =sample_code
```{r}
# Erstellen Sie die Zählvariable i = 1

# Erstellen Sie Zählvariable j und setzen Sie sie auf die Länge von v

# for Schleife 

  
```

*** =solution
```{r}
# Erstellen Sie die Zählvariable i = 1
i <- 1
# Erstellen Sie Zählvariable j und setzen Sie sie auf die Länge von v
j <- length(v)
# for Schleife die r erstellt
for(i in 1:length(v)){
  r[i] <- v[j]
  j <- j-1}

```

*** =sct
```{r}
test_object("r")
test_error()
```
