---
title       : Fail Übung
description : Datenimport und grafische Darstellung
--- type:NormalExercise lang:r xp:100 skills:1 key:b94a6935a5
## Einlesen von Datensätzen in R

Datensätze kann man in R als `CSV-Datei` einlesen. Eine CSV-Datei erkennt man am Dateieinde `.csv`.
Ihnen wurde der Preisverlauf der Deutschen Bank Aktien eines Monats in einem Link hinterlegt.

(Quelle: de.finance.yahoo.com)


*** =instructions

- Lesen sie die Daten ein und speichern Sie diese in `deutsche_bank`.
- Schauen Sie sich die Daten in der Konsole an.

*** =hint
- Nutzen Sie die `read.csv()` Funktion.
- Setzen Sie den Pfad als Argument der Funktion in "Anführungszeichen".
- Zum ausgeben in der Konsole reicht `deutsche_bank`.

*** =pre_exercise_code
```{r}
```

*** =sample_code
```{r}

# die Datei liegt in http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/table.csv


# Geben Sie die eingelesenen Daten in der Konsole aus

```

*** =solution
```{r}
# der Pfad der Datei ist http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/table.csv
deutsche_bank <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/table.csv")

# Schauen Sie sich die Daten in der Konsole an
deutsche_bank

```

*** =sct
```{r}
test_function("read.csv", args = c("file"))
test_object("deutsche_bank")
test_output_contains("deutsche_bank")
test_error()
success_msg("Good work!")

```
--- type:NormalExercise lang:r xp:100 skills:1 key:8e8601a726
## Die Feiertagsproblematik

Gegeben ist Ihnen der Datensatz `aktien`. Er besteht aus den Daten von einem Jahr von sowohl der Deutschen Bank (XETRA also Deutsche Börse) und von facebook (NASDAQ also US-Börse). Durch die unterschiedlichen Feiertage in Deutschland und der USA fehlen einige Werte im Datensatz. Diese Felder sind mit `NA` gekennzeichnet. Um den Datensatz graphisch darstellen zu können, müssen Sie nun eine geeiegnete Möglichkeit finden, diese Felder zu füllen.

(Quelle der Daten: de.finance.yahoo.com)

*** =instructions
Ersetzen Sie die NA Felder in dem Datensatz durch:

- den Durchschnitt der Zeitreihe.

Nehmen Sie hierbei jeweils die Spalte db und fb.

*** =hint
- benutzen Sie `mean()` zur Berechnung des Durchschnitts
- `na.rm = TRUE` entfernt die NA Felder, zur Berechnung des Durchschnitts
- `is.na` findet die NA Felder


*** =pre_exercise_code
```{r}
# Einlesen der Daten
db_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/default.csv")
fb_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")

# Zusammenführung der Daten
library(dplyr)
library(plyr)
both <- full_join(fb_aktie, db_aktie, by = "Date")

# Sortieren und Verkleinerung des Datensatzes (Übersichtlichkeit)
names(both) <- gsub("y", "db", names(both))
names(both) <- gsub("x", "fb", names(both))

aktien <- arrange(both, Date)

aktien$High.db <- NULL
aktien$High.fb <- NULL
aktien$Low.db <- NULL
aktien$Low.fb <- NULL
aktien$Close.db <- NULL
aktien$Close.fb <- NULL
aktien$Volume.db <- NULL
aktien$Volume.fb <- NULL
aktien$Adj.Close.db <- NULL
aktien$Adj.Close.fb <- NULL

aktien <- rename(aktien, c("Open.fb" = "fb", "Open.db" = "db"))

```

*** =sample_code
```{r}
# Ersetzen Sie NA in der Spalte db durch den Durchschnitt der Spalte

# Ersetzen Sie NA in der Spalte fb durch den Durchschnitt der Spalte

# Geben Sie die geänderten Spalten in der Konsole aus




```

*** =solution
```{r}
# ersetzen Sie NA in der Spalte db
aktien$db[is.na(aktien$db)] <- mean(aktien$db, na.rm = TRUE)

# ersetzen Sie NA in der Spalte fb
aktien$fb[is.na(aktien$fb)] <- mean(aktien$fb, na.rm = TRUE)

# Geben Sie die geänderten Spalten aus
print(aktien$db)
print(aktien$fb)



```

*** =sct
```{r}
test_function("mean", args = c("na.rm"), index = 1)
test_function("mean", args = c("na.rm"), xindex = 2)
test_object("aktien")
test_output_contains("aktien$db")
test_output_contains("aktien$fb")

test_data_frame("aktien", columns = "db")

test_error()

```


--- type:NormalExercise lang:r xp:100 skills:1 key:df299a2957
## Die Feiertagsproblematik

Gegeben ist wieder der Datensatz `aktien`. Nun sollen die `NA` Felder mit einer alternativen Möglichkeit gefüllt werden.

(Quelle der Daten: de.finance.yahoo.com)

*** =instructions

Ersetzen Sie die NA Felder in dem Datensatz durch:

- den Durchschnitt der 10 umliegenden Werte (5 vorher, 5 nachher).

Nehmen Sie hierbei wieder die Spalten db und fb.

*** =hint

- benutzen Sie `mean()` zur Berechnung des Durchschnitts
- `na.rm = TRUE` entfernt die NA Felder, zur Berechnung des Durchschnitts
- `is.na` findet die NA Felder

*** =pre_exercise_code
```{r}

# Einlesen der Daten
db_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/default.csv")
fb_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")

# Zusammenführung der Daten
library(dplyr)
library(plyr)
both <- full_join(fb_aktie, db_aktie, by = "Date")

# Sortieren und Verkleinerung des Datensatzes (Übersichtlichkeit)
names(both) <- gsub("x", "db", names(both))
names(both) <- gsub("y", "fb", names(both))

aktien <- arrange(both, Date)

aktien$High.db <- NULL
aktien$High.fb <- NULL
aktien$Low.db <- NULL
aktien$Low.fb <- NULL
aktien$Close.db <- NULL
aktien$Close.fb <- NULL
aktien$Volume.db <- NULL
aktien$Volume.fb <- NULL
aktien$Adj.Close.db <- NULL
aktien$Adj.Close.fb <- NULL

aktien <- rename(aktien, c("Open.fb" = "fb", "Open.db" = "db"))


```

*** =sample_code
```{r}

# Ersetzen Sie NA in der Spalte db durch den Durchschnitt der umliegenden 10 Werte

# Ersetzen Sie NA in der Spalte fb durch den Durchschnitt der umliegenden 10 Werte

# Geben Sie die geänderten Spalten in der Konsole aus



```

*** =solution
```{r}



```

*** =sct
```{r}

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:32b357f9bd
## Vergleich der Methoden
Sie sehen rechts die Zeitreihen der deutschen Bank für ein Jahr geplottet. Einmal wurden die NAs durch den Gesamtdurchschnitt der Zahlenreihe ersetzt, das andere mal durch den gleitenden Mittelwert der umliegenden 10 Tage.

*** =instructions
Welche Methode halten Sie für sinnvoller?

*** =hint

*** =pre_exercise_code
```{r}


```

*** =sct
```{r}

```
