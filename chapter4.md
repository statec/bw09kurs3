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

Nehmen Sie hierbei jeweils die Spalten deutsche und face.

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
aktien <- select(aktienjoin, Date, face = Open.x, deutsche = Open.y )

# Nach Datum sortieren
aktien <- aktien[order(aktien$Date),]

# class Datum setzen
aktien$Date <- as.Date(aktien$Date)

```

*** =sample_code
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$face)]
aktien$Date[is.na(aktien$deutsche)]

# Ersetzen Sie NA in der Spalte 'deutsche' durch den Durchschnitt der Spalte
aktien$___[is.na(___)] <- ___(___, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'face' durch den Durchschnitt der Spalte


# Geben Sie die geänderten Spalten in der Konsole aus


```

*** =solution
```{r}
# Schaue, an welchen Tagen sich NAs befinden
aktien$Date[is.na(aktien$face)]
aktien$Date[is.na(aktien$deutsche)]

# Ersetzen Sie NA in der Spalte 'deutsche' durch den Durchschnitt der Spalte
aktien$deutsche[is.na(aktien$deutsche)] <- mean(aktien$deutsche, na.rm = TRUE)

# Ersetzen Sie NA in der Spalte 'face' durch den Durchschnitt der Spalte
aktien$face[is.na(aktien$face)] <- mean(aktien$face, na.rm = TRUE)

# Geben Sie die geänderten Spalten in der Konsole aus
aktien$deutsche
aktien$face

```

*** =sct
```{r}
test_function("mean", args = c("na.rm"), index = 1, not_called_msg = "Are you shure you have called 'mean()'?")
test_function("mean", args = c("na.rm"), index = 2)
#test_object("aktien")
test_object("aktien$deutsche")
test_object("aktien$face")
#test_output_contains("aktien$deutsche")
#test_output_contains("aktien$face")

#test_data_frame("aktien", columns = "deutsche")

test_error()

```

*** =sct
```{r}

```
