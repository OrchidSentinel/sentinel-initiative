# sentinel-initiative

Content des **„Sentinel"-Tablets** — ein mehrseitiges In-World-Terminal der
*Sentinel Initiative* (Akten/Incident-Datenbank, Sonar, Terminal-Optik).

**Reiner Content** (HTML + Bild), doppelt nutzbar aus einer Quelle:

1. **Website** über GitHub Pages.
2. **In-Game** als Tablet — eingebunden als Git-Submodule der Sammel-Resource
   **`BIRP_Tablet`** (`OrchidSentinel/BIRP_Tablet`), die Rahmen, NUI-Focus,
   Öffnen/Schließen und das ox_inventory-Item (`sentinel_tablet`) stellt.

## Seiten

Einstieg: **`index.html`**. Navigation über relative Links:

```
index ──► access-incident ──► index
index ──► incident-77A ──► (index | terminal)
terminal ──► (access-incident | sonar)
incident-archive ──► index
```

| Datei                   | Inhalt                          |
|-------------------------|---------------------------------|
| `index.html`            | Einstieg / Datenbank-Übersicht  |
| `terminal.html`         | Terminal-Ansicht                |
| `incident-77A.html`     | Vorfall-Akte                    |
| `incident-archive.html` | Archiv                          |
| `access-incident.html`  | Zugriffsseite                   |
| `sonar.html`            | Sonar-Ansicht                   |
| `akte-u-boot.png`       | Bild-Asset                      |

## Im Spiel

Kein eigener Code nötig — `BIRP_Tablet` lädt `index.html` in den Tablet-Rahmen.
Änderungen hier landen nach `git submodule update --remote` direkt im Spiel.
Schließen: **ESC** oder **DISCONNECT**.

## Regeln für Änderungen (Entwickler & KI)

Damit es im Spiel-iframe **und** auf GitHub Pages funktioniert:

1. **Nur reiner Content** (HTML/CSS/JS/Assets) — **kein** `fxmanifest.lua`,
   `client.lua`, `nui.js` oder sonstige FiveM-Glue.
2. **Einstieg bleibt `index.html`** im Root.
3. **Nur relative Links/Assets** (`seite.html`, nicht `/seite.html`).
4. **Muss standalone im Browser laufen** — nicht auf die Hülle verlassen.
5. **Kein `cfx-nui-<name>`** hartkodieren; falls je nötig: `GetParentResourceName()`.
6. **Keine eigene Schließen-/Focus-Logik** — das macht `BIRP_Tablet`.

Gesamtarchitektur: siehe README von `OrchidSentinel/BIRP_Tablet`.
