---
title       : Einheit 4 - inclass
description : ggplot

--- type:NormalExercise lang:r xp:100 skills:1 key:04384eb4ed
## 1. Plot
Sie kennen bereits die plot-Funktion, mit der Sie Datenreihen grafisch darstellen können. Nun wurde in der Vorlesung die ggplot Bibliothek eingeführt. 
Gegeben ist ihnen der Datensatz "diamonds". Darin sind verschiedene Informationen gegeben, wie zum Beispiel Karatzahl, Preis und Qualität. Schauen Sie ihn sich in der Konsole an und erstellen Sie 2 Plots - die Bibliothek ist bereits eingebunden.

Hilfe zum `plot` Befehl und den verschiedene Eingabeparametern finden Sie, indem Sie `?plot()` in der Konsole eingeben. 


*** =instructions
- Erstellen Sie einen Punkte-Plot der die Karatzahl und den Preis aus dem dataframe "diamonds". Benutzen Sie `plot()`.
- Erstellen Sie den gleichen Plot mit der ggplot-Funktion. Benutzen Sie `geom_point()`.

*** =hint
- Schauen Sie für die ggplot-Funktion ins Skript oder benutzen Sie `?ggplot()` um mehr zu erfahren.

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)
```

*** =sample_code
```{r}
# Plot mit plot(), type = "p" erstellt einen Punkteplot.
plot(___, ___, type = "p", main = "diamonds", xlab = "price", ylab = "carat")
# Plot mit ggplot() mit geom_point()
ggplot(data = ___, mapping = ___)
  

```

*** =solution
```{r}
# Plot mit plot() 
plot(diamonds$price, diamonds$carat, type = "p", main = "diamonds", xlab = "price", ylab = "carat")
# Plot mit ggplot() mit geom_point()
ggplot(data = diamonds, mapping = aes(x = carat, y = price))+
  geom_point()

```

*** =sct
```{r}
test_function("plot", args = c("x", "y", "type", "main", "xlab", "ylab") )
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_point")
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:f9dcd5853c
## 2. Plot
Im folgenden sollen Sie nur noch mit ggplot arbeiten. Die Bibliothek ist in allen folgenden Aufgaben bereits eingebunden.
Ihnen ist wieder der "diamonds" Datensatz gegeben.Bei großen Datensätze wie diesen, kann man sehr schön mit dem Parameter `alpha` arbeiten. Dieser verändert die Transparenz der Datenpunkte. 


*** =instructions
- Erstellen Sie drei Plots und variieren Sie jeweils den Wert der Transparenz (`alpha`).
- Benutzen Sie für `alpha` jeweils 1/10, 1/20 und 1/100.
- Schauen Sie sich die Unterschiede in den drei Plots an.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)

```

*** =sample_code
```{r}
# Plot mit alpha = 1/10


# Plot mit alpha = 1/20

  
# Plot mit alpha = 1/100


```

*** =solution
```{r}
# Plot mit alpha = 1/10
ggplot(data = diamonds, mapping = aes(x = carat, y = price) )+
  geom_point(alpha = 1/10)

# Plot mit alpha = 1/20
ggplot(data = diamonds, mapping = aes(x = carat, y = price) )+
  geom_point(alpha = 1/20)
  
# Plot mit alpha = 1/100
ggplot(data = diamonds, mapping = aes(x = carat, y = price) )+
  geom_point(alpha = 1/100)

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"), index = 1)
test_function("geom_point", args = c("alpha"), index = 1)
test_function("ggplot", args = c("data", "mapping"), index = 2)
test_function("geom_point", args = c("alpha"), index = 2)
test_function("ggplot", args = c("data", "mapping"), index = 3)
test_function("geom_point", args = c("alpha"), index = 3)
test_error()

