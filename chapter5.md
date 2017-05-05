---
title       : Einheit 2 - homework
description : Hausaufgabe dataframes & joins

--- type:NormalExercise lang:r xp:100 skills:1 key:567d7068ae
## Basis Funktionen
Gegeben ist ein Datensatz `kurse`. Schauen Sie sich den Datensatz in der Konsole an. Dieser Datensatz ist nicht mehr aktuell und soll nun von Ihnen aktualisiert werden.

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

aktuell <- kurse %>% 
  filter(klausurtermin_2017 > "2017-05-01") %>%
  select(kurs, klausurtermin_2017, kursnummer) %>%
  arrange(klausurtermin_2017)

```

*** =sct
```{r}
test_object("aktuell")

```
