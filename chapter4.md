---
title       : Einheit 2 - inclass
description : Tidyverse - Aufbereiten von Datensätzen
--- type:NormalExercise lang:r xp:100 skills:1 key:4e6279614f
## SELECT
Der Datensatz der deutschen Bank wurde bereits geladen und in dem Objekt `db` gespeichert. Die Bibliothek "dplyr" ist in der gesamten Übung bereits für Sie eingebunden. 

Sie sollen nun durch 2 verschiedene Varianten auf eine bestimmte Spalte des Datensatzes zugreifen. Nutzen Sie dafür `select()`. Schauen Sie zur Funktionsweise der Funktion in den Folien nach, oder führen Sie `?select()` in der Konsole aus.


Tipp: 
Wenn Sie eine Zeile des R-Codes aus dem Skript in der Konsole ausführen möchten, nutzen Sie den shortcut `Strg`+`Enter`, während sich der Cursor in der entsprechenden Zeile befindet. Testen Sie es! Geben Sie `db` im Skript (oben) ein und drücken Sie die beiden Tasten. Schauen Sie, was passiert.


(Quelle: yahoo/finance)
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


(Quelle: yahoo/finance)
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


(Quelle: yahoo/finance)

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



--- type:NormalExercise lang:r xp:100 skills:1 key:3923d161a1
## TIDYR
Gegeben ist ein Datensatz `daten`. Wenn Sie ihn in der Konsole ausgeben, werden Sie merken, dass die zwei Variablen Kontinent und Land gemeinsam in eine Variable geschrieben wurden. Dies sollen Sie nun durch `seperate()` ändern.
Das notwendige Paket aus tidyverse `(tidyr)` wurde für Sie bereits geladen.

(Quelle: Wikipedia)
 
*** =instructions
Erstellen Sie einen neuen Datensatz "tidyTable", in welchem Sie die Spalte ort auf zwei Spalten "land" und "kontinent" aufteilen.

*** =hint
- `seperate(df, into = c("spalte1", "spalte2"), sep = "_")`
- bei `sep = ` geben Sie das jeweilige Trennsymbol ein.

*** =pre_exercise_code
```{r}
library(tidyr)
library(dplyr)
# Erstellen der Daten
unternehmen <- c("BMW", "Sony", "AXA", "IBM", "Toyota", "Lenovo")
# Hauptsitz
ort <- c("Europa_Deutschland", "Asien_Japan", "Europa_Frankreich", "Amerika_USA", "Asien_Japan", "Asien_China")
stadt <- c("Muenchen", "Tokio", "Paris", "Armonk", "Toyota", "Peking")
daten <- data.frame(unternehmen, ort, stadt)


```

*** =sample_code
```{r}
# Erstellen Sie die neuen Spalten und speichern Sie ihr Ergebnis unter "tidyTable"

# Schauen Sie sich das Ergebnis in der Konsole an
print(tidyTable)

```

*** =solution
```{r}
# auseinander ziehen
tidyTable <- daten %>% separate(ort, into = c("kontinent", "land"), sep = "_")
# Ausgabe
print(tidyTable)

```

*** =sct
```{r}
test_object("tidyTable")
test_error()
success_msg("Sehr gut, Sie können nun Spalten auseinander ziehen.")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:b29966e91c
## TIDYR 2
Der von ihnen geänderte Datensatz ist in `daten` gegeben. Nun soll ihre Aktion mittels `unite()` wieder rückgängig gemacht werden.
Das notwendige Paket aus tidyverse `(tidyr)` wurde für Sie bereits geladen.

(Quelle: Wikipedia)
 
*** =instructions
Erstellen Sie einen neuen Datensatz "untidyTable", in welchem Sie die zwei Spalten "land" und "kontinent" zu einer Spalte "ort" vereinen. Benutzen Sie als Trennsymbol die Leertaste.

*** =hint
- `unite(df, name, spalte1, spalte2, sep = " ")`
- bei `sep = ` geben Sie das jeweilige Trennsymbol ein.

*** =pre_exercise_code
```{r}
library(tidyr)
library(dplyr)
# Erstellen der Daten
unternehmen <- c("BMW", "Sony", "AXA", "IBM", "Toyota", "Lenovo")
# Hauptsitz
ort <- c("Europa_Deutschland", "Asien_Japan", "Europa_Frankreich", "Amerika_USA", "Asien_Japan", "Asien_China")
stadt <- c("Muenchen", "Tokio", "Paris", "Armonk", "Toyota", "Peking")
# Erstellen dataframe
daten <- data.frame(unternehmen, ort, stadt)
# auseinander ziehen
daten <- daten %>% separate(ort, into = c("kontinent", "land"), sep = "_")

```

*** =sample_code
```{r}
# Vereinigen Sie die beiden Spalten zu einer neuen Spalte "ort"