```

--- type:NormalExercise lang:r xp:100 skills:1 key:e53d6f01e4
## 3. Geoms
Sie sollen nun verschiedene Geoms ausprobieren. 

*** =instructions
- Erstellen Sie einen Plot über die Karatzahl auf der x-Achse und dem Preis auf der y-Achse.
- Fügen Sie ein "geom_line" hinzu, färben Sie diese blau.
- Betiteln Sie die x-Achse mit "Karat" und die y-Achse mit "Preis".

*** =hint
- Die Achsen können durch eigene geoms betitelt werden.

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)
```

*** =sample_code
```{r}
# Plotten Sie mit ggplot()





```

*** =solution
```{r}
# Plotten Sie mit ggplot()
ggplot(data = diamonds, mapping = aes(x = carat, y = price) )+
  geom_line(color = "blue")+
  xlab("Karat")+
  ylab("Preis")

```

*** =sct
```{r}
test_function("ggplot", args = c("data", "mapping"))
test_function("geom_line", args = c("color"))
test_function("xlab")
test_function("ylab")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:d84eccfab0
## 4. Geoms
Die Qualität der Diamanten ist in der Variable "cut" gespeichert. Diese soll nun in der nächsten Grafik verwendet werden.

*** =instructions
- Erstellen Sie ein Balkendiagramm, welches die Häufigkeit der verschiedenen Qualitäten der Edelsteine zeigt.

*** =hint
- Benutzen Sie `geom_bar`

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)
```

*** =sample_code
```{r}
# Erstellen Sie ein Balkendiagramm über cut

```

*** =solution
```{r}
# Plotten Sie mit ggplot()
ggplot(data = diamonds)+
    geom_bar(mapping = aes(x = cut))
```

*** =sct
```{r}
test_function("ggplot", args = c("data"))
test_function("geom_bar", args = c("mapping"))
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:182b668adc
## 5. Lineare Regression
Erstellen Sie eine Grafik, welche die jeweiligen Datenpunkte (Karat zu Preis) darstellt. Durch eine lineare Regression können Sie nun die Abhängigkeit zwischen den beiden Variablen erkennen.

Um mehr über die Eingabeparameter von geom\_smooth zu erfahren, geben Sie `?geom_smooth()` in der Konsole ein.

*** =instructions
- Erstellen Sie einen Punkte-Plot mit der Karat Zahl auf der x-Achse und de Preis auf der y Achse.
- Fügen Sie das geom hinzu, was für eine Glättung der Funktion sorgt.
- Um eine lineare Regression zu bekommen, müssen Sie als Methode "lm" wählen.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)
```

*** =sample_code
```{r}
# Erstellen Sie eine 




```

*** =solution
```{r}
# Erstellen Sie eine 
ggplot(data = diamonds, aes(x = carat, y = price))+
  geom_point()+
  geom_smooth(method = "lm")
```

*** =sct
```{r}
test_function("ggplot", args = c("data", "aes"))
test_function("geom_point")
test_function("geom_smooth", args = c("method"))
test_error()
```


--- type:NormalExercise lang:r xp:100 skills:1 key:9039fe0643
## 6. geom_smooth
Ihnen liegt in diamonds ein verkürzter Datensatz vor. Sie sollen wieder eine Glättungsfunktion über ihre Daten legen.

Info: Bei der span Eingabe von span = 0.1 werden Warnungen in der Konsole ausgegeben. Diese können Sie einfach ignorieren.

*** =instructions
- Erstellen sie einen geom_line Plot.
- Glätten Sie die Funktion mit geom_smooth.
- Setzen Sie den span-Wert einmal auf 0.9 und einmal auf 0.1 (Warnungen ignorieren)
- Vergleichen Sie die Ergebnisplots und achten Sie besonders auf die Wirkung der verschiedenen Eingaben für den "span"-Parameter.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
library(dplyr)
data("diamonds")
diamonds <- as.data.frame(diamonds)
diamonds <- filter(diamonds, diamonds$table < 54)
```

*** =sample_code
```{r}
# Span auf 0.8



