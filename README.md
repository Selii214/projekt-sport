Projekt Sport & Gicht
Eine persönliche Progressive-Web-App (PWA) zur täglichen Dokumentation und automatisierten Auswertung von Harnsäurewerten, Training, Trinkmenge, Schlaf und Ernährung — mit dem Ziel, Zusammenhänge zwischen Krafttraining und Gichtanfällen datenbasiert sichtbar zu machen.
Läuft komplett offline im Browser, keine Server, keine Accounts, keine Cloud. Alle Daten bleiben ausschließlich lokal auf dem Gerät (localStorage).
⚠️ Kein medizinisches Produkt. Diese App ersetzt keine ärztliche Diagnose, Beratung oder Therapieentscheidung. Alle Berechnungen sind rein deskriptive, datenbasierte Beobachtungen (Korrelation, keine Kausalität) und dienen ausschließlich der persönlichen Dokumentation. Medizinische Entscheidungen — insbesondere zu Medikamentendosierung — liegen ausschließlich beim behandelnden Arzt.
Motivation
Bei Gicht ist Krafttraining ein zweischneidiges Schwert: Es hilft beim Muskelerhalt, kann aber durch ATP-Abbau in der arbeitenden Muskulatur, Laktat-Konkurrenz um die renale Harnsäure-Ausscheidung und Dehydration kurzfristig zu einem Harnsäureanstieg führen. Diese App wurde gebaut, um genau das für den eigenen Körper nachvollziehbar zu machen: Welche Aktivität, welche Trinkmenge, welcher Schlaf hängt bei mir persönlich mit welchen Werten zusammen — statt sich auf allgemeine Aussagen zu verlassen.
Features
📋 Trainingsplan
Zwei feste Einheiten (2× wöchentlich, Muskelerhalt-fokussiert):
Einheit A — Oberkörper
Einheit B — Unterkörper & Core
Mit Gerätenummern, Gewichten, Satz-/Wiederholungszahlen, Pausenzeiten und Fortschrittsanzeige. Übungen sind bearbeitbar (Gewicht, Gerät), neu anordbar und individuell erweiterbar.
📈 Verlauf (Protokoll)
Tägliche Erfassung von:
Harnsäure (mg/dl), Blutdruck, Puls
Aktivität heute + optional eine weitere Aktivität Vortag (siehe Dateneingabe-Konvention)
Trinkmenge, Schlafqualität, Trainingsintensität
Ernährung (Freitext) und Notizen
✅ Gicht-Check
Checkliste für vor/während/nach dem Training (Trinkmenge, Pausen, Zucker/Fructose-Verzicht) plus eine Übersicht des bereits dokumentierten Trainingseffekts.
📊 Analyse
Der Kern der App — vollständig automatisiert aus den eigenen Daten berechnet, nichts ist vorprogrammiert oder fest hinterlegt:
Analyse
Was sie zeigt
Harnsäure-Verlauf
Zeitreihe mit Zielbereich-Markierung (≤ 6,0 mg/dl)
Erweiterte Statistik
Min, Max, Median, Spannweite, Standardabweichung
Zielbereichsanalyse
Anteil im Zielbereich, Entwicklung 1. vs. 2. Hälfte des Zeitraums
Langfristige Trendanalyse
Vergleich erste/zweite Hälfte, Trendrichtung, Veränderung in %
Ø nach Einflussfaktor
Durchschnittswerte je Aktivität/Trinkmenge/Schlaf/Intensität
Erweiterte Aktivitätsanalyse
Je Aktivität: n, Ø, Min, Max, Spannweite, Abweichung vom Gesamt-Ø
Trinkmengenanalyse
Rangliste je Trinkmengen-Kategorie + Prüfung, ob mehr Trinken den Trainingsanstieg abschwächt
Schlafanalyse
Rangliste je Schlafqualität
Trainingsintensität
Rangliste je Belastungsstufe
Trainingseffekt
Anstieg nach Training, Erholungsdauer bis zum Ausgangsniveau, Ø Erholungsdauer
Automatische Musteranalyse
Kurzvergleich Training vs. Ruhe, guter vs. schlechter Schlaf
Persönliche Erkenntnisse
Automatisch: niedrigste/höchste Kategorie je Faktor + Unterschied
Automatische medizinische Hinweise
Nur angezeigt, wenn durch die Daten ausreichend belegt (z. B. Muster nach Krafttraining)
💾 Sicherung
JSON-Export/-Import — vollständige Datensicherung (Protokolle, Trainingslog, Nierenwerte, Plangewichte, Reihenfolge)
CSV-Export — für Tabellenkalkulation
Claude-Export — kompletter Textexport (Rohdaten + alle Analysen) zur Weiterverarbeitung mit einem LLM, z. B. für vertiefende Nachfragen zur eigenen Datenlage
Dateneingabe-Konvention
Wichtig für das Verständnis der Auswertung:
Aktivität heute (a) beschreibt, was am Tag der Eingabe passiert (bzw. passieren soll) — ihre physiologische Wirkung zeigt sich typischerweise erst im Harnsäurewert des Folgetags.
Weitere Aktivität Vortag (a2, optional) beschreibt den Tag vor der morgendlichen Messung — sie gehört zum eigenen Harnsäurewert dieses Eintrags.
Blutdruck & Puls werden am Messtag selbst erfasst.
Alle Analysen berücksichtigen diesen Zeitversatz automatisch korrekt.
Messroutine
Harnsäure wird morgens zwischen 06:30–08:00 Uhr, nüchtern gemessen.
Seit 14.07.2026 wird nicht mehr täglich gemessen, sondern gezielt an Trainingstagen, den beiden Folgetagen oder bei subjektiv vermutetem Anstieg. Datenlücken an unauffälligen Tagen sind daher gewollt, keine fehlenden Daten — die App weist bei einigen Auswertungen (z. B. Erholungsdauer) explizit darauf hin, wenn ein Wert wegen fehlender Folgemessung nicht ermittelbar ist.
Technischer Aufbau
Single-File-App: Die komplette Anwendung (HTML, CSS, JavaScript) liegt in einer einzigen index.html — kein Build-Prozess, kein Bundler, keine Abhängigkeiten zur Laufzeit.
Datenhaltung: localStorage des Browsers. Keine Datenübertragung an einen Server.
Hosting: Statisch über GitHub Pages ausgeliefert.
Projektstruktur
Code
Tests
test.js lädt die echte index.html per jsdom und prüft die zentralen Analysefunktionen (Aktivitäts-Gruppierung, Trainingseffekt-Erkennung, Trend-/Zielbereichsberechnung, Migrationen etc.) gegen feste, von Hand nachgerechnete Beispieldaten. Kein Nachbau der Logik — es werden die tatsächlichen Funktionen aus der App aufgerufen.
Bash
Ist reines Entwicklungswerkzeug, kein Teil der ausgelieferten App.
Verwendung
Repo per GitHub Pages veröffentlichen (Settings → Pages → Branch auswählen) oder index.html lokal im Browser öffnen.
Auf dem Smartphone: Seite öffnen und über den Browser „Zum Startbildschirm hinzufügen", um sie wie eine App zu nutzen.
Backups regelmäßig über Sicherung → Datensicherung → JSON-Export anlegen, da alle Daten nur lokal im Browser gespeichert sind (Löschen der Browserdaten löscht auch die Einträge).
Hinweis zu Opera Mobile (Android): Der JSON-Export kann dort als leere Datei (0 B) ankommen — eine bekannte Einschränkung des Android-Downloadmanagers mit blob:-URLs in Opera, kein Fehler der App. Empfehlung: Brave oder Chrome als Browser für den Export verwenden.
Lizenz
Privates Projekt zur persönlichen Gesundheitsdokumentation. Keine Lizenz für die Weiterverwendung als medizinisches Hilfsmittel vorgesehen — bei Interesse an Nachnutzung bitte vorher Kontakt aufnehmen.
