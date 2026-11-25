# CLAUDE.md – Lebensdashboard „Mein Leben“

Zwei Versionen derselben App:
- **Claude-Dashboard (Artifact)** – Hauptversion, gespeichert im Claude-Konto, synchronisiert zwischen Geräten. Link steht im Second Brain.
- **Diese PWA** – Zweitversion, Daten nur auf dem Gerät, läuft offline, veröffentlicht über GitHub Pages (siehe `README.md`).

## Regeln für Änderungen
- **Neue Funktionen kommen immer in beide Versionen.** Pascal sagt dazu im Chat: „auch in der App, Repo mein-leben“.
- Nach Änderungen an `index.html` in `sw.js` die `VERSION` erhöhen, sonst laden installierte Apps die neue Fassung nicht.
- **Kein automatischer Sync** zwischen den Versionen (technisch nicht möglich). Abgleich über „Sicherung kopieren“ → „Zusammenführen“ (ergänzt nur, Gelöschtes kann zurückkommen) oder „Ersetzen“ (überschreibt komplett).
- Das Repo ist öffentlich: keine Einträge, persönlichen Daten oder Links zum Artifact hier ablegen.
- Wochenende: Sport zählt Sa/So nicht in die Tageswertung (Bonus); der Aufgabenplaner verteilt keine Arbeit aufs Wochenende.

## Bauweg seit 2026-11-25 (eine Quelle für beide Versionen)
- Quelle: `~/Claude-Projekte/mein-leben-dashboard/dashboard.html` (nicht in diesem öffentlichen Repo, enthält Kundendaten im Block `/*SEED*/`).
- Dashboard: diese Datei mit dem Artifact-Tool auf die Dashboard-URL veröffentlichen (Link im Second Brain).
- App: `python3 ~/Claude-Projekte/mein-leben-dashboard/build_pwa.py ~/Claude-Projekte/mein-leben-dashboard/dashboard.html index.html <Version> "<Notiz>"`, dann `VERSION` in `sw.js` erhöhen, committen, pushen. Das Skript tauscht den Kopf, entfernt Konto-Sync und `/*SEED*/`, bricht bei Kundennamen ab.
- Stolperstein: Klassennamen vor Neuvergabe suchen (`.gbar` war schon der Zielbalken und hat die Navigation auf 10 px gequetscht). Optik prüfen mit Chrome headless: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --window-size=500,700 --user-data-dir=<tmp> --screenshot=<png> file://<html>` (mind. 500 px breit, auf Datei warten, Prozess danach beenden).
- Leiste mit den Bereichen: am Handy fest unten (Klasse `.areabar`), am Mac oben; Unterreiter oben. Der frühere „Leiste unsichtbar“-Fehler war die Namenskollision, nicht die feste Position.

## Aufbau seit 2026-11-25 (App-Version 20)
- Bereiche: Start (Übersicht = Frag Claude, Nächste 7 Tage, Kunden; Unterreiter Auswertung = alle Diagramme), Heute (nur Abhaken), Kalender, Arbeit (Planung, Business, Content, Prompts, Kurse), Leben (Körper inkl. Einkauf, Geld, Zuhause, Ich inkl. Menschen und Notizen).
- Alte Reiter Einkauf/Menschen/Notizen (Index 6/10/12) bleiben als leere Einträge, `MERGE` leitet sie um; eigene Karten dieser Reiter erscheinen im Zielreiter.
- Einmal-Migration `S.v10`: blendet Diese Woche/Projekte/Kunden & Akquise aus, im Dashboard auch Geburtstage und Termine & Fristen, Zuhause→Einkauf nur wenn leer. Nichts gelöscht, zurückholen über „Karten bearbeiten“.
- Listenzeilen (`.row.q`): Unteraufgaben, Mo–Fr und Löschen erst bei Hover bzw. nach Tippen auf „⋯“.