# Span auf 0.1 (Warnungen ignorieren)


```

*** =solution
```{r}
# Span auf 0.8
ggplot(data = diamonds, mapping = aes(x = carat, y = price))+
  geom_line()+
  geom_smooth(span = 0.8)
# Span auf 0.1 (Warnungen ignorieren)
ggplot(data = diamonds, mapping = aes(x = carat, y = price))+
  geom_line()+
  geom_smooth(span = 0.1)
```

*** =sct
```{r}

test_function("ggplot", args = c("data", "mapping"), index = 1)
test_function("geom_line", index = 1)
test_function("geom_smooth", args = c("span"), index = 1)
test_function("ggplot", args = c("data", "mapping"), index = 2)
test_function("geom_line", index = 2)
test_function("geom_smooth", args = c("span"), index = 2)
test_error()
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0a648e1e7d
## 7. span
Was bewirkt ein hoher Wert für den span-Parameter bei der geom_smooth Funktion?

Zur Erinnerung sind ihnen die beiden von ihnen vorher erstellten Plots gegeben - Plot 1 mit span=0.8 und Plot 2 mit span=0.1

*** =instructions
- Die Funktion wird "unruhiger".
- Die Funktion wird glatter.
- Punkte in der direkten Nachbarschaft werden stärker berücksichtigt.

*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
library(dplyr)
data("diamonds")
diamonds <- as.data.frame(diamonds)
diamonds <- filter(diamonds, diamonds$table < 54)
# Span auf 0.8
ggplot(data = diamonds, mapping = aes(x = carat, y = price))+
  geom_line()+
  geom_smooth(span = 0.8)
# Span auf 0.1 (Warnungen ignorieren)
ggplot(data = diamonds, mapping = aes(x = carat, y = price))+
  geom_line()+
  geom_smooth(span = 0.1)

```

*** =sct
```{r}
msg_bad <- "Leider falsch!"
msg_success <- "Richtig!"
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad))
```
--- type:NormalExercise lang:r xp:100 skills:1 key:8d133ae583
## 10. Funktion 
Sie haben bereits gelernt eigene Funktionen zu schreiben. Nun sollen Sie das bisherige Wissen mit dem neu gelernten verknüpfen.

*** =instructions
- Schreiben Sie eine Funktion "mean_compare"
- Die Funktion erwartet 3 Eingabeparameter: `daten`, `a` und `b`.
- Die Funktion erstellt einen Punkteplot mit `x = a` und `y = b`.
- Außerdem soll der Plot als rote Konstante über dem Punkeplot den Mittelwert des y-Wertes anzeigen. 
- Führen Sie die Funktion mit dem Datensatz "diamonds" aus. Die Eingabeparameter sind bereits vorgegeben.
*** =hint
- Sie können den Mittelwert mit `mean(vektor)` berechnen.
- Sie können die mean-Funktion innerhalb des ggplot-geoms aufrufen.

*** =pre_exercise_code
```{r}
library(ggplot2)
data("diamonds")
diamonds <- as.data.frame(diamonds)
```

*** =sample_code
```{r}
# Funktion welche einen Punkteplot angibt und die Mittelwertkonstante
mean_compare <- function(daten, a, b){



}
# Ausführung der Funktion an diamonds
mean_compare(diamonds, diamonds$carat, diamonds$price)

```

*** =solution
```{r}
# Funktion welche einen Punkteplot angibt und die Mittelwertkonstante
mean_compare <- function(daten, a, b){
ggplot(data = daten)+
  geom_point(mapping = aes(x = a, y = b))+
  geom_line(mapping = aes(x = a, y = mean(b)),  color = "red")
}
# Ausführung der Funktion an diamonds
mean_compare(diamonds, diamonds$carat, diamonds$price)
```

*** =sct
```{r}
#test_function("ggplot", args = c("data"))
#test_function("mean_compare")
#test_error()
```
