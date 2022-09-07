# Aufgabe 2: ISINs auflösen

Als Investor lese ich ständig Wirtschaftsnews, aber weil ich nur ein 56k-Modem habe, lasse ich mir die News als einfache Textdateien ohne HTML oder ähnlichem liefern. In den Textdateien werden oft Firmen anhand ihrer Wertpapier-Nummern (ISINs) genannt. Zum Beispiel so:

```
Gerade habe ich erfahren, dass der Hausmeister bei DE0007100000 den Schlüssel verlegt hat und deshalb heute nicht gearbeitet werden kann. IE00BZ12WP82 geht die Luft aus.
```

Weil ich mir die Nummern nicht merken kann, soll ein Programm mittels Regex automatisch die ISINs finden, aus einer händisch gepflegten Liste die dazugehörige Firma raussuchen, und im Text ergänzen.


## Schritt 1: ISINs identifizieren

Wir wollen zunächst alle Wertpapiere im Text identifizieren. Das Programm soll alle Tokens (Substrings) aus dem Text ausgeben, die dem Format einer ISIN entsprechen.

Erwartete Ausgabe:

```
DE0007100000
IE00BZ12WP82
```

## Schritt 2: Prüfen, ob ISINs korrekt sind

Die letzte Stelle einer ISIN ist eine Prüfziffer, mit der man schnell Tippfehler oder Ähnliches erkennen kann.

Das Programm soll so erweitert werden, dass es nur ISINs ausgibt, deren Format korrekt ist (egal, ob sie tatsächlich existieren).

## Schritt 3: Firma finden und im Text einsetzen

Das Programm soll nun für jede ISIN die dazugehörige Firma suchen und im Text einfügen. Die nötigen Daten zur Zuordnung sollen aus einer weiteren Textdatei kommen, die man händisch pflegen muss.

Beispiel:
```
MeinProgramm.exe news.txt firmen.txt
```

Inhalt von firmen.txt:
```
DE0007100000 = Mercedes Benz Group ADR
IE00BZ12WP82 = Linde PLC
```

Erwartete Ausgabe:
```
Gerade habe ich erfahren, dass der Hausmeister bei Mercedes Benz Group ADR (DE0007100000) den Schlüssel verlegt hat und deshalb heute nicht gearbeitet werden kann. Linde PLC (IE00BZ12WP82) geht die Luft aus.
```