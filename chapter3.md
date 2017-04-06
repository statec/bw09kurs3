---
title       : Übung 1.1
description : Datenimport und grafische Darstellung
--- type:NormalExercise lang:r xp:100 skills:1 key:b94a6935a5
## Einlesen von Datensätzen in R

Datensätze kann man in R als `CSV-Datei` einlesen. Eine CSV-Datei erkennt man am Dateieinde `.csv`.
Ihnen wurde der Preisverlauf der Deutschen Bank Aktien eines Monats in einem Link hinterlegt.


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

Gegeben ist Ihnen ein Datensatz, in dem einige Werte fehlen. Diese Felder sind mit `N.A.` gekennzeichnet. Plotten Sie das Ergebnis einmal um zu sehen, wie die Zahlenreihe aussieht.


*** =instructions

*** =hint


*** =pre_exercise_code
```{r}
db_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie.csv")
fb_aktie <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/fb_aktie.csv")

# plot(db_aktie$Date, db_aktie$Open, type = "l")
# lines(db_aktie$Date, db_aktie$Open, col = "black")
# plot(fb_aktie$Date, fb_aktie$Open, type = "l")
# lines(fb_aktie$Date, fb_aktie$Open, col = "blue")

library(dplyr)
both <- full_join(fb_aktie, db_aktie, by = "Date")
names(both) <- gsub("x", "db", names(both))
names(both) <- gsub("y", "fb", names(both))

total <- 1
```

*** =sample_code
```{r}
# Geben Sie den Datensatz in der Konsole aus.


```

*** =solution
```{r}
# Geben Sie den Datensatz in der Konsole aus.
total

```

*** =sct
```{r}
test_object("total")
test_error()

```
