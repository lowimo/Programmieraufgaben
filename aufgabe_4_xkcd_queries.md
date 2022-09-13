# Aufgabe 4: xkcd Queries

Aufbauend auf der Idee zum Analysieren von xkcd-Comics, wollen wir diese Logik jetzt über eine REST-API
zur Verfügung stellen. Benutzer sollen Anfragen per HTTP an das Programm stellen können und die Antwort
zurückbekommen.

## Schritt 1: REST-API

Zunächst muss mal ein grundlegender Aufruf funktionieren. Baue ein Programm, dass HTTP-GET-Requests entgegennimmt
und mit einem JSON-Dokument antwortet. Das Programm soll zunächst nur auf `localhost` und einem beliebigen Port lauschen.

Wenn du dein Programm aufrufst (z.B. `http://localhost:50000/api`), soll man in der JSON-Antwort das aktuelle Datum ausgegeben bekommen:
```
{
    "currentDate": "2022-09-13"
}
```

Ich empfehle, das `ASP.NET Core Web API` Projekt-Template zu verwenden. Das Programm
aufrufen kann man z.B. über einen Browser (bei GET-Requests recht einfach) oder über ein
Tool wie `Insomnia`.

## Schritt 2: Erste Antworten

Jetzt sollen Aufrufer das Programm über eine Route aufrufen können um Infos über einen
einzelnen xkcd-Comic zu erhalten - uns genügt die Nummer, der Titel und der Prozentsatz bemalter Pixel.

Aufruf: `http://localhost:50000/single_comic/42`

Erwartete Antwort:
```
{
    "num": 42,
    "title": "Geico",
    "paintedRatio": 0.14 // z.B. wenn 14% bemalt
}
```

## Schritt 3: Mehrere Comics abfragen

Der Aufrufer soll jetzt auch gleich die Infos über mehrere Comics gleichzeitig abrufen können. Erfinde eine sinnvolle Schnittstelle, wie der Aufrufer den Request formulieren muss.

Wenn der Aufrufer z.B. die Infos über Comics 42, 100 und 123 abfragt, soll er eine
derartige Antwort bekommen:
```
[
    {
        "num": 42,
        "title": "Geico",
        "paintedRatio": 0.0 // erfundener wert
    },
    {
        "num": 100,
        "title": "Family Circus",
        "paintedRatio": 0.0
    },
    {
        "num": 123,
        "title": "Centrifugal Force",
        "paintedRatio": 0.0
    }
]
```

## Schritt 4: Filtern und Sortieren

Der Aufrufer soll jetzt zusätzlich die Comics filtern und sortieren können.

Er muss weiterhin eine Liste der Nummern angeben, die betrachtet werden sollen. Dann will er allerdings zusätzlich einen Filter für den Titel angeben können. Nur wenn der Titel eines Comics den gesuchten Filtertext enthält (Contains / Case-Insensitive) soll der Eintrag
in der Liste ausgegeben werden.

Wenn der Aufrufer die Nummer 42, 100 und 123 angibt mit dem Suchtext "circus", würde nur Comic 100 ausgegeben. Mit dem Suchtext "o" würden Comic 42 und 123 ausgegeben.

Zusätzlich soll der Aufrufer angeben können, nach welchem der drei Felder die Ausgabe sortiert sein soll und ob aufsteigend oder absteigend sortiert werden soll.

## Schritt 5: Komplexes Filtern

Ich will nun die Anfragen mit komplexeren Filtern durchführen können.

Zum Beispiel: Gebe mir alle xkcd-comics mit einer Nummer größer-gleich 42 und kleiner-gleich 100, die einen Titel haben, der länger als 6 Zeichen ist und KEIN 'x' enthält - und ich will sie absteigend nach dem bemalten Prozentsatz.

Ein anderer Aufrufer will: Geb mir alle xkcd-comics mit einer nummer kleiner 100, die durch 2 teilbar ist. Aber statt dem Feld "paintedRatio" will ich nur ein Feld "mostlyPainted", das mir ausgibt, ob der Comic mehr als 50% bemalt ist.

Bei diesem Schritt geht es darum, eine geignete Schnittstelle zu designen, die angenehm zu benutzen ist für den Aufrufer - sie muss nicht implementiert werden. Die Aufrufer werden sicherlich auch auf immer neue Ideen kommen, wie sie filtern und sortieren wollen und welche Felder sie in der Ausgabe haben wollen. Die Schnittstelle soll also so designt werden, dass sie relativ einfach um diese neuen (noch unbekannten) Anforderungen erweitert werden kann - möglichst ohne die Schnittstelle für bestehende Aufrufer zu brechen.

## Schritt 6: Schnittstelle implementieren (optional)

Wenn du eine schöne Schnittstelle in Schritt 5 designt und besprochen hast, kannst du sie schrittweise umsetzen. Das ist - je nach Design - sicherlich nicht ganz trivial.