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
