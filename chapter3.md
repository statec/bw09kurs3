---
title       : Übung 1.1
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


# Geben Sie die eingelesenen Daten in der Kosole aus

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
# test_function("read.csv", args = "x")
test_function_result("read.csv")
test_object("deutsche_bank")
test_output_contains("deutsche_bank")
test_error()
success_msg("Good work!")

```
--- type:NormalExercise lang:r xp:100 skills:1 key:8e8601a726
## Die Feiertagsproblematik

Gegeben ist Ihnen der Datensatz `aktien`. Er besteht aus den Daten von einem Jahr von sowohl der Deutschen Bank (XETRA also Deutsche Börse) und von facebook (NASDAQ also US-Börse). Durch die unterschiedlichen Feiertage in Deutschland und der USA fehlen einige Werte im Datensatz. Diese Felder sind mit `N.A.` gekennzeichnet. Um den Datensatz graphisch darstellen zu können, müssen Sie nun eine geeiegnete Möglichkeit finden, diese Felder zu füllen.

(Quelle: de.finance.yahoo.com)

*** =instructions
Ersetzen Sie die N.A. Felder in dem Datensatz durch:
- den Durchschnitt der Zeitreihe
- den Durchschnitt der umliegenden 10 Tage

*** =hint
- benutzen Sie `mean()` zur Berechnung des Durchschnitts


*** =pre_exercise_code
```{r}
# Einlesen der Daten
db_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie.csv")
fb_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")

# Zusammenführung der Daten
library(dplyr)
both <- full_join(fb_aktie, db_aktie, by = "Date")
names(both) <- gsub("x", "db", names(both))
names(both) <- gsub("y", "fb", names(both))

aktien <- arrange(both, Date)

```

*** =sample_code
```{r}
# Geben Sie den Datensatz in der Konsole aus.
aktien


```

*** =solution
```{r}
# Geben Sie den Datensatz in der Konsole aus.
print(aktien)


```

*** =sct
```{r}
test_output_contains("aktien")
test_error()

```
