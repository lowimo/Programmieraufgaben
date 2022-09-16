# Aufgabe 5: Onlineshop
Die folgende Aufgabe dreht sich um einen einfachen Onlineshop


## Anforderungen:
* Bei einer Person kann Anrede, Vorname, Nachname, Geburtsdatum und eine Adresse hinterlegt werden.
* Eine Adresse besteht aus Straße, PLZ, Ort
* Der Onlineshop enthält Artikel.
* Ein Artikel besteht aus Name, Beschreibung, Netto Preis und MWst-Satz (ermäßigt/voll). Der Preis eines Artikels ändert sich im laufe der Zeit und soll historisch gespeichert werden.
* Die Eingruppierung eines Artikels in einen MWst.-Satz ändert sich nie.
* Eine Person kann beliebig oft eine Bestellung abgeben und dabei beliebig viele Artikel bestellen. Jede Bestellung hat eine Rechnungsanschrift und optional eine (abweichende) Lieferadresse. Bei einer Bestellung soll der Bestellzeitpunkt gespeichert werden.
* Der MWst-Satz (ermäßig/voll) kann sich über die Zeit ändern.


## Schritt 1 - Datenbankmodell
Für einen Onlineshop soll ein Datenbankmodell (in Form von SQL-Statements) erstellt werden.
Als Datenbanksystem soll der SQL-Server von Microsoft zum Einsatz kommen.

## Schritt 2 - ADO.NET
Im nächsten Schritt soll auf das zuvor erstelle Datenbankmodell mit ADO.NET zugegriffen werden.

## Schritt 3 - Dapper
Als nächstes soll der Zugriff auf die Datenbank über Dapper (https://github.com/DapperLib/Dapper) erfolgen.

## Schritt 4 - Entity Framework Core
Als nächstes soll der Zugriff auf die Datenbank über Entity Framework Core erfolgen.
