# Advanter Adressenstamm

Der advanter® Adressenstamm ist ein flexibles System zur Speicherung von Kunden-, Lieferanten- und sonstigen Adressdaten.

Er besteht aus mehreren miteinander verknüpften Tabellen, die eine umfassende Verwaltung von Adressinformationen ermöglichen.

## 🏠 Adressen Tabelle

Die `Adressen` Tabelle speichert Adressen / Anschriften / Firmen von Kunden, Lieferanten, Debitoren, Kreditoren und sonstigen Adressaten.

Es sind 4 Arten von Adressen, die hier  gespeichert werden:

1. Firmenadresse
2. (verknüpfte) Lieferadresse
3. (verknüpfte) Rechnungsadresse
4. Privatperson
5. Einzelhändler 🚧 FIXME - Zu klären 🚧

   1. Firma in Adresstabelle + Privatperson in Personentabelle?
   2. oder Firma + Privatperson in einer Adresse?

      - In diesem Fall sind auch weitere Ansprechpartner in der Personentabelle erlaubt?

   3. oder sind beide Möglichkeiten erlaubt?

Im Fall 2., 3. und 4. wird zusätzlich zu dem Anschrift auch die Personeninfos (wie Vorname, Nachname) in der Adressentabelle gespeichert.

## 📞 Kommunikation Tabelle

Die `Kommunikation` Tabelle speichert die Kommunikationsdaten zu den Adressen.

Verschiedene Arten von Kommunikationen, können hier gespeichert werden:

- Telefon
- Mobil
- Fax
- E-Mail
- RG-E-Mail
- Webseite
- Sonstige

## 🧑🏻📱 Personen Tabelle

Die `Personen` Tabelle speichert Ansprechpartner zu Adressen

- Details zum Mensch
- Kommunikationsdetails
  - Telefon
  - Mobil
  - Fax
  - E-Mail

## Lieferadressen und Einteilungslieferadressen

Es sind zweit Arten Lieferadressen im Einsatz in advanter®:

1. Lieferadresse
   - Die einzige Lieferadresse im Kopf des Belegs
   - Diese darf auch ein separater Ansprechpartner in der Personentabelle haben
2. Einteilungslieferadresse
   - Mehrere Einteilungslieferadresse in den Positionen des Belegs
   - Diese dürfen **keinen** separaten Ansprechpartner in der Personentabelle haben
