# IronQuest — iPhone Setup Anleitung

## Option 1: Gleiches WLAN (einfachste Methode)

Mac und iPhone müssen im selben WLAN sein.

1. **Server starten** auf dem Mac (Terminal):
   ```bash
   cd ~/Desktop/IronQuest && python3 -m http.server 8888
   ```

2. **Aktuelle IP herausfinden** (Terminal):
   ```bash
   ipconfig getifaddr en0
   ```

3. **Safari auf dem iPhone** öffnen:
   ```
   http://<DEINE-IP>:8888
   ```
   Beispiel: `http://192.168.1.221:8888`

4. **Zum Home-Bildschirm hinzufügen:**
   - Teilen-Button antippen (Quadrat mit Pfeil nach oben)
   - "Zum Home-Bildschirm" wählen
   - "Hinzufügen"

5. Server kann danach gestoppt werden — die PWA funktioniert offline.

---

## Option 2: Ohne gleiches WLAN

### A) iCloud Drive (kein Server nötig)

1. Den Ordner `IronQuest` in iCloud Drive verschieben/kopieren:
   ```bash
   cp -r ~/Desktop/IronQuest ~/Library/Mobile\ Documents/com~apple~CloudDocs/IronQuest
   ```
2. Auf dem iPhone: **Dateien-App** öffnen → iCloud Drive → IronQuest → `index.html` antippen
3. Nachteil: Öffnet sich im Dateien-Browser, nicht als Fullscreen-App. Daten werden lokal im Browser gespeichert.

### B) GitHub Pages (kostenlos, von überall erreichbar)

1. GitHub-Repository erstellen (öffentlich oder privat)
2. Alle Dateien aus `IronQuest/` hochladen
3. Settings → Pages → Source: main branch → Save
4. Erreichbar unter: `https://<username>.github.io/<repo-name>/`
5. Auf dem iPhone als Home-Screen-App hinzufügen (wie oben)
6. Funktioniert von überall, auch ohne WLAN-Verbindung zum Mac

### C) Hotspot / USB

- **iPhone-Hotspot**: Mac verbindet sich mit dem iPhone-Hotspot → selbes Netzwerk → Option 1 funktioniert
- **USB**: Mac per USB mit iPhone verbinden, dann funktioniert Option 1 auch ohne WLAN (Mac-IP über `ifconfig` finden, Interface `bridge` oder `en*`)

---

## Daten-Synchronisation

Die Daten auf Mac und iPhone sind **getrennt** (jeweils lokal im Browser gespeichert).

Um Daten zu übertragen:
1. **Data**-Tab öffnen → "Export Data (JSON)" → JSON-Datei herunterladen
2. Datei per AirDrop, iCloud oder Messenger ans andere Gerät senden
3. Dort **Data**-Tab → "Import Data (JSON)" → Datei auswählen

---

## Troubleshooting

- **Seite lädt nicht auf dem iPhone?** → Prüfe ob Mac und iPhone im selben WLAN sind, und ob der Server läuft
- **IP hat sich geändert?** → `ipconfig getifaddr en0` im Terminal
- **Port blockiert?** → Anderen Port probieren: `python3 -m http.server 9999`
- **PWA aktualisieren?** → Safari → Website öffnen → Seite neu laden. Der Service Worker aktualisiert den Cache
