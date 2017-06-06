---
title       : Einheit 4 - homework
description : Homework zum ggplot Kapitel


--- type:NormalExercise lang:r xp:100 skills:1 key:4262a8c0ff
## ggplot(I)
Erstellen Sie einen Plot mit ggplot.

Die Daten liegen im Datensatz "cars".

*** =instructions
- Erstellen Sie einen Punkteplot mit der Geschwindigkeit `dist` auf der x-Achse und `speed` auf der y-Achse.
- Beschriften Sie die x-Achse mit "Distanz" und die y-Achse mit Geschwindigkeit.
- Schreiben Sie über die Grafik den Titel "cars"

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)

```

*** =sample_code
```{r}
library(ggplot2)
# Plot



    
```

*** =solution
```{r}
# Plot
ggplot(data = cars, mapping = aes(x = dist, y = speed))+
    geom_point()+
    xlab("Distanz")+
    ylab("Geschwindigkeit")+
    ggtitle("cars")

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("xlab")
test_function("ylab")
test_function("ggtitle")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:19545c4dd1
## ggplot(II)
Gegeben ist der Datensatz mtcars.

Erstellen Sie einen ggplot. 



*** =instructions
- Plotten Sie das Gewicht "wt" auf x  und auf "mpg" (miles per gallon) auf y.
- Stellen Sie anhand der Größe der Quadrate die Beschleudigung "qsec" dar. (Quadrate haben die Kennzahl 15)
- Unterstützen Sie die qsec Darstellung durch die Färbung nach Beschleunigung.

*** =hint
- nutzen Sie für die Größe in `aes(..., size = VARIABLE,...)`
- nutzen Sie für die Färbung `aes(..., group = VAR, color = VAR)`
- setzen Sie die Form durch `shape = 15`

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)

```

*** =sample_code
```{r}
library(ggplot2)
# Plot


```

*** =solution
```{r}
ggplot(data = mtcars, mapping = aes(x = wt, y = mpg, size = qsec, group = qsec, color = qsec))+
  geom_point(shape = 15)

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_point", args = c("shape"))
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:3a1d2c4e79
## ggplot(III)
Erstellen sie einen Boxplot mit ggplot.

Zum Datensatz: Im mtcars Datensatz steht in der `am` Variable eine 0 für automatik und eine 1 für manuel.

*** =instructions
- Erstellen sie  jeweils für Automatik und Manuelle Fahrzeuge einen Boxplot, der die Verteilung der beiden Merkmale auf die Variable "mpg" anzeigt.
- Trennen Sie durch `group = VAR` die beiden Boxplots.
- Benennen Sie die y-Achse zu "miles per gallon".
*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)
```

*** =sample_code
```{r}
library(ggplot2)
# Boxplot




```

*** =solution
```{r}
ggplot(data = mtcars)+
  geom_boxplot(mapping = aes(x = am, y= mpg, group = am))+
  ylab("Miles per Gallon")
```

*** =sct
```{r}
test_function("ggplot", args = c("data"))
test_function("geom_boxplot", args = c("mapping"))
test_function("ylab")
test_error()

```


--- type:NormalExercise lang:r xp:100 skills:1 key:f716f27f34
## ggplot(IV)
Erstellen Sie ein Histogramm über die Verteilung der Cylinderzahl (cyl).

*** =instructions
- Arbeiten Sie mit verschiedenen aesthetics:
- Färben Sie die Balken außen mit rot und innen mit blau.
*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)
```

*** =sample_code
```{r}
library(ggplot2)
# Histogramm


```

*** =solution
```{r}
ggplot(data = mtcars, mapping = aes(x = cyl))+
  geom_bar(color = "red", fill = "blue")
```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_bar", args = c("color", "fill"))
test_error()

```
--- type:NormalExercise lang:r xp:100 skills:1 key:2c68925ce4
## Regression (I)
Erstellen Sie eine lineare Regression und prüfen Sie den Zusammenhang der Variablen "wt" (Gewicht) und "mpg" (miles per gallon) aus dem Datensatz "mtcars".


*** =instructions
- Erstellen Sie einen Punkteplot mit dem Gewicht des Autos auf der x-Achse, und "miles per gallon" auf der y-Achse.
- Benutzen Sie eine lineare Regression, um einen Möglichen Zusammenhang zu entdecken.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)
```

