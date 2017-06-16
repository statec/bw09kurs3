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




--- type:NormalExercise lang:r xp:100 skills:1 key:ab30f0abfa
## Normalverteilung (I)
Die mittleren Jahreseinkommen einer Großstadt betragen 33000€ mit einer Standardabweichung von 6500€.
Man entnimmt eine Zufallsstichprobe mit 500 Haushalten.

Runden Sie nicht! Arbeiten Sie mit den exkten Werten.

*** =instructions
- Wie hoch ist die Wahrscheinlichkeit in der Stichprobe ein mittleres Jahreseinkommen von über 32800€ zu finden?
*** =hint
- Laut ZGS sind die Mittelwerte Normalverteilt.

*** =pre_exercise_code
```{r}
xxx <- 1 -pnorm(abs(sqrt(500)*(32800-33000)/6500))
```

*** =sample_code
```{r}


```

*** =solution
```{r}
Zn  <- abs(sqrt(500)*(32800-33000)/6500)
gegen_p <- pnorm(Zn)
p <- 1 - gegen_p
```

*** =sct
```{r}
test_output_contains("xxx")
test_error()

```


--- type:NormalExercise lang:r xp:100 skills:1 key:635ecf6689
## Normalverteilung (II)
Die mittleren Jahreseinkommen einer Großstadt betragen 33000€ mit einer Standardabweichung von 6500€.
Man entnimmt eine Zufallsstichprobe mit 500 Haushalten.

Runden Sie nicht! Arbeiten Sie mit den exakten Werten.

*** =instructions
- Berechnen Sie die Wahrscheinlichkeit dafür, dass der Stichprobenmittelwert zwischen 32750 und 33250 liegt. Geben Sie das Ergebnis in der Konsole aus.

*** =hint

*** =pre_exercise_code
```{r}
ax <- pnorm(abs(sqrt(500)*(33250-33000)/6500))
bx <- 1 -pnorm(abs(sqrt(500)*(32750-33000)/6500))
pkl <- ax - bx
rm(ax)
rm(bx)

```

*** =sample_code
```{r}

```

*** =solution
```{r}
upperbound <- pnorm(abs(sqrt(500)*(33250-33000)/6500))
lowerbound <- 1 -pnorm(abs(sqrt(500)*(32750-33000)/6500))
upperbound - lowerbound

```

*** =sct
```{r}
test_output_contains("pkl")
test_error()
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:fcb503360c
## Hypothesentest(I)
Die Annahmeprüfung für eine Produktion von Sicherungen wird auf Stichprobenbasis durchgeführt.

Der Hersteller behauptet, der Anteil der nicht funktionsfähigen Sicherungen beträgt höchstens 7.5%. 


Die Prüfung von 400 zufällig ausgewählten Sicherungen ergab, dass 359 funktionsfähig waren.


Wir können annehmen, dass wir eine Binominalverteilung vorliegen haben. Ablehnung der Hypothese?

*** =instructions
- Ablehnung der Hypothese auf Signifikanzniveau 2%
- Ablehnung der Hypothese auf Signifikanzniveau 5%
- Ablehnung der Hypothese auf Signifikanzniveau 10%
*** =hint

*** =pre_exercise_code
```{r}
# Berechnung durch
# pwert <- pbinom(q = 359, size = 400, prob = 0.925)

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))
```


--- type:NormalExercise lang:r xp:100 skills:1 key:2cccffc667
## Hyptothesentest (II)
Die Annahmeprüfung für eine Produktion von Sicherungen wird auf Stichprobenbasis durchgeführt.

Der Hersteller behauptet, der Anteil der nicht funktionsfähigen Sicherungen beträgt höchstens 5%. 


Es wird eine Stichprobe von 500 Stück geprüft.


Wir können annehmen, dass wir eine Binominalverteilung vorliegen haben.

*** =instructions
- Wie viele Lampen müssen funktionstüchtig sein, um unter einem Signifikanzniveau von 7% die Hypothese des Herstellers abzulehnen?
- Geben Sie den Wert in der Konsole aus.
- Hier stimmt irgendwas mit der Logik nicht...
*** =hint

*** =pre_exercise_code
```{r}
uhi <- qbinom(p =0.07 , size = 500, prob = 0.95 )
```

*** =sample_code
```{r}
qbinom(p =0.07 , size = 500, prob = 0.95 )

```

*** =solution
```{r}
# Berechnung durch inverse Verteilungsfunktion
qbinom(p =0.07 , size = 500, prob = 0.95 )
# Veranschaulicht - Test Zwischenwerte: 
pbinom(q = 467, size = 500, prob = 0.95)
pbinom(q = 468, size = 500, prob = 0.95)
```

*** =sct
```{r}
test_output_contains("uhi")
test_error()

```
--- type:NormalExercise lang:r xp:100 skills:1 key:20e949d5dc
## ZGS (I)
Replizieren Sie die Grafik aus der VL für n = 30  un n = 100 (Folien 18 & 19).

Gehen Sie weiterhin von 1 Freiheitsgrad aus.

Tipp: Informieren Sie sich über die Standardabweichung der Chiquadrat Verteilung.

*** =instructions
- Setze die korrekte Standardabweichung für der ChiQuadrath verteilung. 
- Überprüfen Sie selbst, ob die von Ihnen erstellte Grafik den entsprechenden Grafiken im Skript entsprechen.
*** =hint

*** =pre_exercise_code
```{r}


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

# Anwenden der Funktion für n = 30
mw <- check_zgs(groesse = 30, freiheitsgrade = 1)
plot(density(mw))
# Setzen Sie die korrekte Standardabweichung
sd_test <- ___
# Vergleich zur asymptotischen Verteilung laut ZGS
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))

# Anwenden der Funktion für n = 100
mw <- check_zgs(groesse = 100, freiheitsgrade = 1)
plot(density(mw))
# Setzen Sie die korrekte Standardabweichung
sd_test <- ___
# Vergleich zur asymptotischen Verteilung laut ZGS 
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))


```

*** =solution
```{r}
check_zgs <- function(groesse, freiheitsgrade){
  mittelwerte <- c()
  for(i in 1:10000){
    stichprobe_i <- rchisq(n = groesse, df = freiheitsgrade)
    mittelwerte[i] <- mean(stichprobe_i)
  }
  return(mittelwerte)
}

# Anwenden der Funktion für n = 30
groesse = 30
freiheitsgrade = 1
# Varianz = 2*df
varianz = 2
mw <- check_zgs(groesse, freiheitsgrade)
plot(density(mw))
# Setzen Sie die korrekte Standardabweichung
sd_test <- sqrt(varianz/groesse)
# vergleich zur asymptotischen Verteilung laut ZGS (norm)
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))

# Anwenden der Funktion für n = 100
groesse = 100
mw <- check_zgs(groesse, freiheitsgrade)
plot(density(mw))
# Setzen Sie die korrekte Standardabweichung
sd_test <- sqrt(varianz/groesse)
# vergleich zur asymptotischen Verteilung laut ZGS (norm)
curve(dnorm(x, mean = 1, sd = sd_test), from = -5, to = 5, col = "red", lwd = 2, add = TRUE)
legend("topright", c("check_zgs", "ZGS"), col=c("black", "red"))
```

*** =sct
```{r}

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:a015e94bb1
## ZGS(II)
Welche Standartabweichung hätten wir bei einer Chiquadrat Verteilung mit folgenden Parametern:

groesse = 100


freiheitsgrade = 2

*** =instructions
- 1/5
- 2/100
- 1/10

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig! Hier muss man sich merken Varianz = 2*freiheitsgrade."
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))
```
