# advanter-Mailclient (Greenprint)

2025-07-05 RW: aus E-Mail von RW an SG, MR, RB, KP

Hier ist meine erste Brainstorm der Funktionalität (eigentlich eine Mischung aus Marketing- und Entwicklungs-, und Dokumentationseinträge und -fragen) -> diese muss vervollständigt und sortiert werden, aber vor allem die Unklarheiten, Abhängigkeiten und Fragen aufarbeitet werden:

## Zu tun

- Funktionsumfang (& -abhängikeiten) genau definieren

## Microsoft 365 Mail-Sync

- Marketing Name?
- Wichtig: Mailsync mit Microsoft aber noch keine Terminsync, usw.!
- D.h. Kunden mit E-Mail- + Terminsync können noch nicht zu Microsoft 365 Sync wechseln!
  - Haben wir Bedarf diese zu trennen?
  - Bisher haben wir ein zentraler Schalter / Unterstützung von nur 1 System
  - Brauchen wir User-, bzw. E.-Mail-Konto-, orientierte Einstellungen?
- Wie unterscheidet sich dieses Systemkonfiguration von den anderen Systemkonfigurationen (Exchange, Kerio, SMTP)?  
  - A…
  - B…
  - C…

## Advanter HTML-E-Mail Kompatibilität

- Advanter HTML-E-Mails werden als ganze HTML-Seite mit CSS versendet.
- Diese ist nicht mit allen E-Mailclients kompatibel!
  - Infos benötigt…!

## Einstellungen

- Voreinst > …
  - E-Mail > Mailserver > [Zahnrad] > Exchange > Schnittstelle = "Microsoft Graph API"
  - @MR: so?
- E-Mail Konten > Microsoft 365 Reiter
- E-Mail Konten > User-Zuordnung (User-Abo)
  - 100% unterstützt?
- E-Mail Konten > Gruppe-Zuordnung (User-Abo)
  - 100% unterstützt?

## Advanter Connect

- APIs
  - MS-Graph-API
  - Usw.
  - Klären: Lizenzierung von Connect APIs?
  - Wie werden API-Funktionalität verkauft?
  - Wir wollen nicht alle APIs einfach schenken, die drin sind, oder?
  - Wie sind die überhaupt ein/auszuschalten?
- API Historie
- Callback Links
  - Marketing Name?
- Klären: Administration & Zugriff auf Connect Funktionalität?

## Archiv

- Benötigt?
- Von Connect benötigt?
- Bei G+J muss aus Connect ausgebaut werden?

## Kunden-markierte Daten ('advanter self-awareness')

- Zentralinfos (in der Konstanten-Tabelle)
  - GBS-Kunde
  - …plus DeploymentDateien, usw.?
- GBS-Kunden Tabelle mit Kunde + Test-DS
  - Klären: 
  - Benötigt Connect?
  - Notig bei G+J?
  - Ein-/Ausbauaufwand?
  - Werteliste hart kodieren? = RTL / Test
- …und 'GBS-Name' = G+J oder RTL?

## E-Mail Versand + Erfassung

- Interne HTML E-Mails (Marketing Name? 'advanter Workflow E-Mails'…?) mit
  - E-Mail Templates
  - E-Mail Buttons (Marketing Name? 'advanter Mail-to-Action Buttons'…?)
  - Callback Links
  - Darstellung strukturierter Daten (JSON als HTML Tabelle)
  - (anpassbare?) Design durch CSS
