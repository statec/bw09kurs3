---
title       : Einheit 2 - inclass
description : Tidyverse - Aufbereiten von Datensätzen
--- type:NormalExercise lang:r xp:100 skills:1 key:4e6279614f
## SELECT
Der Datensatz der deutschen Bank wurde bereits geladen und in dem Objekt `db` gespeichert. Die Bibliothek "dplyr" ist in der gesamten Übung bereits für Sie eingebunden. 

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
test_error()
success_msg("Sehr gut! Einen kleinen Unterschied gab es dann doch zwischen select() und $. Achten Sie bei der nächsten Aufgabe besonders darauf!")

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
# In den Lösungen werden Pipes benutzt. Pipes können gerne benutzt werden, sind aber nicht notwendig.

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
test_error()
success_msg("Sehr schön! Ist Ihnen der Unterschied aufgefallen? filter() belässt das Erbegnis bei dem Typ dataframe, [ ] jedoch erstellt einen Vektor. Genau so bei select() und $.")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:cafc5b7402
## DPLYR
In dieser Aufgabe geht es um die verschiedenen Funktionen der Bibliothek `dplyr` (bereits geladen). Die Daten der deutschen Bank Aktie liegen im Objekt `db`. Die Funktionen, welche Sie benötigen, finden Sie in der Vorlesung.

Das Ziel dieser Aufgabe ist es, das am Ende die Rendite als neue Spalte in der Tabelle steht. Gehen Sie hierfür schrittweise vor.

Tipp: 
- `!=` ist ein Vergleichsoperator. `a != 1` ist wahr, wenn a ungleich 1 ist.
- Durch `select()` können Sie auf bestimmte Spalten, durch `filter()` auf Zeilen zugreifen. 
- Schauen Sie für Beispiele in die Vorlesungsfolien.

*** =instructions
- Verkleinern Sie den Datensatz mittels `select()`, sodass er nur noch Date und Open enthält.
- Sortieren Sie den Datensatz nach dem Datum.
- Benennen Sie die Spalte "Open" zu "Rate" um.
- Erstellen Sie eine neue Variable "Rendite" in der die jeweilige Tagesrendite steht.
- Orientieren Sie sich an den Anweisungen im Beispielcode.

*** =hint
- ordnen: `arrange(daten, spalte)`.
- eine neue Spalte erstellen Sie durch `mutate(daten, neueSpalte = vektor)`.
- das erste bzw. letzte Datum in der sortierten Tabelle bekommen Sie durch `head(db)` bzw. `tail(db)`.

*** =pre_exercise_code
```{r}
library(dplyr)

# Einlesen der Daten
db <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/production/course_3722/datasets/db_aktie.csv")
db$Date <- as.Date(db$Date)

```

*** =sample_code
```{r}
# Verkleinerung des Datensatzes
db <- 

# Sortieren nach Date
db <-

# Umbenennung des Wertes
db <-

# Erstellung der 2 Vektoren, die für Renditenberechnung notwendig sind
x_t <- ___[___ != "2016-04-06"]
x_tminus1 <- 

# Wir brauchen die Daten ohne die Erste Zeile (Keine Rendite berechenbar). Nutzen Sie filter().


# Fügen Sie die zwei Hilfsvektoren zu der Tabelle hinzu


# Berechnen Sie die Rendite und erstellen Sie eine neue Variable "Rendite" im Datensatz. 
daten <- 


```

*** =solution
```{r}
# Verkleinerung des Datensatzes
db <- select(db, Date, Open)

# Sortieren nach Date
db <- arrange(db, Date)

# Umbenennung des Wertes
db <- rename(db, Rate = Open)

# Erstellung der 2 Vektoren, die für Renditenberechnung notwendig sind
x_t <- db$Rate[db$Date != "2016-04-06"]
x_tminus1 <- db$Rate[db$Date != "2017-04-05"]

# Wir brauchen die Daten ohne die Erste Zeile (Keine Rendite berechenbar). Nutzen Sie filter().
db <- filter(db, Date != "2016-04-06")

# Fügen Sie die zwei Hilfsvektoren zu der Tabelle hinzu
db <- db %>% mutate(x_t = x_t, x_tminus1 = x_tminus1)

# Berechnen Sie die Rendite und erstellen Sie eine neue Variable "Rendite" im Datensatz.
daten <- db %>% mutate(Rendite = (x_t-x_tminus1)/x_tminus1)

head(daten)

```

*** =sct
```{r}
test_object("daten")
success_msg("Geschafft!")
```
