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
res <- ______

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
# Anzahl der Beobachtungen pro Gruppe
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
Die Daten liegen in `datensatz`. Ihr Ergebnis von der vorherigen Aufgabe steht in `zaehler`.

Tipp: Um die Summen über die korrekten vektoren zu bilden, müssen Sie den Datensatz erst anhand der Gruppen aufteilen. 

*** =instructions
- Berechnen Sie die Varianz innerhalb der Gruppen.
- Speichern Sie das Ergebnis in `nenner`.
- Benutzen Sie `filter()` um die Gruppen aufzuteilen.
- Berechnen Sie F.
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

# Anzahl der Gruppen
l <- 4
# Anzahl der Beobachtungen pro Gruppe
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

*** =sample_code
```{r}
library(dplyr)







# Varianz innerhalb der Gruppen
nenner <- ___




# Ergebnis
F_wert = zaehler/nenner
# Vergleich mit aov()
summary(aov(werte ~ gruppenname, data = datensatz))
```

*** =solution
```{r}
library(dplyr)
# Anzahl der Gruppen
l <- 4
# Anzahl Beobachtungen von allen Gruppen
n <- 400
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
# Varianz innerhalb der Gruppen
nenner <- 1/( n - l ) * ( sum( ( g1$werte - m_g1 )^2 ) +
                            sum( ( g2$werte - m_g2 )^2 ) +
                            sum( ( g3$werte - m_g3 )^2 ) +
                            sum( ( g4$werte - m_g4 )^2 ) )
# Ergebnis
F_wert = zaehler/nenner
# Vergleich mit aov()
summary(aov(werte ~ gruppenname, data = datensatz))
```

*** =sct
```{r}
test_object("nenner")
test_object("F_wert")
test_function("aov")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:872e0ec346
## ANOVA (IV)
Schreiben Sie eine Funktion `anova_check2`, welche eine Teststatistik erstellt, um die Normalverteilungsannahme zu prüfen, welche wir bisher unterstellt haben. Bedenken Sie, dass es eine Einteilung in 4 Gruppen gibt. 

*** =instructions
- Schreiben Sie die Funktion `anova_check2`.
- Orientieren Sie sich an der Funktion im Skript.
- Beachten Sie, dass es 4 Gruppen gibt.
- Erstellen Sie die Teststatistiken und überprüfen Sie anhand eines Plottes die Normalverteilungsannahme.
*** =hint
- Arbeiten Sie mit `plot(density())` und dem `curve()` Befehl.
*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Erstellung der Funktion
anova_check2 <- function(n){










  return(___)
}

# Erstellung der Teststatistik (vorgegeben)
test_stats <- c()
for(i in 1:10000){
  test_stats[i] <- anova_check2(5)
}

# Plotten um Normalverteilungsannahme zu überprüfen




```

*** =solution
```{r}
anova_check2 <- function(n){
  g1 <- rnorm(n)
  g2 <- rnorm(n)
  g3 <- rnorm(n)
  g4 <- rnorm(n)
  m_g1 <- mean(g1)
  m_g2 <- mean(g2)
  m_g3 <- mean(g3)
  m_g4 <- mean(g4)
  m_all <- mean(c(g1, g2, g3, g4))
  #
  zaehler <- 1/3 * (n*(m_g1 - m_all)^2 +
                    n*(m_g2 - m_all)^2 +
                    n*(m_g3 - m_all)^2 + 
                    n*(m_g4 - m_all)^2 )
  nenner <- 1/(4*n-4)* (sum((g1-m_g1)^2)+
                        sum((g2-m_g2)^2)+
                        sum((g3-m_g2)^2)+
                        sum((g4-m_g3)^2))
  teststat <- zaehler / nenner 
  return(teststat)
}

# Erstellung der Teststatistiken
test_stats <- c()
for(i in 1:10000){
  test_stats[i] <- anova_check2(5)
}

# Plotten um Normalverteilungsannahme zu überprüfen
plot(density(test_stats))
curve(df(x, df1 = 3, df2 = 4*5 -4), from = -1, to = 30, n = 10000, col = "red", lwd = 2, add = TRUE)
legend("topright", c("test_stats", "vorhergesagte Verteilung"), col = c("black", "red"), lty = c(1,1))
# Problem: Der Plot bestätigt eher nicht die Normalverteilungsannahme? Habe ich einen Parameter vergessen, falsche ingegeben?
```

*** =sct
```{r}
test_function("anova_check2")
test_error()
```



--- type:NormalExercise lang:r xp:100 skills:1 key:b03912de68
## ANOVA (V)
Gegeben ist der `datensatz`.

Nach der Normalverteilungsannahme muss nun noch die Varianzhomogenität überprüft werden. 

*** =instructions
- Überprüfen Sie die Varianzhomogenität über die Boxplot Funktion.
- Erstellen Sie die Boxplots für die jeweiligen Gruppen nebeneinander, sodass Sie die Abweichungen innerhalb der Gruppen mit denen der anderen vergleichen können.
- Gilt die Annahme?
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
library(ggplot2)
# Test auf Varianzhomogenität



