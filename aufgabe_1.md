# Aufgabe 1: Käsekuchen

Wir wollen ein kleines Programm schreiben, dass uns dabei hilft die Länge von Wörtern zu bestimmen.

## Schritt 1

Lege ein Projekt als Konsolenanwendung an.

Das Programm soll ein Wort als Kommandozeilenparameter übergeben bekommen (`args[0]`) und ausgeben, wie lang das Wort ist:

Aufruf:
```
MeinProgramm.exe Käsekuchen
```

Erwartete Ausgabe:
```
Das Wort Käsekuchen ist 10 Zeichen lang.
```

## Schritt 2

Das Programm soll jetzt gleich mehrere Worte auf einmal verarbeiten können.

Aufruf:
```
MeinProgramm.exe Käsekuchen Eis Kekse
```

Erwartete Ausgabe:
```
Das Wort Käsekuchen ist 10 Zeichen lang.
Das Wort Eis ist 3 Zeichen lang.
Das Wort Kekse ist 5 Zeichen lang.
```

## Schritt 3

Das Programm soll jetzt zusätzlich das längste und das kürzeste Wort herausfinden.

Wenn mehrere Worte gleich kurz oder lang sind, darf sich das Programm ein beliebiges aussuchen.

Aufruf:
```
MeinProgramm.exe Käsekuchen Eis Kekse
```

Erwartete Ausgabe:
```
Das Wort Käsekuchen ist 10 Zeichen lang.
Das Wort Eis ist 3 Zeichen lang.
Das Wort Kekse ist 5 Zeichen lang.
Das längste Wort ist Käsekuchen.
Das kürzeste Wort ist Eis.
```

## Schritt 4

Das Programm soll jetzt auch damit umgehen können, dass es mehrere kürzeste oder längste Worte geben kann.

Wenn es mehrere kürzeste oder längste Worte gibt, sollen diese mit einem Komma getrennt ausgegeben werden.

### Beispiel 1

Aufruf:
```
MeinProgramm.exe Käsekuchen Eis Schokokeks
```

Erwartete Ausgabe:
```
Das Wort Käsekuchen ist 10 Zeichen lang.
Das Wort Eis ist 3 Zeichen lang.
Das Wort Schokokeks ist 10 Zeichen lang.
Die längsten Worte sind Käsekuchen, Schokokeks.
Das kürzeste Wort ist Eis.
```

### Beispiel 2

Aufruf:
```
MeinProgramm.exe Käsekuchen Tiramisu Nüsse Schokokeks Torte Chips
```

Erwartete Ausgabe:
```
Das Wort Käsekuchen ist 10 Zeichen lang.
Das Wort Tiramisu ist 8 Zeichen lang.
Das Wort Nüsse ist 5 Zeichen lang.
Das Wort Schokokeks ist 10 Zeichen lang.
Das Wort Torte ist 5 Zeichen lang.
Das Wort Chips ist 5 Zeichen lang.
Die längsten Worte sind Käsekuchen, Schokokeks.
Die kürzesten Worte sind Nüsse, Torte, Chips.
```