## Körper seit App-Version 22 (2026-11-25)
- **Training heute** (`train`): Tag aus dem Sport-Plan (Mo/Di/Do/Fr, Titel beginnt mit „Mo ·“ usw.), Woche im 4-Wochen-Block ab `S.blk` (Start 2026-11-19), Hinweis aus „Steigerung über 4 Wochen“. Haken nur zur Übersicht (`S.trn`), Gewicht nur per „Eintragen“ in den Verlauf.
- **„Heute trainiert“ zählt nur per Antippen** (`S.sp`), Übungseinträge zählen nicht mehr automatisch (Migration `S.v11` übernimmt alte Tage).
- **Einkaufsliste**: Abschnitte statt Unteraufgaben, Abgehaktes unten, neue Artikel per Stichwort in die Abteilung (`SHK`), „Neue Woche“ setzt Haken zurück.
- **Menüplan**: Gericht antippen zeigt das passende Rezept aus „Rezepte“ (erstes Wort des Rezepttitels). „Menüplan bearbeiten“ zeigt die normale Liste.
- Automatische Einkaufsliste aus dem Menüplan: nicht gebaut, Rezepte sind freier Text ohne Mengenliste.

## Nur im Claude-Dashboard (Stand 2026-11-25, Artifact-Version 27)
- **Navigation:** 5 Bereiche (Start, Heute, Kalender, Arbeit, Leben) mit Unterreitern, am Handy Leiste fest unten. Tagesbogen nur auf Start. Reiter-Indizes und Hash-Namen der alten 13 Reiter sind unverändert, `kalender` ist Index 13.
- **Kalender (live):** Connector „Google Calendar“ über die Fähigkeit `mcp` (list/create/update/delete_event). Agenda 60 Tage, Bearbeiten im Formular, Karte „Termine heute & morgen“ unter Heute, „Nächste 7 Tage“ auf Start.
- **Frag Claude** (Fähigkeit `sample`) auf Start: liest Termine, Top 3, Planer und Pipeline; darf Termine anlegen und ändern, aber nicht löschen.
- **Kunden-Pipeline:** neue Felder `n` (nächster Schritt) und `o` (offener Betrag), Karte „Kunden“ auf Start.
- In der PWA nicht möglich (kein Connector, kein Claude). Navigation und Kunden-Felder ließen sich übertragen.

## Funktionen (Stand: App-Version 8, 2026-11-19)
- **Heute:** Tagesbogen 7–22 Uhr, Erledigt-Quote, Routine, Top 3, Gewohnheiten (Schalter „Mo–Fr“), Fokus-Timer, Energie
- **Aufgabenplaner:** Start, Deadline, Arbeitstage und Stunden werden auf Werktage verteilt (Kapazität 5 h pro Tag); wiederkehrende Aufgaben
- **Unteraufgaben** bei allen Listen und im Planer, mit automatischem Abhaken der Hauptaufgabe
- **Übersicht:** Heatmap über 20 Wochen, Serie (Tage mit mindestens 80 %), Energie, Fokus, Geld, Ziele, Umsatz über 6 Monate, Sport, Termine, Lebensrad
- **Körper:** Sport-Haken mit Wochenleiste, Übungen mit Gewichtsverlauf und Bestwerten, Sport-Plan aus `~/Claude-Projekte/fitness/plan-aktuell.md`
- **Geld:** Kontostand, frei verfügbar, möglicher Kontostand, Zielbetrag mit Fortschritt
- **Business:** Umsatz pro Business und Monat, Kunden-Pipeline, Projekte
- **Prompts:** eigene Kategorien (Emoji + Name, sortierbar), Favoriten, Suche, Platzhalter wie `{{Name}}` werden beim Kopieren abgefragt, Nutzungszähler
- **Eigene Karten** in jedem Reiter, vorhandene ausblendbar
- Schnellerfassung und Suche (⌘K), Sicherung und Zusammenführen
