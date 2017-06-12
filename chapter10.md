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

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:bd5b2e2444
## qnorm()
Versuchen Sie diese Frage ohne Berechnung zu beantworten.

Welches Ergebnis liefert `qnorm(0.5, mean = 40, sd = 5)`

*** =instructions
- Einen zufälligen Wert zwischen 35 und 45
- 40
- 20
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig!"
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad))
```



--- type:NormalExercise lang:r xp:100 skills:1 key:039e472d47
## ZGS (I)


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
--- type:NormalExercise lang:r xp:100 skills:1 key:20e949d5dc
## ZGS (II)
Replizieren Sie die Grafik aus der VL für n = 30  un n = 100.
Gehen Sie weiterhin von 1 Freiheitsgrad aus.

*** =instructions
- BeaSetze die korrekte Standardabweichung für der ChiQuadrath verteilung

*** =hint

*** =pre_exercise_code
```{r}
check_zgs <- function(groesse, freiheitsgrade){
  mittelwerte <- c()
  for(i in 1:10000){
    stichprobe_i <- rchisq(n = groesse, df = freiheitsgrade)
    mittelwerte[i] <- mean(stichprobe_i)
  }
  return(mittelwerte)
}

# Anwenden der Funktion
g1 = 30
mw <- check_zgs(groesse, freiheitsgrade = 1)
# Darin sind jetzt 10000 Mittwelwerte von Stichproben der Größe 5 mit der Varianz 2
plot(density(mw))
# Festsetzen der Werte (Varianz = 2* df)
varianz = 2
# Woher kommt der mean?
sd_test <- sqrt(varianz/groesse)
# vergleich zur asymptotischen Verteilung laut ZGS (norm)
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))

```

*** =sample_code
```{r}
check_zgs <- function(groesse, freiheitsgrade){
  mittelwerte <- c()
  for(i in 1:10000){
    stichprobe_i <- rchisq(n = groesse, df = freiheitsgrade)
    mittelwerte[i] <- mean(stichprobe_i)
  }
  return(mittelwerte)
}

# Anwenden der Funktion

mw <- check_zgs(___, freiheitsgrade = 1)

plot(density(mw))
# Setzen Sie die korrekte Standardabweichung
sd_test <- ___

# vergleich zur asymptotischen Verteilung laut ZGS (norm)
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))


```

*** =solution
```{r}

```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:d116af166c
## ZGS(III)



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
