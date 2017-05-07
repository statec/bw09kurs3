---
title       : Einheit 2 - homework
description : Hausaufgabe dataframes & joins

--- type:NormalExercise lang:r xp:100 skills:1 key:567d7068ae
## 1. Basis Funktionen dplyr
Gegeben ist ein Datensatz `kurse`. Schauen Sie sich den Datensatz in der Konsole an. Der Datensatz ist nicht mehr aktuell und soll nun von Ihnen aktualisiert werden. Die benötigte Bibliothek "dplyr" ist bereits für Sie eingebunden.

Tipp: 

Das Datum ist als Typ "Date" gespeichert und kann durch ganz normale Vergleichsoperatoren verglichen werden. 

Bsp: `Datum < "2017-05-01"`.


*** =instructions
Verkleinern und aktualisieren Sie den Datensatz nach folgenden Vorgaben:

- Erstellen Sie einen Datensatz `aktuell` mit allen Klausurterminen, die vor "2017-05-01" stattgefunden haben. 
- Ordnen Sie den Datensatz nach den Klausurterminen, welche noch im Datensatz vorhanden sind.

*** =hint
- `filter()` wählt bestimmte Zeilen nach angegebenen Bedingung aus. 
- `select()` wählt bestimmte Spalten aus.
- `arrange()` sortiert den Datensatz.

*** =pre_exercise_code
```{r}
library(dplyr)
# Erstellen des Datensatzes
kurse <- data.frame(kurs = c("BWL", "VWL", "Statistik", "Geldpolitik", "Personalmanagement"), klausurtermin_2016 = c("2016-04-18", "2016-05-14", "2016-05-08",  "2016-05-30", "2016-05-21"), klausurtermin_2017 = c("2017-05-03", "2017-04-28", "2017-05-04",  "2017-05-30", "2017-05-23"), kursnummer = c(201, 101, 302, 111, 206))
# Für arrange()
kurse$klausurtermin_2017 <- as.Date(kurse$klausurtermin_2017)
kurse$klausurtermin_2016 <- as.Date(kurse$klausurtermin_2016)
```

*** =sample_code
```{r}
# Entferne alle Spalten und Zeilen mit Klausurterminen die vor dem 01.05.17 stattgefunden haben. 
aktuell <-
# Sortieren Sie den neuen Datensatz nach den aktuellen Klausurterminen.

```

*** =solution
```{r}
# Entferne alle Spalten und Zeilen mit Klausurterminen die vor dem 01.05.17 stattgefunden haben. 
# Sortieren Sie den neuen Datensatz nach den aktuellen Klausurterminen.

aktuell <- filter(kurse, klausurtermin_2017 > "2017-05-01") %>% 
    select(kurs, klausurtermin_2017, kursnummer) %>% 
    arrange(klausurtermin_2017)

```

*** =sct
```{r}
test_function("select")
test_function("filter")
test_function("arrange")
test_object("aktuell")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:7a690271fe
## 2. Basis Funktionen dplyr
Der Datensatz liegt in `evaluation`. Es wurden verschiedene Studiengänge evaluiert. Nun soll von Ihnen der Durchschnitt errechnet werden.
Die Bibliothek "dplyr" wurde bereits eingebunden.


*** =instructions
Erstellen Sie mit `mutate()` eine neue Spalte, in welcher die Durchschnittsnote des jeweiligen Studienganges steht. Die Berechnung können Sie direkt in der Funktion `mutate()` ausführen:

`mutate(datensatz, name = (1*spalte1 + 2*spalte2 + ...))`.

*** =hint
Da Sie hier Zeilenweise und nicht Spaltenweise den Schnitt berechnen, können Sie nicht `mean()` benutzen, da diese Funktion einen Vektor als Eingabe erwartet.

*** =pre_exercise_code
```{r}
library(dplyr)
# Erstellung der Daten
studiengang <- c("lehramt", "mathe", "physik", "medizin", "wirtschaft", "jura", "chemie")
note_1 <- c(32, 40, 25, 33, 144, 54, 22)
note_2 <- c(201, 89, 67, 166, 244, 98, 167)
note_3 <- c(102, 23, 89, 31, 129, 77, 33)
note_4 <- c(12, 3, 33, 12, 29, 54, 19)
evaluation <- data.frame(studiengang, note_1, note_2, note_3, note_4)

```

*** =sample_code
```{r}
# Erstellen Sie den neuen Datensatz mit der neuen Spalte "durchschnitt"
evaluation1 <- 

```

*** =solution
```{r}
# Lösung
evaluation1 <- evaluation %>%
    mutate(durchschnitt = (note_1 + 2*note_2 + 3*note_3 + 4*note_4)/(note_1 + note_2 + note_3 + note_4)) %>%
    arrange(durchschnitt)

