---
title       : Einheit 5 - inclass
description : probability distributions


--- type:NormalExercise lang:r xp:100 skills:1 key:18badc89d0
## distributions (I)
Sei X eine normalverteilte Zufallsvariable mit Mittelwert 10 und Standardabweichung 1. 

Geben Sie `?dnorm()` in der Konsole ein, um die Eingabeparameter der Funktionen korrekt zu wählen.


*** =instructions
- a) Berechne die Wahrscheinlichkeitsverteiling an der Stelle x = 9.
- b) Wie groß ist die Wahrscheinlichkeit dass X einen Wert kleiner als 8 annimmt?
- c) kleiner gleich welcher Wert ist X zu 40%?
- d) Erstellen Sie einen Vektor aus 10 zufälligen Ziehungen dieser Verteilung.

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}
# Wahrscheinlichkeitsverteiling an der Stelle x = 9
dnorm(x = 9, mean = 10, sd = 1)

# Verteilungsfunktion an der Stelle x = 8
pnorm(q = 8, mean = 10, sd = 1)

# kleiner gleich welcher Wert ist X zu 40%
qnorm(p = 0.4 , mean = 10, sd = 1)

# 10 zufälligen Ziehungen
rnorm(n = 10, mean = 10, sd = 1)


```

*** =sct
```{r}
test_function("dnorm", args = c("x", "mean", "sd"))
test_function("pnorm", args = c("q", "mean", "sd"))
test_function("qnorm", args = c("p", "mean", "sd"))
test_function("rnorm", args = c("n", "mean", "sd"))
test_error()
```
