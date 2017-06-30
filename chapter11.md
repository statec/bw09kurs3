---
title       : Einheit 6 - inclass
description : Varianzanalyse und Modellierung

--- type:NormalExercise lang:r xp:100 skills:1 key:82ad91f31b
## ANOVA (I)
Ihnen ist ein  `datensatz` gegeben. 


Untersuchen Sie mittels einer univariaten Anova Analyse, ob sich die `werte` signifikant voneinander unterscheiden.

*** =instructions
- Benutzen Sie `aov()` um eine Varianzanalyse durchzuführen.
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

# Summary mit F value 7.211
summary(res)
```

*** =sct
```{r}
test_function("aov")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:920fd7379a
## ANOVA (II)
Nun sollen Sie per hand Schrittweise die Varianzanalyse vornehmen. Zuerst soll alleine der Zähler der F-Wert berechnung augerechnet werden.

Tipp: Die Daten sind in 3 Gruppen aufgeteilt, welche in `gruppe_i` für 1 <= i <=3 enthalten sind.

*** =instructions
- Rechnen Sie zuerst den Zähler des Bruches aus.
*** =hint

*** =pre_exercise_code
```{r}
n <- 100
set.seed(2)
# Erstellt Zufallszahlen
gruppe_1 <- rnorm(n, mean = 0, sd = 5)
gruppe_2 <- rnorm(n, mean = 1, sd = 5)
gruppe_3 <- rnorm(n, mean = 2, sd = 5)
# Liste der Gruppen
werte <- c(gruppe_1, gruppe_2, gruppe_3)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n))
datensatz <- data.frame(werte, gruppenname)


```

*** =sample_code
```{r}
# Anzahl der Gruppen
l <- 3
# Anzahl der Beobachtungen
n_i <- 100
# means berechnen
m_g1 <- mean(gruppe_1)
m_g2 <- mean(gruppe_2)
m_g3 <- mean(gruppe_3)
m_all <- mean(c(gruppe_1, gruppe_2, gruppe_3))

zaehler <- 1/(l-1) * ( n_i* ( m_g1 - m_all )^2 +
                                    nb* ( m_g2 - m_all )^2 +
                                    nb* ( m_g3 - m_all )^2 )


```

*** =solution
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:374cb2ecaa
## Annahmen Überprüfung
Überprüfen Sie die Normalverteilungsannahme.


*** =instructions
- Erstellen Sie einen Plot, um die Normalverteilungsannahme zu überprüfen!
- Orientieren Sie sich am Skript.
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
