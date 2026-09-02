# Essensbestie

Foto vom Essen machen, optional einen Satz dazuschreiben, Naehrwerte bekommen.
Eine einzelne HTML-Datei, keine Server-Kosten, keine Registrierung ausser einem
kostenlosen Google-API-Key.

## Einrichten

1. **API-Key holen** — https://aistudio.google.com/apikey
   Mit Google-Konto anmelden, "Create API key" klicken, Schluessel kopieren.
   Kostenloses Kontingent, keine Kreditkarte noetig.
2. `index.html` oeffnen und den Key im Einrichtungs-Assistenten eintragen.
   Er wird nur im `localStorage` dieses Browsers gespeichert.

## Lokal starten

    python -m http.server 8321

Dann http://localhost:8321 oeffnen. (Direkt per Doppelklick geht auch, aber
ohne Service Worker und je nach Browser ohne Speicherung.)

## Aufs Handy bringen

Beliebiges kostenloses Static-Hosting, z.B.:

- **GitHub Pages** — Repo anlegen, Dateien hochladen, Settings > Pages > Branch `main` waehlen.
- **Netlify Drop** — https://app.netlify.com/drop, Ordner reinziehen, fertig.
- **Vercel** — `vercel` im Ordner ausfuehren.

Danach im Handy-Browser oeffnen und "Zum Startbildschirm hinzufuegen".
Dann verhaelt es sich wie eine installierte App inklusive Kamerazugriff.

Wichtig: Der API-Key steckt im Browser des jeweiligen Geraets. Wer die Seite
oeffnet, muss seinen eigenen Key eintragen — teile die Seite also ruhig,
aber nie deinen Schluessel.

## Was drin ist

- Foto (Kamera oder Galerie) + Notiz, Analyse per Gemini mit strukturierter JSON-Antwort
- Portionsfaktor (1/2 bis 2x) vor dem Speichern
- Vier Sektionen: Fruehstueck, Mittagessen, Abendessen, Snacks
- Einrichtungs-Assistent: Geschlecht, Alter, Groesse, Gewicht, Aktivitaet, Ziel
  -> Kalorienziel nach Mifflin-St-Jeor, jederzeit ueberschreibbar
- Makros als Prozentverteilung der Kalorien (Standard 50 % Kohlenhydrate,
  30 % Protein, 20 % Fett) mit Gramm-Anzeige daneben; Presets fuer Protein,
  Low Carb und Aufbau, oder frei einstellbar
- Gewicht per Plus/Minus-Stepper in 100-g-Schritten, halten beschleunigt
- Optionale Module: Wasser, Gewichtstrend, Streak, Rezeptideen
- Modell-Auswahl fragt den eigenen Key, welche Modelle er freischaltet;
  bei einem 404 schaltet die App automatisch auf ein verfuegbares um
- Rezeptvorschlaege: drei proteinreiche Ideen, die ins Restbudget des Tages passen,
  auf Wunsch direkt als Mahlzeit eintragbar
- Verlauf ueber 30 Tage, Durchschnitte, Export als JSON und CSV
- Offline-faehig per Service Worker; ohne Netz laeuft alles ausser der Analyse

## Kosten

0 Euro. Einzige Grenze ist das kostenlose Kontingent der Gemini-API
(Anfragen pro Minute und pro Tag). Fuer normalen Alltagsgebrauch reicht es
deutlich. Wenn es doch mal klemmt: unter "Mehr" auf Flash Lite umstellen.

## Daten

Alles liegt im `localStorage` des Browsers — nichts wird an einen eigenen Server
geschickt. Nur Bild und Notiz gehen zur Analyse an die Google-API.
Beim Loeschen der Browserdaten ist alles weg, also ab und zu unter
"Verlauf > Daten sichern" exportieren.

## Haftungsausschluss

Alle Naehrwerte sind Schaetzungen eines KI-Modells, keine Laboranalyse.
Fuer den Alltag gut genug, kein Ersatz fuer Kuechenwaage oder aerztlichen Rat.
