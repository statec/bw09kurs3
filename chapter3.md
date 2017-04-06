---
title       : Datenimport
description : Übung 1.1
--- type:NormalExercise lang:r xp:100 skills:1 key:b94a6935a5
## Einlesen von Datensätzen in R

Datensätze kann man in R als `CSV-Datei` einlesen. Eine CSV-Datei erkennt man am Dateieinde `.csv`.
Ihnen wurde der Preisverlauf der Deutschen Bank Aktien eines Jahres in einem Link hinterlegt.


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
