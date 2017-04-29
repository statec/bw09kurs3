---
title       : Einheit 2 - inclass
description : Tidyverse - Aufbereiten von Datensätzen
--- type:NormalExercise lang:r xp:100 skills:1 key:4e6279614f
## Grundlegende Funktionen
Der Datensatz der deutschen Bank wurde bereits geladen und in dem Objekt `db` gespeichert. Die Bibliotheken "dplyr" und "tidyr" sind in der gesamten Übung bereits für Sie eingebunden. 

Sie sollen nun durch 2 verschiedene Varianten auf eine bestimmte Spalte des Datensatzes zugreifen. Nutzen Sie dafür `select()`. Schauen Sie zur Funktionsweise der Funktion in den Folien nach, oder führen Sie `?select()` in der Konsole aus.


Tipp: 
Wenn Sie eine Zeile des R-Codes aus dem Skript in der Konsole ausführen möchten, nutzen Sie den shortcut `Strg`+`Enter`, während sich der Cursor in der entsprechenden Zeile befindet. Testen Sie es! Geben Sie `db` im Skript (oben) ein und drücken Sie die beiden Tasten. Schauen Sie, was passiert.

*** =instructions
Um auf die `Open` Spalte des Datensatzes zuzugreifen, haben Sie lin der letzten Sitzung schon eine Möglichkeit kennen gelernt. Nutzen Sie diese, um die `Open` Spalte des Datensatzes in `spalte1` zu speichern.
Nutzen Sie außerdem die Funktion `select()`, um das gleiche Ergebnis zu erzielen.



*** =hint
- nutzen Sie `daten$spalte`
- `select(daten, spaltenname)`

*** =pre_exercise_code
```{r}
library(dplyr)
library(tidyr)

db <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie.csv")

```

*** =sample_code
```{r}
# shortcut Test

# schon bekannte Variante
spalte1 <-

# select Variante
spalte2 <-

```

*** =solution
```{r}
# shortcut Test
db

# schon bekannte Variante
spalte1 <- db$Open

# select Variante
spalte2 <- select(db, Open)

```

*** =sct
```{r}
test_object("spalte1")
test_object("spalte2")
test_function("select", args = c(".data"))

```
