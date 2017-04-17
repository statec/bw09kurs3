---
title       : 1. Übung
description : Übungen zum Einlesen, Analysieren und Darstellen von Daten
--- type:NormalExercise lang:r xp:100 skills:1 key:34f28f22ca
## Einlesen von Datensätzen in R

Datensätze kann man in R als `CSV-Datei` einlesen. Eine CSV-Datei erkennt man am Dateieinde `.csv`.
Ihnen wurde der Preisverlauf der Deutschen Bank Aktien eines Jahres in einem Link hinterlegt.

(Quelle: de.finance.yahoo.com)


*** =instructions

- Lesen Sie die Daten ein und speichern Sie diese in `deutschebank`.
- Schauen Sie sich die Daten in der Konsole an.

*** =hint
- Nutzen Sie die `read.csv()` Funktion.
- Setzen Sie den Pfad als Argument der Funktion `read.csv()` in "Anführungszeichen".
- Zum ausgeben in der Konsole reicht `deutschebank`.

*** =pre_exercise_code
```{r}
```

*** =sample_code
```{r}

# die Datei liegt in http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie_Feiertage2NA.csv


# Geben Sie die eingelesenen Daten in der Konsole aus

```

*** =solution
```{r}
# der Pfad der Datei ist 
deutschebank <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie_Feiertage2NA.csv")

# Schauen Sie sich die Daten in der Konsole an
deutschebank

```

*** =sct
```{r}
test_function("read.csv", args = c("file"))
test_object("deutschebank")
test_output_contains("deutschebank")
test_error()
success_msg("Good work!")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:38a63c90da
## Die Feiertagsproblematik

Gegeben ist Ihnen der Datensatz `aktien`. Er besteht aus den Daten von einem Jahr von sowohl der Deutschen Bank (XETRA also Deutsche Börse) und von facebook (NASDAQ also US-Börse). Durch die unterschiedlichen Feiertage in Deutschland und der USA fehlen einige Werte im Datensatz. Diese Felder sind mit `NA` gekennzeichnet. Um den Datensatz grafisch darstellen zu können, müssen Sie eine geeiegnete Möglichkeit finden, diese Felder zu ersetzen.

(Quelle der Daten: de.finance.yahoo.com)

*** =instructions
Ersetzen Sie die NA Felder in dem Datensatz durch:

- den Durchschnitt der gesamten Zeitreihe. Hierfür können Sie die `mean()`-Funktion nutzen.
- in den [ ]-Klammern hinter der Variable stehen die Auswahlbedingungen. Beispielsweise: `spalte[is.na(spalte)]` gibt nur die Felder aus `spalte` zurück, in denen NA steht.

Nehmen Sie hierbei jeweils die Spalten db und fb.

*** =hint
- `na.rm = TRUE` entfernt die NA Felder, zur Berechnung des Durchschnitts.
- `is.na(daten)` findet die NAs in den daten.
-  Zur Ausgabe in der Konsole können Sie auch `print(Objekt)` nutzen

*** =pre_exercise_code
```{r}
# Einlesen der Daten
deutschebank <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie_Feiertage2NA.csv")
facebook <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie2NA.csv")

# Zusammenführung der Daten
library(dplyr)

# Merging der Datensätze
aktienjoin <- full_join(facebook, deutschebank, by = "Date")

# Verkleinerung der Datensätze
aktien <- select(aktienjoin, Date, fb = Open.x, db = Open.y )
remove(aktienjoin)
remove(facebook)
remove(deutschebank)

# Nach Datum sortieren
aktien <- aktien[order(aktien$Date),]

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)

```

*** =sample_code
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$fb)]
aktien$Date[is.na(aktien$db)]

# Ersetzen Sie NA in der Spalte 'deutsche' durch den Durchschnitt der Spalte
aktien$___[is.na(___)] <- ___(___, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'face' durch den Durchschnitt der Spalte


# Geben Sie die geänderten Spalten in der Konsole aus


```

*** =solution
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$fb)]
aktien$Date[is.na(aktien$db)]