```

*** =sct
```{r}
test_function("mutate")
test_function("arrange")
test_object("evaluation1")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:c95c4d616c
## 3. Pipes
Gegeben ist der ihnen schon bekannte Datensatz `evaluation`. Die Bibliothek "dplyr" wurde eingelesen.

*** =instructions
- Verkleinern Sie den Datensatz, sodass nur noch die der Studiengang und die Durchschnittsnote ethalten sind. 
- Nennen Sie die Spalte "durschnitt" zu "Bewertung" um.
- Bei dieser Aufgabe sollen Sie pipes `%>%` benutzen. Zur Funktionsweise schauen Sie bitte in die Folien.

*** =hint
- um bestimmte Spalten auszuwählen können Sie `select(df, Spalte)` nutzen.
- Zum Umbenennen können Sie `rename(df, Name = alter_Name)` nutzen.


*** =pre_exercise_code
```{r}
library(dplyr)
# Erstellung der Daten
studiengang <- c("lehramt", "mathe", "physik", "medizin", "wirtschaft", "jura", "chemie")
note_1 <- c(32, 40, 25, 33, 144, 54, 22)
note_2 <- c(201, 89, 67, 166, 244, 98, 167)
note_3 <- c(102, 23, 89, 31, 129, 77, 33)
note_4 <- c(12, 3, 33, 12, 29, 54, 19)
evaluation <- data.frame(studiengang, note_1, note_2, note_3, note_4)
evaluation <- evaluation %>%
    mutate(durchschnitt = (note_1 + 2*note_2 + 3*note_3 + 4*note_4)/(note_1 + note_2 + note_3 + note_4)) %>%
    arrange(durchschnitt)

```

*** =sample_code
```{r}
# nutzen Sie zuerst select() und dann rename()
evaluation1 <- evaluation %>%  

```

*** =solution
```{r}
evaluation1 <- evaluation %>% 
    select(studiengang, durchschnitt) %>% 
    rename(Bewertung = durchschnitt)

```

*** =sct
```{r}
test_object("evaluation1")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:545c855428
## 4. tidyr
Gegeben ist ein Datensatz `firma`. Sie sehen im Datensatz dass die Spalte Mitarbeiter_Abteilung aus zwei verschiedenen Variablen besteht. Dies soll nun geändert werden.

Das notwendige Paket aus tidyverse "tidyr" wurde für Sie bereits geladen, ebenso wie "dplyr".

 
*** =instructions
- Erstellen Sie für jede der zwei Variablen eine eigene Spalte. 
- Fügen Sie eine Spalte zum Datensatz hinzu, der das Alter der Mitarbeiter anzeigt. 
- Führen Sie `unite()` aus und speichern Sie das Ergebnis unter "firma_alt". Benutzen Sie ein Leerzeichen als Trennsymbol.


*** =hint
- `separate(df, into = c("spalte1", "spalte2"), sep = "_")`
- bei `sep = ` geben Sie das jeweilige Trennsymbol ein.
- `mutate()` erstellt eine neue Variable im Datensatz.
- `unite(df, name, spalte1, spalte2, sep = " ")`

*** =pre_exercise_code
```{r}
library(tidyr)
library(dplyr)
# Erstellen der Daten
Mitarbeiter_id <- c(3462, 9305, 3894, 4539, 3205, 4995, 3202, 1847, 5566)
Vorname <- c("Luisa", "Christina", "Heinrich", "Xenia", "Kim", "Franco", "Simon", "Larissa", "Joseph")
Mitarbeiter_Abteilung <- c("Kamm_IT", "Donner_IT", "Lohrer_EDV", "Warm_IT", "Bose_IT", "Gustavo_HR", "Mueller_EDV", "Schnabel_EDV", "Hust_HR") 
Geburtsjahr <- c(1986, 1990, 1974, 1977, 1964, 1981, 1960, 1959, 1974)
Geschlecht <- c("W", "W", "M", "W", "M",  "M",  "M", "W", "M")
firma <- data.frame(Mitarbeiter_id, Vorname, Mitarbeiter_Abteilung, Geschlecht, Geburtsjahr)


```

*** =sample_code
```{r}
# Erstellen Sie die neuen Spalten und errechnen Sie das Alter der Personen (Die Tage/Monate sind hierbei zu vernachlässigen)
firma <- 

# Wenden Sie unite() an und speichern Sie das Ergebnis in firma_alt
firma_alt <-

```

*** =solution
```{r}
# auseinander ziehen
firma <- firma %>% 
    separate(Mitarbeiter_Abteilung, into = c("Mitarbeiter", "Abteilung"), sep = "_") %>%
    mutate(Alter = 2017 - Geburtsjahr)
# unite() anwenden
firma_alt <- unite(firma, "Mitarbeiter Abteilung", Mitarbeiter, Abteilung, sep = " ")

```

*** =sct
```{r}
test_object("firma")
test_object("firma_alt")
test_error()

```
