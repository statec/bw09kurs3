---
title       : Einheit 6 - inclass
description : Varianzanalyse und Modellierung

--- type:NormalExercise lang:r xp:100 skills:1 key:82ad91f31b
## ANOVA (I)
Ihnen ist ein  `datensatz` gegeben, über den Sie nun eine Varianzanalyse machen sollen.

*** =instructions
- Benutzen Sie `aov()` um eine varianzanalyse zu machen.
- Speichern Sie das Ergebnis in `res`.
- Geben sie das Summary des Ergebnisses aus. 
*** =hint

*** =pre_exercise_code
```{r}
n <- 100
set.seed(2)
# Erstellt Zufallszahlen
gruppe1 <- rnorm(n, mean = 0, sd = 5)
gruppe2 <- rnorm(n, mean = 1, sd = 5)
gruppe3 <- rnorm(n, mean = 2, sd = 5)
# Liste der Gruppen
werte <- c(gruppe1, gruppe2, gruppe3)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n))
datensatz <- data.frame(werte, gruppenname)

```

*** =sample_code
```{r}
# ANOVA Analyse
res <- 

# Summary
summary(res)

```

*** =solution
```{r}
# ANOVA Analyse
res <- aov(werte ~ gruppenname, data = datensatz)

# Summary
summary(res)
```

*** =sct
```{r}
test_function("aov")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:920fd7379a
## ANOVA (II)


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
