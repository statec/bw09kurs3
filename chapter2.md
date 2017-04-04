---
title       : First Try
description : Einmal nur ein bisschen Rechnen


--- type:NormalExercise lang:r xp:100 skills:1 key:abeb4f636d
## Zurück im kleinen Einmal Eins

Hier nur ein Test, wie die `Übung` aussehen könnte. 


*** =instructions
- Benutzt euer `Gehirn` und es wird wie von selbst funktionieren!


*** =hint
- Die Funktion um die Wurzel zu berechnen lautet `sqrt()`.
- Mehr Tipps gibt es nicht :)

*** =pre_exercise_code
```{r}

zahl <- 9
```

*** =sample_code
```{r}
# Ziehe die Quadrathwurzel aus der Variablen "zahl" und schreibe das Ergebnis in zahl1.


# Addiere nun 6 auf das Ergebnis und schreibe das Ergebnis in zahl0.


```

*** =solution
```{r}
# Ziehe die Quadrathwurzel aus der Variablen "zahl" und schreibe das Ergebnis in zahl1.
zahl1 <- sqrt(zahl)

# Addiere nun 6 auf das Ergebnis und schreibe das Ergebnis in zahl0.
zahl0 <- zahl1 + 6

```

*** =sct
```{r}


test_function("sqrt", args = "zahl")
              
test_object("zahl1")
test_object("zahl0")

test_error()

success_msg("Good work!")

```