# Ersetzen Sie NA in der Spalte 'deutsche' durch den Durchschnitt der Spalte
aktien$db[is.na(aktien$db)] <- mean(aktien$db, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'face' durch den Durchschnitt der Spalte
aktien$fb[is.na(aktien$fb)] <- mean(aktien$fb, na.rm = TRUE)

# Geben Sie die geänderten Spalten in der Konsole aus
aktien$db
aktien$fb

```

*** =sct
```{r}

test_function("mean", index = 1, args = c("x", "na.rm"))
test_function("mean", index = 2, args = c("x", "na.rm"))

test_object("aktien$db")
test_object("aktien$fb")
test_output_contains("aktien$db")
test_output_contains("aktien$fb")

test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:cc03c69900
## Die Feiertagsproblematik
Die Daten liegen in der Variable `aktien`. Ersetzen Sie nun die NAs im Datensatz durch den gleitenden Durchschnitt über 10 Tage. Nehmen Sie hierfür den `mean()` von den 5 vorherigen und 5 folgenden Werten. 

Nützliche R Funktionen:

- `c(1,2,3,4)` bildet einen Vektor mit dem Inhalt 1,2,3,4.
- `c(1:4)` bildet den gleichen Vektor.
- `which(a == "hallo")` gibt an, an welcher Stelle der Vektor a dem String "hallo" entspricht.


*** =instructions
Ersetzen Sie die NAs in beiden Spalten db und fb durch den gleitenden 10er-Durchschnitt der jeweiligen Spalte.

Die NA-Stellen finden Sie über: 
`aktien[is.na(aktien$db)]`
Für Facebook analog.

*** =hint
NAs deutschebank (db): "2016-04-14" "2016-10-31"

NAs facebook (fb): "2017-01-16" "2017-02-20"

*** =pre_exercise_code
```{r}
# Einlesen der Daten
#deutschebank <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie_Feiertage2NA.csv")
#facebook <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie2NA.csv")

# Zusammenführung der Daten
#library(dplyr)

# Merging der Datensätze
#aktienjoin <- full_join(facebook, deutschebank, by = "Date")

# Verkleinerung der Datensätze
#aktien <- select(aktienjoin, Date, fb = Open.x, db = Open.y )
#remove(aktienjoin)
#remove(facebook)
#remove(deutschebank)

# class Datum setzen
#aktien$Date <- as.Date(aktien$Date)

# Nach Datum sortieren
#aktien <- aktien[order(aktien$Date),]

```

*** =sample_code
```{r}

# deutschebank  (db)
# Finde den Index und schreibe ihn in index1
#index1 <- which(___ == "___")
# durch Durchschnitt ersetzen
#aktien$db[___] <- ___(c(___[c((index1-___):(index1-___),(index1+___):(index1+___))]))
# Neuer Wert
#aktien$db[___]


# Finde den Index und schreibe ihn in index2

# durch Durchschnitt ersetzen

# Neuer Wert


# facebook (fb)
# Finde den Index und schreibe ihn in index3

# durch Durchschnitt ersetzen

# Neuer Wert



# Finde den Index und schreibe ihn in index4

# durch Durchschnitt ersetzen

# Neuer Wert


```

*** =solution
```{r}
# Deutschebank
# Finde den Index 1
#index1 <- which(aktien$Date == "2016-04-14")
# durch Durchschnitt ersetzen
#aktien$db[index1] <- mean(c(aktien$db[c((index1-5):(index1-1),(index1+1):(index1+5))]))
# Neuer Wert
#aktien$db[index1]

# Finde den Index 2
#index2 <- which(aktien$Date == "2016-10-31")
# durch Durchschnitt ersetzen
#aktien$db[index2] <- mean(c(aktien$db[c((index2-5):(index2-1),(index2+1):(index2+5))]))
# Neuer Wert
#aktien$db[index2]


# Facebook 
# Finde den Index 3
#index3 <- which(aktien$Date == "2017-01-16")
# durch Durchschnitt ersetzen
#aktien$fb[index3] <- mean(c(aktien$fb[c((index3-5):(index3-1),(index3+1):(index3+5))]))
# Neuer Wert
#aktien$fb[index3]

# Finde den Index 4
#index4 <- which(aktien$Date == "2017-02-20")
# durch Durchschnitt ersetzen
#aktien$fb[index]4 <- mean(c(aktien$fb[c((index4-5):(index4-1),(index4+1):(index4+5))]))
# Neuer Wert
#aktien$fb[index4]

```

*** =sct
```{r}
#test_function("which", args = "x", index = 1)
#test_function("which", args = "x", index = 2)
#test_function("which", args = "x", index = 3)
#test_function("which", args = "x", index = 4)
#test_object("index1")
#test_object("index2")
#test_object("index3")
#test_object("index4")
#test_function("mean", index = 1, args = c("x"))
#test_function("mean", index = 22 args = c("x"))
#test_function("mean", index = 3, args = c("x"))
#test_function("mean", index = 4, args = c("x"))
#test_output_contains("aktien$fb[index1]")
#test_output_contains("aktien$fb[index2]")
#test_output_contains("aktien$fb[index3]")
#test_output_contains("aktien$fb[index4]")
```
