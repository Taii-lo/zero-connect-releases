# Zero Connect

Zero Connect ist ein kleines Gerät (Raspberry Pi), das die Daten deines **Zero-Elektromotorrads** aus der Zero Cloud liest und dir eine eigene App dafür gibt: Batteriestand und Ladeverlauf, 12-V-Batterie, Fahrten, Reichweite, Ladeorte, Wartung und auf Wunsch Mitteilungen. Es liest nur und steuert nichts am Motorrad.

*English summary below.*

> **Ein privates Hobbyprojekt, kein Produkt.** Zero Connect ist unabhängig und nicht von Zero Motorcycles. Es gibt keine Garantie. Du nutzt es auf eigenes Risiko. Siehe [NOTICE.md](NOTICE.md) und unten „Hinweise“.

## Was du brauchst

- Einen **Raspberry Pi 3 B+ oder Pi 5** mit microSD-Karte (ab 16 GB) oder SSD, Netzteil und WLAN oder Netzwerkkabel. Andere Modelle (z. B. Pi 4) sind nicht getestet.
- Dein **eigenes Zero-Cloud-Konto** (dieselbe E-Mail und dasselbe Passwort wie in der Zero-App). Jedes Gerät nutzt das Konto seines Besitzers.
- Ein Telefon oder Computer im selben WLAN.
- Optional: ein kostenloses [Tailscale](https://tailscale.com)-Konto, wenn du die App auch unterwegs öffnen willst.

## Installieren (etwa 15 Minuten)

1. Lade unter [**Releases**](https://github.com/Taii-lo/zero-connect-releases/releases/latest) die Datei `zero-connect-….img.xz` herunter.
2. Installiere den [Raspberry Pi Imager](https://www.raspberrypi.com/software/), wähle unter „Betriebssystem“ ganz unten **„Eigenes Image verwenden“** und die heruntergeladene Datei, dann die Speicherkarte. Fragt der Imager, ob du Einstellungen anpassen möchtest: **Nein**, das Image bringt alles mit.
3. Karte in den Pi, Netzteil anschließen. Ohne Netzwerkkabel baut der Pi ein WLAN **„Zero Connect Setup“** auf: Mit dem Telefon verbinden, die Einrichtung öffnet sich.
4. Heim-WLAN wählen, Motorradmodell wählen, Zero-Cloud-Konto eintragen. Fertig. Die App ist danach unter der Adresse erreichbar, die dir die Einrichtung am Ende zeigt (z. B. `http://zero-connect.local:8080`).

Eine ausführliche Anleitung mit Fernzugriff (Tailscale) und Mitteilungen steht in der App unter **Einstellungen → Hilfe & Diagnose → Häufige Fragen**.

## Updates und Beta

Die App prüft einmal am Tag auf neue Versionen und installiert sie auf Wunsch (auch nachts). Vor jedem Update sichert sie den alten Stand und kehrt bei einem Fehler selbst zurück; **deine Daten bleiben erhalten**. Alle Update-Dateien in diesem Repository sind digital signiert, das Gerät nimmt nichts an, was nicht zur Signatur passt.

Neue Versionen erscheinen zuerst als **Beta**. Unter *Einstellungen → App & Updates* schaltest du **„Beta-Versionen erhalten“** ein oder aus, ganz ohne Code. Wenn du die Beta ausschaltest und noch eine Beta-Version nutzt, die neuer ist als die stabile, bietet die App an, zur stabilen Version zurückzuwechseln, aber nur, wenn deine Daten dort sicher lesbar sind.

## Datenschutz: was bleibt wo?

Deine Daten (Ladeverlauf, Fahrten, Orte, Zugangsdaten) liegen **auf deinem Gerät** und werden nicht an den Entwickler geschickt. Es gibt kein Konto bei uns. Ehrlich gesagt: Das Gerät spricht für seine Funktionen mit diesen Diensten Dritter.

| Dienst | Wofür | Was dorthin geht |
|---|---|---|
| Zero Cloud (`mongol.brono.com`) | Fahrzeugdaten abrufen (erforderlich) | dein Zero-Login, wie die Zero-App es auch tut |
| `photon.komoot.io` | Ortsnamen für Ladeorte | **die genauen Koordinaten** des Ladeortes |
| `tile.openstreetmap.org` | Kartenkacheln | der angezeigte Kartenausschnitt, aus deinem Browser |
| Bildserver von Zero (`images.prismic.io`) | Bild deines Modells | die Modellauswahl |
| GitHub Pages (dieses Repository) | Update-Prüfung | die Anfrage selbst (IP-Adresse) |
| Tailscale, Aivi, ABRP, Web-Push | nur, wenn du sie einschaltest | siehe jeweilige Dienste |

Ein Update, das den Ortsnamen-Dienst abschaltbar macht und die Datenflüsse beweisbar zeigt, ist geplant.

## Unterstützt und getestet

- **Motorräder:** Entwickelt und getestet mit einer **Zero SR/S**. Die Einrichtung kennt auch SR/F, SR, S, DS, DSR und DSR/X; diese sollten dieselbe Zero Cloud nutzen, sind aber **nicht getestet**.
- **Telefone:** Getestet mit **iPhone** (inklusive Mitteilungen und Live-Aktivität über Aivi). **Android ist nicht getestet**, die App läuft in jedem Browser, Mitteilungen auf Android sind unbekannt.
- **Geräte:** Raspberry Pi 3 B+ und Pi 5.

## Wenn etwas nicht klappt

In der App: *Einstellungen → Hilfe & Diagnose → Häufige Fragen*. Hilft das nicht: *Systemaktionen → Supportpaket erstellen*, herunterladen und an den Entwickler schicken. Das Paket ist standardmäßig von Zugangsdaten und Standort bereinigt.

## Hinweise

- Zero Connect ist ein unabhängiges, nicht offizielles Projekt. „Zero“ und Modellnamen sind Marken ihrer Inhaber.
- Es gibt keine Garantie. Entscheidungen beim Laden und Fahren triffst du selbst.
- Dieses Repository enthält nur die **signierten Update-Dateien** und das Image für neue Geräte, keinen Quelltext und keine Fahrzeugfotos.

---

## English summary

Zero Connect is a small appliance (Raspberry Pi 3 B+ or 5) that reads your **Zero electric motorcycle's** data from the Zero Cloud and gives you your own app for it: battery level and charging history, 12 V battery, rides, range, places and maintenance. It only reads; it never controls the motorcycle. It is an unofficial hobby project with no warranty.

**Install:** download `zero-connect-….img.xz` from [Releases](https://github.com/Taii-lo/zero-connect-releases/releases/latest), write it with Raspberry Pi Imager ("Use custom"), power the Pi, join the Wi-Fi *Zero Connect Setup* and follow the setup (home Wi-Fi, bike model, your own Zero Cloud login).

**Updates** are signed, backed up and rolled back on failure; your data stays. Switch **"Receive beta versions"** on or off under *Settings → App & Updates*; no code needed. **Privacy:** your data stays on the device; the device talks to the Zero Cloud (required), `photon.komoot.io` (place names, sends exact charging-place coordinates), OpenStreetMap (map tiles), Zero's image server (model photo) and GitHub Pages (update check), plus Tailscale, Aivi, ABRP and web push only if you enable them. **Tested** with a Zero SR/S and iPhone; Android and other models are untested.
