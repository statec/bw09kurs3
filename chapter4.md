---
title       : Einheit 2 - inclass
description : Tidyverse - Aufbereiten von Datensätzen
--- type:NormalExercise lang:r xp:100 skills:1 key:4e6279614f
## SELECT
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


--- type:NormalExercise lang:r xp:100 skills:1 key:8fb5e293ad
## SELECT & FILTER
Der Datensatz liegt wieder in `db` für Sie bereit.
Den bereits bekannten Zugriff auf eine Spalte, welche eine bestimmte Bedingung erfüllt mit `daten$spalte[condition]` kennen Sie bereits. Experimentieren Sie ein wenig damit, um sich deren Funktion wieder ins Gedächnis zu rufen. 


Genauso funktionieren `select()` + `filter()`. Informationen zu den Funktionen finden Sie im Vorlesungsskript oder wie sonst auch mit `?function()` in der Konsole.


Denken Sie an den Shortcut `Strg` + `Enter` für angenehmeres arbeiten. 

*** =instructions
Wie hoch ist der Eröffnungskurs einer Deutschen Bank Aktie am 17.03.2017?
Nutzen Sie einmal die altbekannte Variante und einmal `select()` und `filter()`.

Speichern Sie ihr Ergebnis in den vorgegebenen Variablen.

*** =hint
- Wenden Sie zuerst `filter()` und dann `select()`an.
- Geben Sie das Datum in der Form "YYYY-MM-DD" an.


*** =pre_exercise_code
```{r}
library(dplyr)
library(tidyr)

db <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie.csv")

```

*** =sample_code
```{r}
# mit $ und []
day1 <-

# mit select() und filter()
day2 <-

```

*** =solution
```{r}
# In den Lösungen werden Pipes benutzt, dies ist jedoch nicht unbedingt notwendig.

# mit $ und []
day1 <- db$Open[db$Date == "2017-03-17"]

# mit select() und filter()
day2 <- db %>%
    filter(Date == "2017-03-17") %>% 
    select(Open)


```

*** =sct
```{r}
test_object("day1")
test_object("day2")
test_function("select")
test_function("filter")

```
