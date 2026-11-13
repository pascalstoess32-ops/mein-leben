# Mein Leben

Persönliches Dashboard als installierbare Handy-App (PWA): Tagesbogen, Routinen, Top 3, Fokus-Timer, Aufgabenplaner, Business, Geld, Körper, Ziele und mehr. Läuft offline. Alle Einträge bleiben nur auf dem jeweiligen Gerät (Browser-Speicher), nichts davon steht in diesem Repo.

**App:** https://pascalstoess32-ops.github.io/mein-leben/

## Installieren
- **iPhone:** Link in Safari öffnen → Teilen → „Zum Home-Bildschirm“.
- **Android:** Link in Chrome öffnen → Menü → „App installieren“.

## Daten
- **Aus dem Claude-Dashboard übernehmen:** Dort unter *Notizen → Sicherung & Daten* auf „Sicherung kopieren“ tippen, in der App an derselben Stelle einfügen und zweimal „Wiederherstellen“ tippen.
- **Regelmäßig sichern:** Die Daten liegen nur auf dem Gerät. Ab und zu „Sicherung kopieren“ und den Text z. B. in der Notizen-App ablegen.

## Veröffentlichen
GitHub Pages veröffentlicht den Branch `main` automatisch (Settings → Pages → Deploy from a branch → `main` / root).

Nach Änderungen an `index.html` in `sw.js` die `VERSION` erhöhen (z. B. `leben-v2`), damit installierte Apps die neue Fassung laden.
