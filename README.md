# Zero Connect

Zero Connect ist eine Anwendung für den Raspberry Pi. Sie liest die Daten deines **Zero-Elektromotorrads** aus der Zero Cloud und zeigt sie in einer eigenen App: Ladestand und Ladeverlauf, 12-V-Batterie, Fahrten, Reichweite, Ladeorte und Wartung. Sie liest nur und steuert nichts am Motorrad.

> **Beta.** Privates Hobbyprojekt, unabhängig von Zero Motorcycles, ohne Garantie. Nutzung auf eigenes Risiko ([NOTICE](NOTICE.md)).

*[English summary](#english)*

## Das brauchst du

- Raspberry Pi 3 B+ mit microSD-Karte (ab 16 GB) und Netzteil
- Computer mit Kartenleser
- Dein Zero-Cloud-Konto (wie in der Zero-App)
- WLAN und ein Telefon

## Installation

1. Unter [**Releases**](https://github.com/Taii-lo/zero-connect-releases/releases) die Datei `zero-connect-….img.xz` laden (etwa 200 MB, nicht entpacken).
2. Mit dem [Raspberry Pi Imager](https://www.raspberrypi.com/software/) auf die Karte schreiben: *Betriebssystem → Eigenes Image verwenden*. Einstellungen anpassen: **Nein**.
3. Karte in den Pi, Strom anschließen, etwa zwei Minuten warten.
4. Telefon mit dem WLAN **„Zero Connect Setup“** verbinden und der Einrichtung folgen: Heim-WLAN, Motorradmodell, Zero-Login.
5. App öffnen unter `http://zero-connect.local:8080` (alternativ die IP-Adresse des Pi aus dem Router).

## Updates

Die App sucht täglich nach neuen Versionen und installiert sie auf Wunsch. Deine Daten bleiben erhalten. Unter *Einstellungen → App & Updates* schaltest du **Beta-Versionen** ein oder aus.

## Datenschutz

Deine Daten liegen auf deinem Gerät. Es gibt kein Konto beim Entwickler. Für seine Funktionen spricht das Gerät mit diesen Diensten:

| Dienst | Wofür | Was dorthin geht |
|---|---|---|
| Zero Cloud (`mongol.brono.com`) | Fahrzeugdaten (erforderlich) | dein Zero-Login |
| `photon.komoot.io` | Ortsnamen für Ladeorte | die genauen Koordinaten des Ladeortes |
| `tile.openstreetmap.org` | Kartenkacheln | der Kartenausschnitt, aus deinem Browser |
| `images.prismic.io` | Bild deines Modells | die Modellauswahl |
| GitHub Pages | Update-Prüfung | die Anfrage selbst (IP-Adresse) |
| Tailscale, Aivi, ABRP, Web-Push | nur wenn du sie einschaltest | siehe jeweiliger Dienst |

## Getestet mit

| | getestet | nicht getestet |
|---|---|---|
| Motorrad | Zero SR/S | alle anderen Modelle |
| Telefon | iPhone | Android |
| Raspberry Pi | 3 B+ | Pi 5, Pi 4 und andere |

## Hilfe

In der App: *Einstellungen → Hilfe & Diagnose → Häufige Fragen*. Sonst: *Systemaktionen → Supportpaket erstellen* und an den Entwickler schicken (ohne Zugangsdaten und Standort).

Zero und die Modellnamen sind Marken ihrer Inhaber. Dieses Repository enthält nur das Image und die Update-Dateien, keinen Quelltext.

---

## English

Zero Connect runs on a Raspberry Pi and shows your **Zero electric motorcycle's** data from the Zero Cloud in its own app: battery and charging history, 12 V battery, rides, range, places, maintenance. Read-only, unofficial, no warranty.

**Install:** download `zero-connect-….img.xz` from [Releases](https://github.com/Taii-lo/zero-connect-releases/releases), write it with Raspberry Pi Imager ("Use custom"), power the Pi, join the Wi-Fi *Zero Connect Setup* and follow the setup. **Updates** keep your data; *Settings → App & Updates* has the beta switch. **Privacy:** data stays on the device; the services it contacts are listed above. **Tested:** Zero SR/S, iPhone, Raspberry Pi 3 B+.
