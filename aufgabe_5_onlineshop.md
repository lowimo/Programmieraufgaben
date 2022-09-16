# Aufgabe 5: Onlineshop
Für einen Onlineshop soll ein Datenbankmodell (in Form von SQL-Statements) erstellt werden.
Als Datenbanksystem soll der SQL-Server von Microsoft zum Einsatz kommen.

Anforderungen:
* Bei einer Person kann Anrede, Vorname, Nachname, Geburtsdatum und eine Adresse hinterlegt werden.
* Eine Adresse besteht aus Straße, PLZ, Ort
* Der Onlineshop enthält Artikel.
* Ein Artikel besteht aus Name, Beschreibung, Netto Preis und MWst-Satz (ermäßigt/voll). Der Preis eines Artikels ändert sich im laufe der Zeit und soll historisch gespeichert werden.
* Die Eingruppierung eines Artikels in einen MWst.-Satz ändert sich nie.
* Eine Person kann beliebig oft eine Bestellung abgeben und dabei beliebig viele Artikel bestellen. Jede Bestellung hat eine Rechnungsanschrift und optional eine (abweichende) Lieferadresse. Bei einer Bestellung soll der Bestellzeitpunkt gespeichert werden.
* Der MWst-Satz (ermäßig/voll) kann sich über die Zeit ändern.
