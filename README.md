# ScrapTrap Session-Recorder-Blocker 1.0 (Windows Utility)
 
## Sozialinformatisches Forschungswerkzeug & Clientseitiges Schutzsystem gegen unbemerktes Session-Recording
 
## 📋 Überblick
 
Der ScrapTrap Session-Recorder-Blocker ist eine autarke, install-freie Windows-Anwendung zur systemweiten Unterbindung von Session-Recording-Diensten (z. B. Microsoft Clarity, Hotjar, Mouseflow, FullStory, Smartlook u. a.).
 
Das Tool wurde im Rahmen sozialinformatischer Untersuchungen zum IT-Sicherheits- und Datenschutzverhalten entwickelt. Es adressiert eine zentrale Schutzlücke moderner Webarchitekturen:
 
> Die unbewusste und ungefragte Aufzeichnung von Nutzerinteraktionen (Mausbewegungen, Klicks, Scroll-Verhalten, Formulareingaben) noch vor der Erteilung eines wirksamen Consents.
 
## 🔬 Problemstellung & Wissenschaftlicher Hintergrund
 
In empirischen Prüfungen zeigte sich, dass Session-Recording-Skripte auf einer Vielzahl von kommerziellen wie öffentlichen Webseiten geladen werden, bevor der Nutzer eine Interaktion mit einem Consent-Banner (Cookie-Banner) durchführen konnte.
 
Besonders in sensiblen Handlungsfeldern der Sozialen Arbeit, Wohlfahrtspflege, Beratungseinrichtungen (NGOs) sowie bei Angeboten für geschützte Personengruppen (z. B. Opferberatung, Suchthilfe, Schwangerschaftskonfliktberatung) entsteht hierdurch ein erhebliches Schutzdefizit:
 
1. **Vorzeitige Datenübertragung:** Telemetrie- und Browser-Verbindungsdaten (inkl. IP-Adressen und Metadaten) fließen bereits beim Initialaufruf der Webseite an Drittanbieter-Server (oft im Nicht-EU-Ausland).
 
2. **Ungewollte Inhalts-Protokollierung:** Trotz Anonymisierungs-Versuchen durch Drittanbieter besteht bei Fehlkonfigurationen das Risiko, dass sensible Eingaben in Formularfeldern oder spezifische Navigationsmuster aufgezeichnet werden.
 
3. **Vertrauensverlust:** Nutzer verlassen sich auf die Schutzversprechen eines Consent-Banners, während im Hintergrund bereits aktives Session-Tracking stattfindet.
 
## 🛠️ Funktionsweise & Systemarchitektur
 
Im Gegensatz zu Browser-Erweiterungen (Extensions), die nur innerhalb eines spezifischen Browsers wirken und durch Skripte umgangen werden können, greift der ScrapTrap Session-Recorder-Blocker direkt auf Betriebssystemebene (Windows OS).
 
```text
[ Webbrowser / Electron App ]
│
▼ (DNS-Auflösung für tracking-domain.com)
 
[ Windows hosts-Datei ] ◄─── (ScrapTrap Umleitung auf 0.0.0.0)
│
▼
 
[ Paket verworfen / Blockiert ]
```
 
- **Systemweite Wirkung:** Blockiert Aufrufe von Recording-Endpunkten für sämtliche installierten Browser (Edge, Chrome, Firefox, Opera, Brave etc.) sowie Electron- und Desktop-Anwendungen.
 
- **0.0.0.0-Redirection:** Ergänzt die lokale Windows-hosts-Datei (`C:\Windows\System32\drivers\etc\hosts`) um dedizierte Verweise der bekannten Tracking-Server auf `0.0.0.0`. Dadurch schlagen Anfragen augenblicklich fehl, ohne Netzwerk-Timeouts zu erzeugen.
 
- **Keine Installation erforderlich:** Portables Executable (.exe), das ohne Hintergrunddienste oder Persistent-Daemons auskommt.
 
- **Transparente Wiederherstellbarkeit:** Über die Benutzeroberfläche lassen sich die gesetzten Blockaden mit einem Klick vollständig und rückstandsfrei entfernen.
 
## 🎯 Unterstützte Dienste (Auszug)
 
Das Modul blockiert u. a. Verbindungen zu folgenden Diensten und Domains:
 
- Microsoft Clarity
- Hotjar
- Mouseflow
- FullStory
- Lucky Orange
- Smartlook
- Contentsquare (ehem. Clicktale)
- Crazy Egg
- LogRocket
- Inspectlet
 
## 🚀 Installation & Nutzung
 
### 1. Download
 
Laden Sie die gepackte Anwendung `scraptrap_sessionrecorderblocker.zip` aus dem Repository oder von scraptrap.de herunter.
 
### 2. Entpacken
 
Entpacken Sie die ZIP-Datei in ein beliebiges Verzeichnis.
 
### 3. Ausführung als Administrator
 
Klicken Sie mit der rechten Maustaste auf die Datei `scraptrap_sessionrecorderblocker.exe` und wählen Sie **„Als Administrator ausführen“**.
 
> Hinweis: Administratorrechte sind zwingend erforderlich, um Schreibzugriff auf die Windows-hosts-Datei zu erlangen.
 
### 4. Schutz aktivieren
 
Klicken Sie auf den Button **Record-Tools SPERREN**.
 
Die Serveradressen werden in die hosts-Datei eingetragen.
 
### 5. Schutz aufheben
 
Über den Button **Sperre AUFHEBEN** wird der ursprüngliche Zustand der hosts-Datei wiederhergestellt.
 
## 🔒 Datenschutz & Transparenz
 
- **Zero-Data-Collection:** Das Tool erhebt, speichert oder überträgt keinerlei personenbezogene Daten, Telemetrie oder Nutzungsstatistiken.
 
- **Keine Injektion:** Es werden keine Zertifikate installiert oder Man-in-the-Middle-Techniken angewendet.
 
- **Quelloffen & Prüfbar:** Sämtliche Dateioperationen beschränken sich exklusiv auf das Auslesen und Schreiben der lokalen hosts-Datei.
 
## 📚 Verankerung im ScrapTrap-Ökosystem
 
Dieses Windows Utility ergänzt die serverseitigen Komponenten des ScrapTrap Frameworks (WAF, Bot-Mitigation, HTTP 402 Payment Enforcement) um ein clientseitiges Schutzwerkzeug für Endanwender, Bildungseinrichtungen und Gemeinnützige Träger.
 
- **Autor:** Dr. Uwe Janatzek, M.A.
- **Fachgebiet:** Sozialinformatik / IT-Sicherheit
- **Canonical URL:** https://www.scraptrap.de/scraptrap_session_recorder_blocker_win_tool.php
- **Wikidata Item:** Q141601085
- **ORCID:** 0009-0000-4404-7626
 
## 📄 Lizenz
 
Dieses Projekt ist unter der MIT License veröffentlicht – freie Nutzung für Forschung, Lehre, öffentliche Einrichtungen und private Anwender.
