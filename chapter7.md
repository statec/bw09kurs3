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

--- type:NormalExercise lang:r xp:100 skills:1 key:4973089211
## 3. Ganzzahlige Division
Sie sollen nun mit Hilfe einer while Schleife berechnen, wie oft die Zahl 5 in eine andere gegebene Zahl `zahl` passt, und welcher Rest übrig bleibt. Sie dürfen von Natürlichen Zahlen (0 inklusive) ausgehen.


*** =instructions
- Ziehen Sie innerhalb der while-Schleife immer 5 von der Zahl ab.
- Setzen Sie anschließend den Zähler `x` eins hoch.
- Überlegen Sie, bis wohin die while Schleife sinnvollerweise gehen sollte, damit `zahl` niemals negativ wird. 
- In Zahl soll am Ende der Rest stehen, der aus der ganzzahligen Division übrig geblieben ist.

*** =hint

*** =pre_exercise_code
```{r}
# zahl setzen
zahl <- 63
```

*** =sample_code
```{r}
# Zähler auf Null setzen
x <- 0
# Schleife 

# Ausgabe von x und zahl
x
zahl

```

*** =solution
```{r}
# Zähler setzen
x <- 0
# Schleife
while(zahl >= 5){
  zahl <- zahl - 5
  x <- x + 1
}
# Ausgabe
x
zahl

```

*** =sct
```{r}
test_object("zahl")
test_object("x")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:a7e56ceac1
## Moving Average
In den Übungen haben Sie bereits eine Funktion geschrieben, welche den gleitenden x-er Durchschnitt berechnet. Sie durften jedoch davon ausgehen, dass x eine ungerade natürliche Zahl war. Nun Soll x zwar eine natürliche Zahl sein, aber auch gerade Zahlen sollen akzeptiert werden. 
Wenn x gerade ist, sollen Sie erst x in eine ungerade Zahl umwandeln indem Sie x auf x+1 setzen.

Tipp: Benutzen Sie den Modulo-Operator `%%` um zu überprüfen, ob x gerade ist. Dieser zeigt den Rest einer Ganzzahligen Division an.

- Bsp: 7 %% 2 = 1 oder 4 %% 2 = 0

*** =instructions
- Schreiben Sie eine Funktion `gleitender_durchschnitt`, die als Eingabe einen Vektor `zeitreihe` und einen Wert `x` erwartet.
- Zuerst soll die Funktion prüfen, ob x gerade oder ungerade ist, und x gegebenenfalls ungerade machen. Nutzen Sie hierzu eine if-Abfrage.
- Die Funktion soll den gleitenden x-er Durchschnitt berechnen. Sie können sich hier weitestgehend an der Funktion aus der Vorlesung orientieren.
- Sie gibt am Ende ein `ergebnis` zurück.
- Testen Sie ihre Funktion an dem gegebenen Vektor `reihe`.

*** =hint
- Die Struktur einer Funktion: 
- `neue_funktion <- function(Eingabeparameter){...working ...return (Ausgabeparameter)}`
- Berechnen Sie zuerst den Abstand nach links und rechts in der Zeitreihe und speichern Sie diesen in einer neuen Variable in der Funktion.
- Bedenken Sie, dass z.B. der gleitende 9-er Durchschnitt für die ersten und letzten 4 Zahlen nicht berechnet werden kann.

*** =pre_exercise_code
```{r}
reihe <- c(11, 12, 13, 16, 18, 20, 33, 66, 54, 67, 89, 102, 133, 150, 120, 110, 60, 78, 90, 101, 50, 37, 21, 2)
xyz <- c(11.00000,  12.00000,  13.00000,  17.57143,  25.42857,  31.42857,  39.14286,  49.57143,  61.57143,  77.71429,  94.42857, 102.14286, 110.14286, 109.14286,
 107.57143, 105.85714, 101.28571,  87.00000,  75.14286,  62.42857,  50.00000,  37.00000,  21.00000,   2.00000)



```

*** =sample_code
```{r}
# Funktion Berechnung gleitender Durchschnitt








# Testen Sie ihre Funktion an reihe mit x = 6 und x = 7
gleitender_durchschnitt(reihe, 6)
gleitender_durchschnitt(reihe, 7)


```

*** =solution
```{r}
# Funktion Berechnung gleitender Durchschnitt
gleitender_durchschnitt <- function(zeitreihe, x){
    laenge <- length(zeitreihe)
    ergebnis <- c()
    if(x %% 2 == 0){ x <- x + 1 }
    # Berechnung des Abstandes nach links und rechts
    n <- (x-1)/2
    for(i in 1:laenge){
        # Darf nicht für die ersten n Zahlen berechnet werden
        if( i <= n | i >= (laenge-n)){
            ergebnis[i] <- zeitreihe[i]
        }else{
            ergebnis[i] <- mean( zeitreihe [(i - n) : (i + n)])
        }
    }
    return(ergebnis)
}
# Test an reihe mit x = 6 und x = 7
gleitender_durchschnitt(reihe, 6)
gleitender_durchschnitt(reihe, 7)

```

*** =sct
```{r}
test_output_contains("xyz")
test_error()


```