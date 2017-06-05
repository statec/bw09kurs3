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
