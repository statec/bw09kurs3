---
title       : Einheit 1 - homework
description : Hausaufgabe zum Einlesen, Analysieren und Darstellen von Daten mit R

--- type:NormalExercise lang:r xp:100 skills:1 key:a055bddcaf
## 1. Einlesen von Datensätzen

Datensätze kann man in R als `CSV-Datei` einlesen. Eine CSV-Datei erkennt man am Dateieinde `.csv`.
Ihnen wurde der Preisverlauf der Henkel Aktien eines Jahres in einem Link hinterlegt.

(Quelle: de.finance.yahoo.com)


*** =instructions

- Lesen Sie die Daten ein und speichern Sie diese in `henkel`.
- Schauen Sie sich die Daten in der Konsole an.

*** =hint
- Nutzen Sie die `read.csv()` Funktion.
- Setzen Sie den Pfad als Argument der Funktion `read.csv()` in "Anführungszeichen".
- Zum ausgeben in der Konsole reicht `henkel`.

*** =pre_exercise_code
```{r}
```

*** =sample_code
```{r}

# die Datei liegt in __________.csv


# Geben Sie die eingelesenen Daten in der Konsole aus

```

*** =solution
```{r}
# der Pfad der Datei ist 
henkel <- read.csv("___________.csv")

# Schauen Sie sich die Daten in der Konsole an
henkel

```

*** =sct
```{r}
test_function("read.csv", args = c("file"))
test_object("henkel")
test_output_contains("henkel")
test_error()
success_msg("Sehr gut!")

```


--- type:NormalExercise lang:r xp:100 skills:1 key:97f29a5b16
## 2 a) Die Feiertagsproblematik

Gegeben ist Ihnen der Datensatz `aktien`. Er besteht aus den Daten von einem Jahr sowohl von Henkel (Frankfurter Börse) und von Exxon Mobile (NYSE). Durch die unterschiedlichen Feiertage in Deutschland und der USA fehlen einige Werte im Datensatz. Diese Felder sind mit `NA` gekennzeichnet. Um den Datensatz grafisch darstellen zu können, müssen Sie eine geeiegnete Möglichkeit finden, diese Felder zu ersetzen.

(Quelle der Daten: de.finance.yahoo.com)

*** =instructions
Ersetzen Sie die NA Felder in dem Datensatz durch:

- den Durchschnitt der gesamten Zeitreihe. Hierfür können Sie die `mean()`-Funktion nutzen.
- in den [ ]-Klammern hinter der Variable stehen die Auswahlbedingungen. Beispielsweise: `spalte[is.na(spalte)]` gibt nur die Felder aus `spalte` zurück, in denen NA steht.

Nehmen Sie hierbei jeweils die Spalten henkel und exxon.

*** =hint
- `na.rm = TRUE` entfernt die NA Felder, zur Berechnung des Durchschnitts.
- `is.na(daten)` findet die NAs in den daten.
-  Zur Ausgabe in der Konsole können Sie auch `print(Objekt)` nutzen

*** =pre_exercise_code
```{r}
# Einlesen der Daten
exxon <- read.csv("_________________")
henkel <- read.csv("_________________")

# Zusammenführung der Daten
library(dplyr)
# Merging der Datensätze
aktienjoin <- full_join(exxon, henkel, by = "Date")

# Verkleinerung der Datensätze
aktien <- select(aktienjoin, Date, exxon = Open.x, henkel = Open.y )

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)
remove(aktienjoin)

# Nach Datum sortieren
aktien <- aktien[order(aktien$Date),]

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)

```

*** =sample_code
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$exxon)]
aktien$Date[is.na(aktien$henkel)]

# Ersetzen Sie NA in der Spalte 'henkel' durch den Durchschnitt der Spalte
aktien$___[is.na(___)] <- ___(___, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'exxon' durch den Durchschnitt der Spalte


# Geben Sie die geänderten Spalten in der Konsole aus


```

*** =solution
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$exxon)]
aktien$Date[is.na(aktien$henkel)]

# Ersetzen Sie NA in der Spalte 'henkel' durch den Durchschnitt der Spalte
aktien$db[is.na(aktien$henkel)] <- mean(aktien$henkel, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'exxon' durch den Durchschnitt der Spalte
aktien$fb[is.na(aktien$exxon)] <- mean(aktien$exxon, na.rm = TRUE)

# Geben Sie die geänderten Spalten in der Konsole aus
aktien$henkel
aktien$exxon

```

*** =sct
```{r}

test_function("mean", index = 1, args = c("x", "na.rm"))
test_function("mean", index = 2, args = c("x", "na.rm"))

test_object("aktien$henkel")
test_object("aktien$exxon")
test_output_contains("aktien$henkel")
test_output_contains("aktien$exxon")

test_error()
success_msg("Sehr gut!")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:cc03c69900
## 2 b) Die Feiertagsproblematik
Die Daten liegen in der Variable `aktien`. Ersetzen Sie nun die NAs im Datensatz durch den gleitenden Durchschnitt über 10 Tage. Nehmen Sie hierfür den `mean()` von den 5 vorherigen und 5 folgenden Werten. 

Nützliche R Funktionen:

- `c(1,2,3,4)` bildet einen Vektor mit dem Inhalt 1,2,3,4.
- `c(1:4)` bildet den gleichen Vektor.
- `which(a == "hallo")` gibt an, an welcher Stelle der Vektor a dem String "hallo" entspricht.


*** =instructions
Ersetzen Sie die NAs in beiden Spalten henkel und exxon durch den gleitenden 10er-Durchschnitt der jeweiligen Spalte.

Die NA-Stellen finden Sie über: 
`aktien[is.na(aktien$exxon)]`

Für Henkel analog.

*** =hint
NAs Henkel: "2016-10-31" "2016-10-03"

NAs Exxon: "2016-09-05" "2016-11-24"

*** =pre_exercise_code
```{r}
# Einlesen der Daten
henkel <- read.csv("_____________________________")
exxon <- read.csv("______________________________")

# Zusammenführung der Daten
library(dplyr)

# Merging der Datensätze
aktienjoin <- full_join(exxon, henkel, by = "Date")

# Verkleinerung der Datensätze
aktien <- select(aktienjoin, Date, exxon = Open.x, henkel = Open.y )
remove(aktienjoin)

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)

