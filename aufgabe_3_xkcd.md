# Aufgabe 3: xkcd

Diesmal ist das Ziel, für jeden xkcd-Comic auszurechnen, welcher Prozentsatz des Bildes bemalt ist.

Letztlich soll man das Programm so aufrufen können:
```
MeinProgramm.exe 100 10
```

Das erste Argument ist die Nummer des Comics, bei dem das Programm anfangen soll. Das zweite Argument die Anzahl, wie viele Comics das Programm verarbeiten soll.

Ausgabe (Prozentwerte sind erfunden):
```
Beginne mit Comic #100
Comic #100: 14%
Beginne mit Comic #101
Comic #101: 22%
...
```

## Schritt 1

Zunächst muss das Programm sich die Bilder der Comics mit den entsprechenden Nummern über die API von xkcd (https://xkcd.com/json.html) beschaffen.

Dazu muss sich das Programm zunächst per HTTP die Metadaten des Comics beschaffen. Beispielsweise bekommt man für den Comic #100 über die URL https://xkcd.com/100/info.0.json folgendes JSON-Dokument:

```
{
  "month": "5",
  "num": 100,
  "link": "",
  "year": "2006",
  "news": "",
  "safe_title": "Family Circus",
  "transcript": "[[Picture shows a pathway winding through trees to a sink inside a house, out to some swings and back to ths sink, out to a ball and back to the sink...]]\nCaption: Jeffy's ongoing struggle with obsessive-compulsive disorder\n{{alt text: This was my friend David's idea}}",
  "alt": "This was my friend David's idea",
  "img": "https://imgs.xkcd.com/comics/family_circus.jpg",
  "title": "Family Circus",
  "day": "10"
}
```

Dann muss das Programm das Bild über die URL aus dem `img` Feld herunterladen.

In diesem Schritt sollen die Bilder als Dateien abgelegt werden.

## Schritt 2

Nun soll das Programm für jedes Bild den bemalten Prozentsatz bestimmen - also die Anzahl Pixel im Bild, die nicht komplett leer (weiß) sind, geteilt durch die Gesamtzahl.

In diesem Schritt soll das Programm keine Dateien im Dateisystem hinterlassen. Das Programm muss die Bilder also entweder nach der Analyse wieder löschen. Oder (besser) die Bilder nur in den Arbeitsspeicher herunterladen und gar nicht erst in eine Datei schreiben.

## Schritt 3

Immer nur ein Bild nach dem anderen herunterzuladen und zu analysieren ist mir zu langsam.

Das Programm soll nun einen dritten Parameter bekommen, der angibt, wie viele Comics maximal parallel behandelt werden dürfen.

Mit dem Aufruf `MeinProgramm.exe 100 10 4` soll das Programm also die Comics 100-104 gleichzeitig herunterladen und analysieren. Sobald die Analyse eines Comics fertig ist, darf mit der Bearbeitung des nächsten begonnen werden - aber es dürfen nie mehr Comics gleichzeitig in Bearbeitung sein, als im dritten Parameter übergeben.

Da die Bearbeitung der Comics unterschiedlich lange dauern kann, könnte die Ausgabe z.B. so aussehen:

```
Beginne mit Comic #100
Beginne mit Comic #101
Beginne mit Comic #102
Beginne mit Comic #103
Comic #102: 14%
Beginne mit Comic #104
Comic #100: 22%
Comic #103: 50%
Beginne mit Comic #105
Beginne mit Comic #106
Comic #101: 6%
...
```