- Advanter Mailclient
  - HTML E-Mails erfassen und versenden
  - E-Mail Templates
  - Einfach auswählen für Super Look!
  - E-Mail Templates von Administrator erfasst
  - Super einfach Erfassung!
  - Text erfassen, HTML bekommen!
  - Formatierter Text mit eingebetteten Bildern ('<Screenshot.png>')
  - Text formatieren…
  - per Rechtsklick
  - per Tastenkürzel
  - Oder per Formatting Bar ein-/ausblenden
  - Bilder einbetten…
  - Anhänge in E-Mailtext mit einem Klick einbetten
  - Einfach '<dateiname.ext>' tippen, z.B. '<Screenshot.png>'
  - Frage:
  - Ist der Umgang mit dem von FileMaker fälschlicherweise eingebettetem Font-Family geklärt?
  - Solange Tahoma als Schrift für das Eingabefeld bleibt…?
  - Muss diese für künftige Entwickler dokumentiert werden?
  - (Noch?) keine Unterstützung von…
  - eingebettetem HTML
  - HTML Tabellen
  - HTML Lists
  - strukturierte Daten (wie in internen E-Mails)
  - Markdown (Überschriften wie in der Dev-DB)
  - Oder - für die Profis - per HTML Quellcode
  - Umgang noch zu klären
	1	HTML-Body im Eingabefeld  erfassen - mit Template
  - Body wird roh in Template eingefügt
	2	HTML-Body im Eingabefeld erfassen - ohne Template
  - Wird in Template eingefügt
	3	Ganzes HTML ohne Template erfassen
  - Wo?
  - In Text-Eingabefeld?
  - Oder durch Ersetzen der HTML Ausgabe komplett 
  - …aber WICHTIG: wenn das Roh-HTML im Text-Eingabefeld erfasst wird, darf der Roh-HTML NICHT im E-Mail Text-Darstellung erscheinen!
  - (Meiner Meinung nach, ist das evtl. das falsche Feld dafür)
	4	Wie werden diese unterschieden?
  - Eine weitere Einstellung für Eingabeformat benötigt?
  - Eingabeformat = (o) Text / (o) HTML
  - Meiner Meinung nach ist dieses ^^^ nötig
  - Dann könnte auch ein (o) Markdown Option geben, um Überschriften zu unterstützen (z,.B, '# Titel', '## Subtitel', … - wie in Dev-DB)

  - Wenn ja, brauchen wir auch eine Defaulteinstellung (Voreinst/User)?
  - Automatisch?
  - Ist es überhaupt möglich (oder sinnvoll)?…(Meiner Meinung: nein)
  - Ohne Template
  - Eingabe startet mit <html> oder <!DOCTYPE html> (oder…?)
  - Ausgabe = Eingabe
  - sonst
  - …
  - Mit Template…
  - HTML E-Mail-Signaturen mit bis 2 Bilder
  - Formatierter Text mit Platzhalter '<Bild 1> ' /'<Bild 2> '
  - Flexible Signaturen
  - 1 Signatur für sowohl HTML als auch für Text (Bilder werden einfach ignoriert)
  - Oder separate Signaturen
  - Signaturdefault?
  - Haben / benötigen wir eine Automatik, um Format-basierte Signaturdefault?
  - Einstellung(en) benötigt für E-Mail-Ausgabeformat Default?
  - Voreinst?
  - User?
  - Empfänger??
  - …oder hart kodiert, default immer HTML jetzt?
  - E-Mail Größe limitieren…
  - Anhang bis x MB
  - exist. Voreinstellung für einzelnen Anhängen wird nach wie vor verwendet
  - Upload von großen Anhängen (> 3MB)
  - Müssen wir Anhänge in 3MB Häppchen hochgeladen?
  - Benötigen wir…
  - Size-Limit für das ganze E-Mail?
  - Sichtbare Berechnung von der Größe?

## E-Mail Empfang / E-Mail-Sync

- Per AAS oder direkt (am Client) oder beides?
  - Geht Beide zusammen überhaupt?
  - Wie würden die URL Links funktioneren?
  - Oder Überschneidungsprobleme?
- Abfrage-Methode
  - Inkremental
  - Per Timestamp
  - Per  URL Link
  - Per Ordner
  - Unterstützt?

## App-Server Funktionalität

- E-Mail Servereinstellungen
  - Abfrage der Systemeinstellungen
  - Wird dort Microsoft 365 gezeigt?
  - Abfrage der Postfächer

## Kern Funktionalität

- Zentrale Einstellungsfelder
  - JSON CSS, usw.
- JSON Funktionen (CFs, Scripts?, …)
- HTML Funktionen (CFs, …)
- Andere Scripts?

## Fragen

- Überblick: Wie funktioniert das ganze System?
  - Einstellung von Microsoft 365?
  - API Token?
  - MS App = advanter?
  - Gleiche App für ALLE Kunden?
  - Oder muss jede Kunde/Deployment extra App in MS haben?
  - Umgang mit Microsoft Authentifizierung / OAuth Token?
  - Umgang Connect mit Authentifizierung…wird automatisch erneut, wenn Auth fails?
- Installationsdokumentation für Kundenadministrator