```

*** =solution
```{r}
library(ggplot2)
# Test auf Varianzhomogenität
ggplot(data = datensatz)+
  geom_boxplot(mapping = aes(x = gruppenname, y = werte))

```

*** =sct
```{r}
test_function("geom_boxplot", args = c("mapping"))
test_error()
```
--- type:NormalExercise lang:r xp:100 skills:1 key:9a4690dabe
## Lineare Regression
Berechnen Sie mittels `lm()` eine lineare Regression für den Eröffnungskurs der facebook Aktie. Diese liegt in `facebook`.


Tipp: sie können per `coefficients(linreg)[i]` auf den i-ten Koeffizienten zugreifen.


*** =instructions
- Speichern Sie die lineare Regressionsgerade in `linreg`.
- Plotten Sie ihr Ergebnis, sodass der Plot wie der vorgegebene aussieht.

*** =hint

*** =pre_exercise_code
```{r}
facebook <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")
facebook$Date<- as.Date(facebook$Date)
facebook$newvar<- 253:1
linreg <- lm( Open ~ newvar , data=facebook)
plot( facebook$newvar , facebook$Open, type = "p" , lwd= 3, xlab="Datum", ylab="Open" , xaxt='n')
curve( coefficients(linreg)[1] + coefficients(linreg)[2]*x , add=TRUE , col="red", lty= 2 , lwd= 2)
```

*** =sample_code
```{r}



linreg <- ___
plot(___, lwd= 3, xlab="Datum", ylab="Open" , xaxt='n')
curve( ___ , add=TRUE , ___, lty= 2 , lwd= 2)
```

*** =solution
```{r}
facebook$Date<- as.Date(facebook$Date)
facebook$newvar<- 253:1

linreg <- lm( Open ~ newvar , data=facebook)
# Pltten der Punkte und der linearen regressionskurve  
plot( facebook$newvar , facebook$Open, type = "p" , lwd= 3, xlab="Datum", ylab="Open" , xaxt='n')
curve( coefficients(linreg)[1] + coefficients(linreg)[2]*x , add=TRUE , col="red", lty= 2 , lwd= 2)
```

*** =sct
```{r}
test_object("linreg")
test_function("curve")
test_function("plot")
test_error()
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:bf8c35aafe
## lineare Regression
Sie sehen links das Ergebnis der vorherigen Aufgabe. Nun sollen Sie die Koeffizienten ablesen.

Welchen Wert hat der Koeffizient beta_0?

*** =instructions
- ca. 113
- ca. 107
- ca. 123
- ca. 97
*** =hint

*** =pre_exercise_code
```{r}
facebook <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")
facebook$Date<- as.Date(facebook$Date)
facebook$Date<- as.Date(facebook$Date)
facebook$newvar<- 253:1
linreg <- lm( Open ~ newvar , data=facebook)
plot( facebook$newvar , facebook$Open, type = "p" , lwd= 3, xlab="Datum", ylab="Open" , xaxt='n')
curve( coefficients(linreg)[1] + coefficients(linreg)[2]*x , add=TRUE , col="red", lty= 2 , lwd= 2)
```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad, msg_bad))

```

--- type:NormalExercise lang:r xp:100 skills:1 key:3c4f6d0b92
## Logit (I)
Ihnen ist der Datensatz `titanic` gegeben. 

Untersuchen Sie den Zusammenhang zwischen dem Alter und dem Geschlecht.
    

*** =instructions
- Führen Sie eine nicht lineare Schätzung mit dem logistischen Regressionsmodell durch.
*** =hint

*** =pre_exercise_code
```{r}
titanic <- Titanic

titanic <- data.frame(titanic)
# Alter zuweisen
Alter <- c()
for(i in 1:length(titanic$Age)){
  if(titanic$Age[i] == "Child"){
    Alter[i] <- sample(1:17, 1)
  }else{
    Alter[i] <- sample(18:75, 1)
  }
}
# Spalte hunzufügen
titanic$Alter <- Alter
titanic$Age <- NULL

```

*** =sample_code
```{r}
# lineare Schaetzung
reg2 <- ___
# summary()


# Plot
plot( titanic$Alter , titanic$Sex, type = "p", xlab="Alter", ylab="Geschlecht" )
curve( coefficients(reg2)[1] + coefficients(reg2)[2]*x,  add = TRUE, col="red")

```

*** =solution
```{r}
reg2 <- glm(Sex ~ Alter, data = titanic, family=binomial(link='logit'))
summary(reg2)
# Plot (Kurve wird noch nicht hinzugefügt)
plot( titanic$Alter , titanic$Sex, type = "p", xlab="Alter", ylab="Geschlecht" )
curve( coefficients(reg2)[1] + coefficients(reg2)[2]*x,  add = TRUE, col="red")

```

*** =sct
```{r}
test_object("reg2")
test_error()
```
