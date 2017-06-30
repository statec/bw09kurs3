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
gruppe4 <- rnorm(n, mean = 3, sd = 5)
# Liste der Gruppen
werte <- c(gruppe1, gruppe2, gruppe3, gruppe4)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n), rep("g4", n))
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
Nun sollen Sie per Hand Schrittweise die Varianzanalyse vornehmen. Zuerst soll alleine der Zähler des F-Wertes berechnet werden. Dieser entspricht der Abweichung im Gruppenmittelwert. Die Daten liegen in `datensatz`.


Tipp: Die Daten sind in 4 Gruppen aufgeteilt, welche in `gruppe_i` für 1<=i<=4 enthalten sind.

*** =instructions
- Berechnen Sie die Abweichung im Gruppenmittelwert.
- Speichern Sie das Ergebnis in `zaehler`.
*** =hint

*** =pre_exercise_code
```{r}
n <- 100
set.seed(2)
# Erstellt Zufallszahlen
gruppe_1 <- rnorm(n, mean = 0, sd = 5)
gruppe_2 <- rnorm(n, mean = 1, sd = 5)
gruppe_3 <- rnorm(n, mean = 2, sd = 5)
gruppe_4 <- rnorm(n, mean = 3, sd = 5)
# Liste der Gruppen
werte <- c(gruppe_1, gruppe_2, gruppe_3, gruppe_4)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n), rep("g4",n))
datensatz <- data.frame(werte, gruppenname)


```

*** =sample_code
```{r}






zaehler <- ___


```

*** =solution
```{r}
# Anzahl der Gruppen
l <- 4
# Anzahl der Beobachtungen
n_i <- 100
# means berechnen
m_g1 <- mean(gruppe_1)
m_g2 <- mean(gruppe_2)
m_g3 <- mean(gruppe_3)
m_g4 <- mean(gruppe_4)
m_all <- mean(c(gruppe_1, gruppe_2, gruppe_3, gruppe_4))
# Abweichung im Gruppenmittelwert
zaehler <- 1/(l-1) * (  n_i* ( m_g1 - m_all )^2 +
                        n_i* ( m_g2 - m_all )^2 +
                        n_i* ( m_g3 - m_all )^2 +
                        n_i* ( m_g4 - m_all )^2 )
```

*** =sct
```{r}
test_object("zaehler")
test_error()
```



--- type:NormalExercise lang:r xp:100 skills:1 key:b3ecb8c0b2
## ANOVA (III)
Weiter in der schrittweisen Varianzanalyse. Nun sollen Sie den Nenner des F-Wertes berechnen. Dieser entspricht der Varianz innerhalb der Gruppen.
Die Daten liegen in `datensatz`.

Tipp: Um die Summen über die korrekten vektoren zu bilden, müssen Sie den Datensatz erst anhand der Gruppen aufteilen. 

*** =instructions
- Berechnen Sie die Varianz innerhalb der Gruppen.
- Speichern Sie das Ergebnis in `nenner`.
- Benutzen Sie `filter()` um die Gruppen aufzuteilen.
*** =hint

*** =pre_exercise_code
```{r}
n <- 100
set.seed(2)
# Erstellt Zufallszahlen
gruppe_1 <- rnorm(n, mean = 0, sd = 5)
gruppe_2 <- rnorm(n, mean = 1, sd = 5)
gruppe_3 <- rnorm(n, mean = 2, sd = 5)
gruppe_4 <- rnorm(n, mean = 3, sd = 5)
# Liste der Gruppen
werte <- c(gruppe_1, gruppe_2, gruppe_3, gruppe_4)
gruppenname <- c(rep("g1", n), rep("g2", n), rep("g3",n), rep("g4",n))
datensatz <- data.frame(werte, gruppenname)
```

*** =sample_code
```{r}
library(dplyr)







# Varianz innerhalb der Gruppen
nenner <- ___





```

*** =solution
```{r}
library(dplyr)
# Anzahl der Gruppen
l <- 4
# Anzahl der Beobachtungen
n_i <- 100
# Gruppentrennung
g1 <- filter(datensatz, gruppenname == "g1")
g2 <- filter(datensatz, gruppenname == "g2")
g3 <- filter(datensatz, gruppenname == "g3")
g4 <- filter(datensatz, gruppenname == "g4")
# means berechnen
m_g1 <- mean(g1$werte)
m_g2 <- mean(g2$werte)
m_g3 <- mean(g3$werte)
m_g4 <- mean(g4$werte)
m_all <- mean(c(g1$werte, g2$werte, g3$werte, g4$werte))
# Varianz innerhalb der Gruppen
nenner <- 1/( n_i - l ) * ( sum( ( g1$werte - m_g1 )^2 ) +
                            sum( ( g2$werte - m_g2 )^2 ) +
                            sum( ( g3$werte - m_g3 )^2 ) +
                            sum( ( g4$werte - m_g4 )^2 ) )
```

*** =sct
```{r}
test_object("nenner")
test_error()
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