*** =sample_code
```{r}
library(ggplot2)
# lineare Regression


```

*** =solution
```{r}
# lineare Regression
ggplot(data = mtcars, mapping = aes(x = wt, y = mpg)) +
    geom_point() + 
    geom_smooth(method = 'lm')

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_point")
test_function("geom_smooth", args = c("method"))
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:d340cf399a
## Regression (II)
Erstellen Sie eine Regression, welche die nächsten Nachbarpunkte stärker berücksichtigt.

*** =instructions
- Erstellen Sie einen Punkteplot über das Gewicht (wt) auf der x-Achse und miles per gallon (mpg) auf der y-Achse.
- Erstellen Sie im Plot eine Regressionsgeraden.
- Benutzen Sie einen Span-Wert von 0.4.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)
```

*** =sample_code
```{r}
library(ggplot2)
# Regressionsplot

```

*** =solution
```{r}
ggplot(data = mtcars, mapping = aes(x = wt, y = mpg))+
  geom_point()+
  geom_smooth(span = 0.4)

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_point")
test_function("geom_smooth")
test_error()
```


--- type:NormalExercise lang:r xp:100 skills:1 key:f3e019f723
## ggplot(V)
Sie sehen rechts im Bild eine Grafik. 

Tipp: Das geom `geom_density` eignet sich zur Häufigkeitsverteilung von stetigen Variablen.

*** =instructions
- Schreiben Sie den Code, der genau diese Grafik erzeugt.
- Achten Sie auch auf Kleinigkeiten wie Beschriftungen.
- der alpha-Wert muss auf 0.4 gesetzt werden.
*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("cars")
cars <- as.data.frame(cars)
ggplot(mtcars, mapping = aes(x = mpg))+
    geom_density(aes(group = cyl, color = cyl, fill = cyl), alpha = 0.4)+
    ggtitle("Haeufigkeitsverteilung")+
    xlab("Miles per gallon")

```

*** =sample_code
```{r}
library(ggplot2)
# Density Plot




```

*** =solution
```{r}
# Density Plot
ggplot(data = mtcars, mapping = aes(x = mpg))+
    geom_density(aes(group = cyl, color = cyl, fill = cyl), alpha = 0.4)+
    ggtitle("Haeufigkeitsverteilung")+
    xlab("Miles per gallon")
```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_density", args = c("mapping", "alpha"))
test_function("ggtitle")
test_function("xlab")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:7aa40d06a6
## function(I)


*** =instructions
- Die Funktion bekommt als Eingabeparameter 2 Datensätze
*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
library(dplyr)

Erstellung der Datensätze
tag <- c(1,2,3,5,8,9,10,11:20, 25, 27, 31:42, 45, 48, 50)
einnahmen <- c(1050, 1280, 3422, 2504, 6123, 1231, 2242, 1624, 1242, 1543, 3746, 8987, 2365, 4425, 2741, 3486, 1334, 5475, 3346, 2335, 2334, 2474, 3444, 6766, 1233, 3142, 2774, 2245, 3426, 1354,2735, 2234, 1623, 5322)
einnahmenDF <- data.frame(tag, einnahmen)
tag <- c(1,3:8,10:22, 25, 26, 31:46, 50)
besucher <- c(100, 180, 322, 204, 123, 131, 242, 124, 124, 543, 346, 897, 235, 425, 241, 346, 134, 475, 346, 235, 234, 244, 444, 666, 123, 142, 274, 245, 326, 134,235, 234, 123, 532, 135, 344, 364, 263, 99)
besucherDF <- data.frame(tag, besucher)

```

*** =sample_code
```{r}
library(ggplot2)
library(dplyr)
```

*** =solution
```{r}
# Funktion
joingrafik <- function(dataset1, dataset2, xwert, ywert1, ywert2){
# joining der Datensaetze anhand von tag
  dataset <- inner_join(dataset1, dataset2, by = xwert)
  # Plotten der Daten
  ggplot(data = dataset)+
    geom_point(mapping = aes(x = get(xwert), y = get(ywert1), group = get(ywert2), size = get(ywert2), color = get(ywert2)))+
    xlab("x")+
    ylab("y")
}

joingrafik(besucherDF, einnahmenDF, "tag", "besucher", "einnahmen")

```

*** =sct
```{r}

```
