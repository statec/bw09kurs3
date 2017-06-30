---
title       : Einheit 6 - inclass
description : Varianzanalyse und Modellierung

--- type:NormalExercise lang:r xp:100 skills:1 key:82ad91f31b
## Varianzanalyse
Sie haben den Outpus des aov() Befehls gegeben.

*** =instructions
- Replizieren Sie diesen von Hand
*** =hint

*** =pre_exercise_code
```{r}
n <- 100
set.seed(1)
# Erstellt Zufallszahlen
gruppe1 <- rnorm(n, mean = 0, sd = 5)
gruppe2 <- rnorm(n, mean = 1, sd = 5)
gruppe3 <- rnorm(n, mean = 2, sd = 5)
# Liste der Gruppen
werte <- c(gruppe1, gruppe2, gruppe3)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n))

datensatz <- data.frame(werte, gruppenname)

aov(werte ~ gruppenname, data = datensatz)

```

*** =sample_code
```{r}
# hier
```

*** =solution
```{r}

```

*** =sct
```{r}

```
