# Windows vServer mieten: Was 4 vCPU und 8 GB RAM wirklich kosten, ob die Lizenz im Preis steckt und wann Managed lohnt (mit Preistabelle)

Ein Windows vServer beginnt in Deutschland bei 9,90 € im Monat für 1 Kern und 2 GB RAM. Die Klasse, die die meisten tatsächlich buchen, liegt bei 4 Kernen und 8 GB RAM und kostet je nach Anbieter zwischen 30 und 50 € monatlich. Woher diese Spanne kommt, sieht man erst, wenn man drei Zeilen prüft, die in den Tariftabellen gern fehlen: Umsatzsteuer, Windows-Lizenz und Backup.

Dieser Text rechnet die Preise der größeren deutschen und österreichischen Anbieter auf dieselbe Konfiguration herunter, zeigt an zwei Beispielen, wie Sie jeden Monatsbetrag selbst nachrechnen, und ordnet ein, wann ein gemanagter Tarif sinnvoll ist und wann nicht.

> **Kurzentschlossen:** Für eine Website, ein paar Remote-Desktop-Sitzungen oder eine kleine SQL-Datenbank reichen 4 vCPU und 8 GB RAM. Bei ava.hosting beginnt der Managed Windows VPS laut Produktseite bei 5,00 €/Monat (1 vCPU, 2 GB RAM, 25 GB NVMe), die größte dort ausgewiesene Stufe liegt bei 40,00 €/Monat (8 vCPU, 16 GB RAM, 160 GB NVMe). Dedizierte IPv4 und NVMe sind in allen Stufen dabei. 👉 [Windows-vServer-Tarife und aktuelle Preise ansehen](https://my.ava.hosting/aff.php?aff=15562)

## Windows vServer bei ava.hosting: Tarife und Ausstattung

ava.hosting (AvaHost) sitzt in Chișinău, Moldau, und betreibt die Hardware selbst. Die Windows-vServer laufen auf KVM, das die vCPU-Kerne hart zuweist, statt sie zwischen Mietern zu teilen. Für SQL Server und .NET-Anwendungen ist das relevanter, als es klingt: Wenn ein Nachbar seine CPU-Reserven ausreizt, entstehen auf Container-Plattformen Steal-Zeiten, die sich als schwankende Antwortzeiten im ASP.NET-Request-Pipeline oder als unerwartete Lock-Wartezeiten bemerkbar machen. Bei fester Kernzuweisung fällt dieser Effekt weg.

Nach dem Deployment steht RDP sofort bereit, ohne zusätzliche Konfiguration. Ein Control Panel ist nicht vorinstalliert, Sie arbeiten mit dem Windows Server Manager; Plesk lässt sich als kostenpflichtige Option dazubuchen.

| Tarif | vCPU / RAM / NVMe | Preis pro Monat | Windows Server | Buchung |
| --- | --- | --- | --- | --- |
| Managed Windows VPS, Einstiegsstufe | 1 vCPU / 2 GB / 25 GB | 5,00 € | vorinstalliert, RDP sofort nutzbar | [Einstiegsstufe prüfen](https://my.ava.hosting/aff.php?aff=15562) |
| Managed Windows VPS, größte ausgewiesene Stufe | 8 vCPU / 16 GB / 160 GB | 40,00 € | vorinstalliert, RDP sofort nutzbar | [Topstufe prüfen](https://my.ava.hosting/aff.php?aff=15562) |

Zwischen 5,00 € und 40,00 € liegen weitere Stufen; deren genaue Aufteilung und der tagesaktuelle Preis stehen im Bestellformular. Eine separate Lizenzzeile weist die Produktseite nicht aus, Windows Server ist Teil des jeweiligen Produkts. Neben der gemanagten Linie gibt es einen nicht gemanagten Windows VPS mit vollem RDP-Zugriff, bei dem Updates, Monitoring und Absicherung bei Ihnen liegen.

## Was hinter dem Preisschild steckt: vier Variablen

### 1. Netto oder brutto

STRATO nennt für den VPS M mit 2 vCores, 4 GB RAM und 120 GB NVMe 20 € pro Monat einschließlich Mehrwertsteuer, zuzüglich 9 € einmaliger Einrichtung. centron in Hallstadt bei Bamberg weist alle Preise netto aus, die Umsatzsteuer kommt obendrauf. Aus 50,24 € netto werden bei 19 % Umsatzsteuer 59,79 €. Wer zwei Angebote vergleicht, ohne auf die Steuerzeile zu schauen, vergleicht zwei verschiedene Dinge.

### 2. Lizenz separat oder im Preis

Das ist der größere Posten. centron berechnet Windows Server mit 9,24 € pro 2 Kerne, ein Server mit 8 vCPU braucht also vier Lizenzen und damit 36,96 € im Monat. PLUSTECH verlangt 7,20 € pro 2-Core-Lizenz. Bei STRATO und IPAX ist das Betriebssystem dagegen im Tarifpreis enthalten, bei IPAX steht ausdrücklich „Windows Server OS inkl.“.

Rechnen Sie das an einer 4-Kern-Maschine mit 8 GB RAM und 200 GB SSD durch:

- **PLUSTECH:** 4 × 2,74 € + 8 × 0,99 € + 200 × 0,06 € = **30,88 € netto**, ohne Lizenz. Mit zwei 2-Core-Lizenzen zu je 7,20 € sind es 45,28 € netto, mit den Managed Services für Backup, Monitoring und Patches weitere 49 € und damit 94,28 € netto.
- **centron, selbst verwaltet:** 6,56 € CPU + 15,20 € RAM + 10,00 € SSD + 18,48 € Lizenz = **50,24 € netto**. Mit Premium Full Managing kommen 50 € Betriebspauschale hinzu, macht 100,24 € netto.

Dieselbe Konfiguration kostet bei STRATO als VPS L mit 240 GB NVMe **40 € brutto inklusive Lizenz**, einmalig 9 € Einrichtung. Wer nur auf die Zahl im Werbebanner schaut, hält PLUSTECH für den günstigsten Anbieter; nach Lizenz und Betrieb ist STRATO in dieser Klasse billiger.

### 3. Backup ist selten inklusive

STRATO schreibt es offen in die Tarifdetails: „Backups: nicht inbegriffen“. Bei IONOS ist Backup eine Option über Acronis ab 6 Cent pro GB und Monat, für 100 GB Daten also 6 € monatlich oder 72 € im Jahr. centron berechnet Backup-Speicher mit 0,03687 € pro GB und Monat, 100 GB kosten dort 3,69 € monatlich, rund 44 € im Jahr, dafür mit täglicher inkrementeller, wöchentlicher differenzieller und monatlicher Vollsicherung bei 28 Tagen Aufbewahrung in einem zweiten Brandabschnitt. IPAX legt einen Basis-Snapshot gratis dazu. Über drei Jahre summiert sich die Differenz zwischen „nicht enthalten“ und „3,69 € im Monat“ auf mehr als 130 €.

### 4. Aktionspreis und Vertragslaufzeit

STRATO bewirbt die Windows-vServer mit 13, 25, 48 und 70 € für die ersten ein oder drei Monate, danach gelten wieder 20, 40, 79 und 116 €. Bei der Ein-Monats-Variante nennt STRATO 15 € Ersparnis im ersten Jahr; ein Monat zum Aktionspreis spart gegenüber 20 € aber nur 7 €. Rechnen Sie mit dem Listenpreis, nicht mit dem Aktionspreis.

IPAX staffelt denselben Tarif nach Laufzeit. Der V20 Win mit 2 Kernen und 4 GB kostet bei 24 Monaten 16,90 €, bei 12 Monaten 19,90 €, bei 6 Monaten 20,90 € und bei monatlicher Zahlung 21,90 €, Einrichtung 0 €. centron gewährt auf zugesagte Ressourcen 10, 20 oder 30 % Rabatt bei 12, 24 oder 36 Monaten; das durchgerechnete Anwendungsbeispiel sinkt dadurch von 175,88 € auf 166,99 €, 158,10 € oder 149,20 € netto.

## Mit Ressourcenpreisen selbst nachrechnen

Zwei Anbieter legen ihre Einzelpreise offen. Damit können Sie jede Konfiguration prüfen und erkennen, ob ein Angebot ehrlich gerechnet ist:

| Position | centron (netto) | PLUSTECH (netto) |
| --- | --- | --- |
| vCPU | 1,64 € pro Kern/Monat | 2,74 € pro Kern/Monat |
| RAM | 1,90 € pro GB/Monat | 0,99 € pro GB/Monat |
| SSD/NVMe | 0,05 € pro GB/Monat | 0,06 € pro GB/Monat |
| Windows Server | 9,24 € pro 2 Kerne | 7,20 € pro 2 Kerne |
| Betrieb/Management | 50,00 € pro Server | 49,00 € inkl. Backup und Monitoring |
| Backup-Speicher | 0,03687 € pro GB/Monat | in den Managed Services enthalten |

Beide Beispielrechnungen der Anbieter gehen mit diesen Sätzen exakt auf. centrons 8-Kern-Server mit 32 GB und 300 GB SSD kostet 88,92 € an Rechenleistung und Speicher, plus 50 € Betrieb, plus 4 × 9,24 € Lizenz, zusammen 175,88 € netto. Ohne Betriebspauschale, aber mit Lizenz, landet dieselbe Maschine bei 125,88 € netto. Bei PLUSTECH ergeben 8 × 2,74 € + 32 × 0,99 € + 500 × 0,06 € genau die beworbenen 83,60 €, allerdings ohne Windows-Lizenz und ohne Managed Services.

Der Unterschied zwischen 125,88 € und 83,60 € kommt also nicht von der Hardware, sondern von 16,64 € Lizenz und 49 € Betrieb. Wer diese beiden Zeilen in jedem Angebot sucht, kann Angebote nicht mehr durcheinanderbringen. 👉 [Managed-Windows-Tarife mit Lizenz und Verwaltung vergleichen](https://my.ava.hosting/aff.php?aff=15562)

## Welche Stufe reicht?

**1 bis 2 Websites, Testumgebung, einzelner RDP-Zugang:** 2 vCPU und 4 GB RAM genügen. STRATO VPS M kostet 20 € brutto monatlich plus 9 € Einrichtung, IPAX V20 ab 16,90 € bei 24 Monaten Laufzeit.

**ERP, SQL Server, mehrere Sites, zehn und mehr gleichzeitige Sitzungen:** 8 vCPU und 32 GB RAM sind die Untergrenze. centron veranschlagt dafür 175,88 € netto mit Full Managing oder 125,88 € netto in Eigenregie, jeweils inklusive Lizenz. Die ava.hosting-Stufe mit 8 vCPU und 16 GB für 40 € monatlich deckt kleinere Datenbanken und Anwendungen ab, bei denen der Speicherbedarf nicht mit der Kernzahl steigt.

**Remote Desktop für mehrere Personen:** Jeder gleichzeitig arbeitende Nutzer braucht eine eigene Lizenz. PLUSTECH berechnet eine RDS-CAL mit 9,48 €, centron weist darauf hin, dass bei mehreren Personen am Server für jede eine Lizenz fällig wird. Bei fünf gleichzeitigen Nutzern kommen so schnell 45 bis 50 € pro Monat zur Servermiete hinzu. Wer nur gelegentlich administriert, braucht keine CAL.

## Windows Server 2022 oder 2025?

STRATO liefert Windows Server 2025 oder 2022 als Datacenter-Edition, IONOS stellt 2022 oder 2025 zur Wahl, IPAX nennt ebenfalls beide Versionen. Bei ava.hosting ist Windows Server Bestandteil des Produkts; welche Version im Einzelfall ausgeliefert wird, steht im Bestellvorgang.

Der Zeitpunkt für einen Wechsel ist günstig. Der erweiterte Support für Windows Server 2016 endet am 12. Januar 2027. Wer heute noch einen 2016er-Server betreibt, hat gut ein Jahr für die Migration und sollte die neue Maschine parallel aufsetzen, statt sie in letzter Minute hochzuziehen.

## Rechenzentrum, Rechtsraum und SLA

STRATO betreibt zwei europäische Rechenzentren mit ISO-27001-Zertifizierung durch den TÜV, die jährlich geprüft wird, und bezieht seit 2008 Strom aus erneuerbaren Quellen. IONOS bietet Standorte in der EU, den USA und Großbritannien, ist ebenfalls ISO-27001-zertifiziert und schließt auf Wunsch einen Vertrag zur Auftragsdatenverarbeitung nach BDSG. centron betreibt sein eigenes Rechenzentrum in Hallstadt, ist BSI C5 Type 1 attestiert und nach ISO 27001 auf Basis von IT-Grundschutz zertifiziert, mit einer SLA von 99,5 % im Worker Pool und 99,8 % im HA Pool. IPAX hostet in Wien in einem ISO/IEC-27001-zertifizierten Rechenzentrum. IONOS gibt 99,99 % Verfügbarkeit an.

ava.hosting betreibt seine Hardware in Chișinău in einem gehärteten Rechenzentrum in einem ehemaligen militärischen Schutzbau, mit Generatorabsicherung und DDoS-Mitigation. Das ist ein anderer Rechtsraum als Deutschland oder Österreich. Wer personenbezogene Daten verarbeitet, muss die Übermittlung in ein Drittland datenschutzrechtlich begründen und die Auftragsverarbeitung klären. Für Projekte mit ausschließlich deutschen Endkundendaten ist ein Anbieter mit Serverstandort in der EU der einfachere Weg.

## Was Nutzer berichten

Die Bewertungen zu ava.hosting fallen gemischt aus. Auf Trustpilot finden sich seit 2025 mehrere Berichte über VPS-Sperrungen nach Spam-Meldungen, teils ohne Wiederherstellungsangebot, sowie über schwankende Netzwerkqualität und lange Antwortzeiten im Support. Andere Nutzer heben Preis, Ausstattung und Oberfläche hervor, ein Vergleichstest bescheinigt dem Anbieter eine Antwortzeit von 573 ms, die knapp unter dem Branchendurchschnitt von 600 ms liegt. Wer eine Verfügbarkeitsgarantie mit Vertragsstrafe und deutschsprachigen Support braucht, ist bei einem deutschen Anbieter mit eigener SLA besser aufgehoben.

## Häufige Fragen

**Kann ich monatlich kündigen?**
Bei centron gibt es keine Mindestlaufzeit, selbst verwaltete Cloud Server werden stundenweise abgerechnet. IPAX bietet einen Ein-Monats-Preis und eine kostenlose Teststellung, STRATO verlangt eine einmalige Einrichtung von 9 €. Bei ava.hosting regelt das Bestellformular die Abrechnungsperiode; prüfen Sie die Angabe dort, bevor Sie abschließen.

**Wie viel Bandbreite ist enthalten?**
STRATO und IONOS nennen bis zu 1 Gbit/s bei unbegrenztem Traffic. IPAX kalkuliert anders: 100 Mbit/s sind im Tarif enthalten, 250 und 1000 Mbit/s müssen dazugebucht werden. Ein Anbieter mit „1 Gbit/s“ im Datenblatt ist deshalb nicht automatisch schneller als einer mit 100 Mbit/s im Basistarif, wenn Sie den Uplink ohnehin nicht auslasten.

**Was kostet eine zusätzliche IPv4-Adresse?**
IONOS berechnet 5 € pro Monat und Adresse, eine ist enthalten, dazu ein IPv6/80-Netz. Bei ava.hosting gehört eine dedizierte IPv4 zur Grundausstattung jedes Tarifs.

**Brauche ich Plesk?**
Nur wenn Sie Websites über eine Oberfläche verwalten wollen. IONOS berechnet die Plesk Web Host Edition mit 5 € monatlich und setzt unter Windows mindestens 32 GB Speicherplatz voraus. Bei ava.hosting ist Plesk eine kostenpflichtige Option, IIS, FTP, DNS und Datenbanken bringt es mit.

## Die Auswahl in drei Sätzen

Sie brauchen eine preiswerte Windows-Maschine für Website, Datenbank oder RDP und kommen mit Serverstandort Moldau sowie eigener Absicherung zurecht, dann ist der Managed-Tarif ab 5,00 € mit 1 vCPU und 2 GB der günstigste Einstieg, die 8-vCPU-Stufe für 40,00 € deckt den nächsten Bedarf. Wenn deutsche oder österreichische Serverstandorte, dokumentierte SLAs und enthaltene Windows-Lizenzen im Vordergrund stehen, rechnen Sie gegen die oben genannten Beträge von STRATO, IPAX und centron. Prüfen Sie vor jeder Bestellung zwei Dinge: wie viele 2-Core-Lizenzen Ihre Konfiguration braucht, und ob ein Backup im Preis steckt oder monatlich extra kostet.

Verbindlich ist immer der Preis, der im Bestellformular steht; Produktseiten und Aktionszeiträume ändern sich. 👉 [Aktuelle Windows-vServer-Tarife bei ava.hosting prüfen](https://my.ava.hosting/aff.php?aff=15562)