# Nach Datum sortieren
aktien <- aktien[order(aktien$Date),]

```

*** =sample_code
```{r}

# Henkel 
# Finde den Index und schreibe ihn in index1
index1 <- which(___ == "___")
# durch Durchschnitt ersetzen
aktien$henkel[___] <- ___(c(___[c((index1-___):(index1-___),(index1+___):(index1+___))]))
# Neuer Wert
aktien$henkel[___]


# Finde den Index und schreibe ihn in index2

# durch Durchschnitt ersetzen

# Neuer Wert


# Exxon 
# Finde den Index und schreibe ihn in index3

# durch Durchschnitt ersetzen

# Neuer Wert



# Finde den Index und schreibe ihn in index4

# durch Durchschnitt ersetzen

# Neuer Wert



```

*** =solution
```{r}
# Henkel
# Finde den Index 1
index1 <- which(aktien$Date == "2016-10-31")
# durch Durchschnitt ersetzen
aktien$henkel[index1] <- mean(c(aktien$henkel[c((index1-5):(index1-1),(index1+1):(index1+5))]))
# Neuer Wert
aktien$henkel[index1]

# Finde den Index 2
index2 <- which(aktien$Date == "2016-10-03")
# durch Durchschnitt ersetzen
aktien$henkel[index2] <- mean(c(aktien$henkel[c((index2-5):(index2-1),(index2+1):(index2+5))]))
# Neuer Wert
aktien$henkel[index2]


# Exxon 
# Finde den Index 3
index3 <- which(aktien$Date == "2016-09-05")
# durch Durchschnitt ersetzen
aktien$exxon[index3] <- mean(c(aktien$exxon[c((index3-5):(index3-1),(index3+1):(index3+5))]))
# Neuer Wert
aktien$exxon[index3]

# Finde den Index 4
index4 <- which(aktien$Date == "2016-11-24")
# durch Durchschnitt ersetzen
aktien$exxon[index4] <- mean(c(aktien$exxon[c((index4-5):(index4-1),(index4+1):(index4+5))]))
# Neuer Wert
aktien$exxon[index4]

```

*** =sct
```{r}
test_function("which", args = "x", index = 1)
test_function("which", args = "x", index = 2)
test_function("which", args = "x", index = 3)
test_function("which", args = "x", index = 4)
test_object("index1")
test_object("index2")
test_object("index3")
test_object("index4")
test_function("mean", index = 1, args = c("x"))
test_function("mean", index = 2, args = c("x"))
test_function("mean", index = 3, args = c("x"))
test_function("mean", index = 4, args = c("x"))
test_output_contains("aktien$henkel[index1]")
test_output_contains("aktien$henkel[index2]")
test_output_contains("aktien$exxon[index3]")
test_output_contains("aktien$exxon[index4]")
text_error()
success_msg("Sehr gut!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:8f09b2617e
## 3) Plotte die Ergebnisse
Ihre Ergebnisse aus der letzten Aufgabe sollen nun zum Vergleich der Methoden geplottet werden. Nehmen Sie hierfür die Daten der Henkel Aktie. Vergleichen Sie die Methoden der Ersetzung (Gleitender 10-er Durchschnitt und gesamt Durchschnitt). 
Zur Erinnerung: Die manipulierten Tage warem: "2016-10-31" "2016-10-03"
*** =instructions


- Gleitender 10er-Durchschnitt
- Durchschnitt gesamte Spalte

*** =hint


*** =pre_exercise_code
```{r}
# Einlesen der Daten
henkel <- read.csv("____________")
exxon <- read.csv("_____________")

# Zusammenführung der Daten
library(dplyr)

# Merging der Datensätze
aktienjoin <- full_join(facebook, deutschebank, by = "Date")

# Verkleinerung der Datensätze
aktien <- select(aktienjoin, Date, fb = Open.x, db = Open.y )

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)

# Nach Datum sortieren
aktien <- aktien[order(aktien$Date),]
aktien2 <- aktien

# Gesamten durchschnitt setzen
aktien2$fb[is.na(aktien2$fb)] <- mean(aktien2$fb, na.rm = TRUE)

# Gleitender Durchschnitt setzen
index3 <- which(aktien$Date == "2017-01-16")
aktien$fb[index3] <- mean(c(aktien$fb[c((index3-5):(index3-1),(index3+1):(index3+5))]))
index4 <- which(aktien$Date == "2017-02-20")
aktien$fb[index4] <- mean(c(aktien$fb[c((index4-5):(index4-1),(index4+1):(index4+5))]))

# Plot von facebook Aktien mit NA durch gleitenden 10er Durchschnitt ersetzt
plot(aktien$Date, aktien$fb, type = "l", main = "Facebook Aktie 2016-2017 mit gleitendem 10er-Durchschnitt", xlab = "Datum", ylab = "Eroeffnungspreis ($)")
# Plot von facebook Aktien mit NA durch gesamten Durchschnitt ersetzt
plot(aktien2$Date, aktien2$fb, type = "l", main = "Facebook Aktie 2016-2017 mit gesamt Durchschnitt", xlab = "Datum", ylab = "Eröffnungspreis ($)")

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad))

```