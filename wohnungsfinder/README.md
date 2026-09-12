# Wohnungsfinder Itzehoe

Statische Wohnungssuche für Itzehoe und den Kreis Steinburg. Läuft ohne Backend
direkt auf GitHub Pages: <https://kevinmalterer-netizen.github.io/wohnungsfinder/>

## Was die Seite kann

- **Filtern** nach Ort, Zimmern, Fläche, Kalt- und Warmmiete; sortieren u. a. nach €/m².
- **Merkliste** (★) und **Bewerbungsstatus** je Wohnung (offen / beworben / besichtigt / abgesagt / zusage).
  Beides liegt nur im `localStorage` des jeweiligen Browsers – es wird nichts hochgeladen.
- **Suchlinks** zu allen relevanten Portalen plus Hinweise zu Genossenschaften und WBS.
- **Bewerbungs-Checkliste** für die Unterlagen-Mappe.

## Angebote pflegen

Alle Daten stehen in `data/listings.json`:

```json
{
  "id": "2026-09-eichenweg",
  "titel": "3-Zimmer-Wohnung mit Balkon",
  "ort": "Itzehoe",
  "strasse": "Eichenweg 4",
  "zimmer": 3,
  "flaeche": 74,
  "kaltmiete": 620,
  "nebenkosten": 180,
  "kaution": 1860,
  "etage": "2. OG",
  "verfuegbar_ab": "2026-10-01",
  "wbs": false,
  "merkmale": ["Balkon", "Einbauküche"],
  "quelle": "ImmoScout24",
  "url": "https://…",
  "notiz": "Besichtigung am Freitag"
}
```

- `id` muss eindeutig sein – daran hängen Merkliste und Status.
- Pflicht ist nur `id` und `titel`, alles andere ist optional.
- Die drei mitgelieferten Einträge sind mit `"demo": true` markiert und blenden oben einen
  Hinweisbalken ein. Vor dem echten Einsatz löschen oder `"wohnungen": []` setzen.

Suchlinks und Umkreis-Orte stehen in `data/portals.json`. Ändert ein Portal seine
URL-Struktur, wird nur dort korrigiert.

## Lokal testen

Die Seite lädt ihre Daten per `fetch`, ein Doppelklick auf die Datei reicht daher nicht:

```bash
python3 -m http.server 8000
# http://localhost:8000/wohnungsfinder/
```