```

*** =solution
```{r}
# Vereinigen Sie die beiden Spalten zu einer neuen Spalte "ort"
untidyTable <- daten %>% unite(ort, kontinent, land, sep = " ")
# Ausgabe
print(untidyTable)

```

*** =sct
```{r}
test_object("untidyTable")
test_error()

```


--- type:NormalExercise lang:r xp:100 skills:1 key:eb9e1eebd4
## GATHER
Die Daten liegen in `df`. Das was bisher oft als Tabelle bezeichnet wurde, nennt man in R "dataframe". Beim gegebenen Datensatz sind die Spaltennamen keine Variablenbezeichnungen, sondern Werte einer Variablen. Nutzen Sie die in der Vorlesung vorgestellte Funktion, um den Datensatz zu ordnen. Die notwendigen Bibliotheken wurden bereits für Sie eingebunden. 


*** =instructions
- Verschönern Sie den Datensatz wie in der Vorlesung
- Entfernen Sie unnötige Informationen durch die Funktionen, die Sie in den vorherigen Aufgaben bereits gelernt haben.
- Schauen Sie sich zur Überprüfung den Datensatz durch `print(dfTidy)` in der Konsole an.

*** =hint
- `gather(df, Wert1, Wert2, key = "___", value = "___" )`.
- Hilfe bei Funktionen bekommen Sie mit `?function()` in der Konsole.

*** =pre_exercise_code
```{r}
library(tidyr)
library(dplyr)
# Erstellen des Datensatzes
aktie <- c("Firma1", "Firma2", "Firma3")
mitarbeiter_2016 <- c(983, 1301, 457)
mitarbeiter_2017 <- c(1003, 1223, 461)
df <- data.frame(aktie, mitarbeiter_2016, mitarbeiter_2017)

```

*** =sample_code
```{r}
# Speichern Sie ihr Ergebnis in dfTidy
dfTidy <-
# Benutzen Sie separate() um die Spalte aufzuteilen in "uninteressant" und "jahr"
dfTidy <-
# Entfernen Sie die Spalte durch select()
dfTidy <-

```

*** =solution
```{r}
# Hinweis: Die Lösung benutzt Pipes, es kann aber genauso in mehr Schritten ohne Pipes gemacht werden.
# Speichern Sie ihr Ergebnis in dfTidy
dfTidy <- df %>% 
    gather(mitarbeiter_2016, mitarbeiter_2017, key = "jahr", value = "mitarbeiter")

# Benutzen Sie separate() um die Spalte aufzuteilen in "uninteressant" und "jahr"
# Entfernen Sie die Spalte durch select()
dfTidy <- dfTidy %>% 
    separate(jahr, into = c("uninteressant", "jahr"), sep = "_") %>% 
    select(aktie, jahr, mitarbeiter)

```

*** =sct
```{r}
test_object("dfTidy")
test_function("gather")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:154576692b
## SPREAD()
Der Datensatz liegt im objekt `df` und die Bibliotheken sind geladen. Nutzen Sie spread um die Zeilenanzahl zu reduzieren, sodass jedes Jahr seine eigene Spalte im dataframe bekommt.


*** =instructions
- Nutzen Sie die Funktion spread() und speichern Sie das Ergebnis in der Variablen `dfNew`.
- Vergleichen Sie den alten und neuen Datensatz durch Ausgabe in der Konsole mit `print(df)` bzw. `print(dfNew)`.

*** =hint
- `spread(df, spalte1, spalte2)`

*** =pre_exercise_code
```{r}
library(dplyr)
library(tidyr)
# Erstellung des Datensatzes
wertpapiere <- c("Aktie1", "Aktie2", "Aktie3", "Aktie1", "Aktie2", "Aktie3", "Aktie1", "Aktie2", "Aktie3")
jahr <- c("Rendite_2015", "Rendite_2015", "Rendite_2015", "Rendite_2016", "Rendite_2016", "Rendite_2016", "Rendite_2017", "Rendite_2017", "Rendite_2017")
rendite <- c(0.01, 0.03, 0.5, 0.2, 0.06, 0.31, 0.2, 0.08, 0.12)
df <-  data.frame(wertpapiere, jahr, rendite)

```

*** =sample_code
```{r}
# Reduzieren Sie die Zeilenanzahl und speichern Sie ihr Ergebnis in "dfNew".

# Schauen Sie sich beide Datensätze zum Vergleich in der Konsole an.

```

*** =solution
```{r}
# Reduzieren Sie die Zeilenanzahl und speichern Sie ihr Ergebnis in "dfNew".
dfNew <- df %>% spread(jahr, rendite)
# Schauen Sie sich beide Datensätze zum Vergleich in der Konsole an.
print(df)
print(dfNew)

```

*** =sct
```{r}
test_object(dfNew)

```
