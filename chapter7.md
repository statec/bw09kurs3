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





--- type:NormalExercise lang:r xp:100 skills:1 key:2312b5b5e8
## 4. Funktion
Schreiben Sie eine Funktion, welche zwei Objekte `a` und `b` als Eingabe erhält. Die Funktion soll als Ausgabe das Produkt der beiden Zahlen ausgeben. Sie sollen innerhalb der Funktion das Produkt berechnen, ohne eine Multiplikation `*` zu benutzen. Benutzen Sie statt dessen Schleifen und Addition.

Tipp: 

Die Multiplikation 3 * 4 kann genauso als Addition gesehen werden - man addiert 3 mal die 4 aufeinander (4 + 4 + 4).

*** =instructions
- Schreiben Sie die Funktion `multiply` 
- Sie soll als Eingabeparameter `a` und `b` zwei Zahlen bekommen.
- Benutzen Sie statt eine Multiplikation eine Addition (siehe Tipp).
- Die Funktion soll das `product` der beiden Zahlen zurück geben.

*** =hint

*** =pre_exercise_code
```{r}
x = 12*14

```

*** =sample_code
```{r}
# Funktion erstellen





# Testen Sie ihre Funktion für a = 12 und b = 14


```

*** =solution
```{r}
# Funktion erstellen
multiply <- function(a,b){
  product <- 0
  while(a>0){
    product <- product + b
    a <- a - 1}
  return(product)
}
# Testen Sie ihre Funktion für a = 12 und b = 14
multiply(12,14)

```

*** =sct
```{r}
test_output_contains("x")
test_error()
```
--- type:NormalExercise lang:r xp:100 skills:1 key:1d44ff1436
## 5. Funktionen 
In einer Firma reicht ein Mitarbeiter seine gewünschten Urlaubstage für das Jahr 2017 ein. Diese liegen im Vektor `daten`. Es gibt allerdings einige Tage in diesem Jahr, an denen Sie auf keinen Mitarbeiter verzichten können. Diese Tage sind der 20.07.2017 und die Zeit zwischen dem 28. und dem 30. Dezember 2017.
Schreiben Sie eine Funktion, welche dieses Problem löst.

Info: 

- Die Vektoren `daten` und `possible` sind bereits als Typ "Date" initialisiert und müssen daher beide der Funktion übergeben werden.
- `possible` ist anfangs leer.
- Ein Datum sieht folgendermaßen aus: "JJJJ-MM-TT", also z.B. "2017-04-03" 

*** =instructions
- Schreiben Sie eine Funktion `urlaub`, welche die Vektoren `daten` und `possible` als Eingabe bekommt.
- in `daten` stehen die Tage, an denen der Mitarbeiter Urlaub nehmen will.
- Vergleichen Sie jeden Wert im Vektor mit den "verbotenen" Tagen. 
- Die Ausgabe soll ein Vektor mit den Daten sein, die nicht kollidieren.
*** =hint
- Die Daten im Vektor `daten` wurden mit as.Date als Typ "Date" gesetzt. Sie können Sie deshalb ganz normal mit Vergleichsoperatoren vergleichen. 
- Verwenden Sie eine for-Schleife, welche den Vektor durchläuft und eine if-Abfrage, welche die Bedingung überprüft.

*** =pre_exercise_code
```{r}
# Erstellung der Vektoren
daten <- c("2017-10-03", "2017-10-04", "2017-10-05", "2017-10-06", "2017-07-20", "2017-07-21",  "2017-07-22",  "2017-07-23",  "2017-07-24", "2017-12-23", "2017-12-28", "2017-12-29", "2017-12-30")
# Beide Vektoren als Datum initialisieren
daten <- as.Date(daten)
possible <- integer(0)
class(possible) <- "Date"
# Ergebnis 
xoxo <- c("2017-10-03", "2017-10-04", "2017-10-05", "2017-10-06", "2017-07-21", "2017-07-22", "2017-07-23", "2017-07-24", "2017-12-23")

```

*** =sample_code
```{r}
#  Schreibe Funktion Urlaub
urlaub <- function(daten, possible){









  return(possible)
}

# Funktion ausführen
urlaub(daten, possible)


```

*** =solution
```{r}
#  Schreibe Funktion Urlaub
urlaub <- function(daten, possible){
# Setze die Zählvariable für den neuen Vektor
  j = 1
  # Gehe den ganzen daten Vektor durch
  for(i in 1:length(daten)){
  # Bedingung - ist es ein Kollisionstag?
    if(daten[i] != "2017-07-20" & (daten[i] < "2017-12-28" | daten[i] > "2017-12-30") ){
    # kein Kollisionstag, also kann Datum in Vektor possible geschrieben werden.
      possible[j] <- daten[i]
      # Zählvariable hochzählen
      j <- j+1
    }
  }
  # possible zurückgeben
  return(possible)
}

# Funktion ausführen
urlaub(daten, possible)

```

*** =sct
```{r}
test_output_contains("xoxo")
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
reihe <- c(1, 33, 45, 33, 4, 66, 78, 98, 98, 99, 102, 103, 45, 304, 255, 32, 6, 78, 12, 3, 4, 56, 7, 1, 0)
xyz <- c(1.00000,  33.00000,  45.00000,  37.14286,  51.00000,  60.28571,  68.00000,  77.85714,  92.00000,  89.00000, 121.28571, 143.71429, 134.28571, 121.00000, 117.57143, 104.57143,  98.57143,  55.71429,  27.28571,  23.71429,  23.00000,  56.00000,   7.00000,   1.00000,  0.00000)



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