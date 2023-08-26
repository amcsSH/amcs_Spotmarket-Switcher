# Victron-ESS, Shelly Plug S und AVM-Fritz-DECT200-210 Spotmarkt-Schalter

Herzlich willkommen im Victron-ESS & Shelly Plug S & AVM-Fritz-DECT200-210 Spotmarkt-Schalter Repository!
Diese Software wurde entwickelt, um die Funktionalit�t Ihrer Energieanlage zu erweitern, indem sie folgende Komponenten integriert:

- Victron Venus OS Energiespeicher-Systeme
- Shelly-Produkte (wie Shelly Plug S oder Shelly Plus1PM)
- AVM Fritz!DECT200 und 210 schaltbare Steckdosen

## Was diese Software bietet

Das Hauptziel dieser Software besteht darin, Ihr System in die Lage zu versetzen, auf die st�ndlichen Preisschwankungen am Spotmarkt f�r Strom zu reagieren.
Diese Preise werden am Nachmittags des Vortags festglegt unter Ber�cksichtigung der Erfahrungswerte f�r den Energiebedarf und den Wettervorhersagen f�r die Wind- und Sonnenkraftwerke.
So ist der Verbraucher zu motivieren, den eigenen Verbrauch dem Tageverlauf der Preisentwicklung anzupassen.
Dadurch kann beispielsweise das Aufladen von Batterien oder das Aktivieren der Stromversorgung ohne h�ndisches Zutun auf Zeiten mit niedrigen Preisen gelegt werden.

In Europa gibt es Preis�nderungen auf Energiem�rkten mit st�ndlichen Anpassungen, allerdings bereits am Vortag anhand von Vorhersagen festgelegt.  Beliebte Energieanbieter wie Tibber oder Awattar �bermitteln diese Echtzeit-Preisniveaus an Endnutzer, um wirtschaftlicheren und nachhaltigeren Energieverbrauch zu erm�glichen. Diese Software unterst�tzt entsprechende automatisierte Anpassungen der Verbraucher.

Durch die Integration dieser Software haben Sie die M�glichkeit, zur sauberen Energieversorgung beizutragen oder einfach nur Ihren Energieverbrauch zu optimieren und so Geld zu sparen:
- **Priorit�t f�r erneuerbare Energien:** Stellen Sie sicher, dass Ihr Energieverbrauch mit der Verf�gbarkeit erneuerbarer Energien in Einklang steht, um nicht-erneuerbare Quellen w�hrend Zeiten geringer Sonneneinstrahlung und Wind zu vermeiden.
- **Batterieoptimierung:** Wenn Sie ein Energiespeichersystem besitzen, erm�glicht Ihnen die Software, Ihre Batterie aufzuladen, wenn die Strompreise niedriger sind als die Einspeiseverg�tung, um kosteng�nstige Energie optimal zu nutzen.
- **Individuelle Regelungen:** Passen Sie die Software Ihren Bed�rfnisse an, basierend auf Faktoren wie Batteriekapazit�t, erwartetem Energieverbrauch und vorausgesagtem Sonnenschein. Dies er�ffnet die M�glichkeit, g�nstige Windenergiepreise in der Nacht oder zu bestimmten Zeitr�umen zu nutzen.
- **Unabh�ngige Nutzung von Energiespeichersystemen:** Diese Software f�rdert die Nutzung von Energiespeichersystemen (ESS) auch ohne Installation von Solaranlagen und bietet Mehrwert f�r alle Benutzer, insbesondere w�hrend der Wintermonate.

## Datenquelle und Erweiterbarkeit

Die Software verwendet derzeit st�ndliche EPEX Spot DE-LU Preise, wie sie von [aWATTar](https://www.awattar.com) oder [Tibber](https://www.tibber.com), zwei mittel-/nordeurop�ischen Energieanbietern, bereitgestellt werden.
Wir m�chten Sie aber dazu anhalten, uns Patches zukommen zu lassen, um �hnliche Dienste in anderen Regionen zu nutzen.

F�r diejenigen, die tiefer in die Integration von APIs einsteigen m�chten, finden Sie wichtige Informationen zur Nutzung der API auf unserer Referenzwebsite: [Awattar API-Dokumentation](https://www.awattar.de/services/api). Es ist erw�hnenswert, dass die API f�r Kunden des Anbieters kostenlos ist und dem Fair-Use-Prinzip folgt. Derzeit ist kein Zugriffstoken erforderlich. Alternativ kann die kostenlose Entso-E-API, die ganz Europa abdeckt, verwendet werden.

## Visualisierung der Strompreise

Um Einblicke in die Strompreise zu erhalten und fundierte Entscheidungen zu treffen, empfiehlt sich die [Transparency Entso-E Platform](https://transparency.entsoe.eu/transmission-domain/r2/dayAheadPrices/show). Diese Plattform erm�glicht es Ihnen, Tagespreise im Voraus zu visualisieren und zu analysieren, mit einer Aufl�sung von PT60M. Bleiben Sie informiert, um handlungsf�hig zu bleiben.

Wir hoffen, dass diese Software Intelligenz und Effizienz in Ihre Energieanlage bringt. Lassen Sie uns gemeinsam an einer intelligenteren und nachhaltigeren Energiezukunft arbeiten!

![grafik](https://user-images.githubusercontent.com/6513794/224442951-c0155a48-f32b-43f4-8014-d86d60c3b311.png)

## Installation

F�r ein zuverl�ssige Funktionieren dieser Anwendung sollen
 - src/controller.sh - Implementation der Logik und des Zugriffs auf Internet, Wechselrichter und schaltbare Steckdosen
 - src/run - wird beim Start ausgef�hrt, um controller.sh st�ndlich zu starten
auf den Controller der Steckdosen/Wechselrichter copiert werden und deren Lokalisation auf dem Dateisystem an richtigen Stellen bekanntgegeben werden.

Zur Erleichterung beiten wir ein Install-Skript an. Wenn dies erfolgreich durchl�uft, so sollten Sie davon ausgehen k�nnen, dass die Konfiguration Ihres Systems alle Voraussetzungen f�r einen Betrieb der Software hat oder sie werden auf vorzunehmende Ver�nderungen hingewiesen. Auch sollten alle Eintr�ge in der crontab f�r den periodischen Start des Controllers, der Registration des Services und dem Start beim Hochfahren des Systems konsistent vorgenommen worden sein.

### Zugriff auf Venus OS

F�r Anweisungen zum Zugriff auf das Venus OS beachten Sie bitte [https://www.victronenergy.com/live/ccgx:root_access](https://www.victronenergy.com/live/ccgx:root_access).


### Ausf�hrung des Installations-Skripts

Die Einrichtung des Victron-ESS & Shelly Plug S & AVM-Fritz-DECT200-210 Spotmarkt-Schalters ist ein unkomplizierter Vorgang. Wenn Sie bereits eine UNIX-basierte Maschine verwenden, wie macOS, Linux oder Windows mit dem Linux-Subsystem, befolgen Sie diese Schritte, um die Software zu installieren:

1. Laden Sie das Installations-Skript aus dem GitHub-Repository herunter, indem Sie [diesen Link verwenden](https://raw.githubusercontent.com/christian1980nrw/Spotmarket-Switcher/main/victron-venus-os-install.sh), oder f�hren Sie den folgenden Befehl in Ihrem Terminal aus:
   ```
   wget https://raw.githubusercontent.com/christian1980nrw/Victron-ESS__Shelly-Plug-S__AVM-Fritz-DECT200-210__Spotmarket-Switcher/main/victron-venus-os-install.sh
   ```

2. F�hren Sie das Installations-Skript aus und verwenden Sie zus�tzliche Optionen, um alles in einem Unterverzeichnis f�r Ihre �berpr�fung vorzubereiten. Zum Beispiel:
   ```
   DESTDIR=/tmp/foo sh victron-venus-os-install.sh
   ```
   Wenn Sie Victron Venus OS verwenden, sollte das korrekte DESTDIR `/` (das Stammverzeichnis) sein. Sie k�nnen die installierten Dateien in `/tmp/foo` erkunden.

Bitte beachten Sie, dass diese Software derzeit f�r das Venus OS optimiert ist, aber an andere Setups angepasst werden kann, beispielsweise um Haushaltsger�te �ber IP-Schalter zu steuern.
Zuk�nftige Entwicklungen sollen die Kompatibilit�t mit anderen Systemen verbessern.

- Wenn Sie Victron Venus OS verwenden:
  - F�hren Sie `victron-venus-os-install.sh` aus, um den Spotmarkt-Schalter herunterzuladen und zu installieren.
  - Bearbeiten Sie die Variablen, indem Sie `vi /data/etc/Spotmarket-Switcher/controller.sh` ausf�hren.
  - Setzen Sie nach der Anpassung mit Schritt 3 fort.

- Wenn Sie ein anderes Betriebssystem verwenden:
  1. Kopieren Sie das Shell-Skript (`controller.sh`) an einen benutzerdefinierten Ort und passen Sie die Variablen entsprechend Ihren Anforderungen an.
  2. Erstellen Sie eine Crontab oder eine andere Zeitplanungsmethode, um dieses Skript zu jeder vollen Stunde auszuf�hren.
  3. Richten Sie einen ESS-Ladeplan ein (siehe Screenshot). Im Beispiel wird die Batterie nachts bis zu 50 % aufgeladen, wenn die Aktivierung erfolgt ist.
     Denken Sie daran, sie nach der Erstellung zu deaktivieren. �berpr�fen Sie, ob die Systemzeit (wie im Screenshot gezeigt) korrekt ist.

![grafik](https://user-images.githubusercontent.com/6513794/206877184-b8bf0752-b5d5-4c1b-af15-800b6499cfc7.png)

### Beispiel-Crontab

Verwenden Sie den folgenden Crontab-Eintrag, um das Steuerskript st�ndlich auszuf�hren:

�ffnen Sie Ihr Terminal und geben Sie `crontab -e` ein, dann f�gen Sie die folgende Zeile ein:
```
0 * * * * /Pfad/zur/controller.sh
```

## Konfiguration

Alle Entscheidungen f�r ein Ein-/Ausschalten der Akkuladung und der Steckdoesen werden im controller-Skript getroffen. Das Skript wird jede Stunde neu gestartet - ohne ein Wissen dar�ber, was in der vorherigen Stunde geschah. Dadurch wird die Ausf�hrung des Skriptes "kontextfrei" und wie wir finden auch alles einfacher bei bereits gutem Erfolg. Die nachfolgend pr�sentierten Regeln haben den folgenden Grundgedanken:

 * Die wirklich gro�en Anlagen interessieren sich nicht f�r den Eigenverbrauch - da geht es um den richtigen Moment f�r eine Einspeisung, die dieses Skript noch nicht abbildet.
 * Eine kleine Anlage im Sommer entspricht den gro�en Anlagen im Winter.
 * Die g�nstigsten Strompreise sind nachts.
 * Es gibt eine Wohlf�hl Akkuladung, die f�r den Tag auch bei diesigem Wetter ausreicht.

Noch ohne implementierte Regel dazu, aber ... moment ... sind da dran:

 * Ziehe diejenige Energie von der Aufladung des Akkus ab, die die Sonne bis zum Moment des erwarteten Verbrauchs bereits liefert

### Regeln f�r Einschaltung der Ladung des Akkus

Die Regeln f�r ein Einschalten des Ladeger�ts sind als array im Skript festgelegt. Das Skript stellt die Werte jeweils in den Variablen zur Verf�gung. Sobald eine Bedingung zutrifft, wird eingeschaltet. Trifft keine zu, so wird abgeschaltet.

```
charging_conditions=(
  "use_start_stop_logic == 1 && start_price_integer > current_price_integer"
  "charge_at_solar_breakeven_logic == 1 && feedin_price_integer > current_price_integer + energy_fee_integer"
  "charge_at_lowest_price == 1 && lowest_price_integer == current_price_integer"
  "charge_at_second_lowest_price == 1 && second_lowest_price_integer == current_price_integer"
  "charge_at_third_lowest_price == 1 && third_lowest_price_integer == current_price_integer"
  "charge_at_fourth_lowest_price == 1 && fourth_lowest_price_integer == current_price_integer"
  "charge_at_fifth_lowest_price == 1 && fifth_lowest_price_integer == current_price_integer"
  "charge_at_sixth_lowest_price == 1 && sixth_lowest_price_integer == current_price_integer"
)
```

### Regeln f�r Einschaltung der Steckdosen

Die Regeln f�r Einschaltung der Steckdosen sind analog zur Ladung des Akkus.

```
switchablesockets_conditions=(
  "switchablesockets_at_start_stop == 1 && start_price_integer > current_price_integer"
  "switchablesockets_at_solar_breakeven_logic == 1  && feedin_price_integer > current_price_integer + energy_fee_integer"
  "switchablesockets_at_lowest_price == 1 && lowest_price_integer == current_price_integer"
  "switchablesockets_at_second_lowest_price == 1 && second_lowest_price_integer == current_price_integer"
  "switchablesockets_at_third_lowest_price == 1 && third_lowest_price_integer == current_price_integer"
  "switchablesockets_at_fourth_lowest_price == 1  && fourth_lowest_price_integer == current_price_integer"
  "switchablesockets_at_fifth_lowest_price == 1 && fifth_lowest_price_integer == current_price_integer"
  "switchablesockets_at_sixth_lowest_price == 1 && sixth_lowest_price_integer == current_price_integer  "
)
```

## Weitere Entwicklung

* Das controll-Skript wird modularisiert und um weitere Anbieter erweitert.
* Wir wollen auch dynamisch einspeisen.

### Unterst�tzung und Beitrag

Wenn Sie dieses Projekt wertvoll finden, erw�gen Sie bitte, die weitere Entwicklung durch diese Links zu unterst�tzen:
- [Revolut](https://revolut.me/christqki2)
- [PayPal](https://paypal.me/christian1980nrw)

Zus�tzlich k�nnen Sie, wenn Sie in Deutschland sind und sich f�r einen dynamischen Stromtarif interessieren, das Projekt unterst�tzen, indem Sie sich �ber diesen [Tibber Empfehlungslink](https://invite.tibber.com/ojgfbx2e) anmelden. Sowohl Sie als auch das Projekt erhalten einen 50 Euro Bonus f�r Hardware. Bitte beachten Sie, dass ein intelligenter Z�hler oder ein Tracker wie der Pulse [hier erh�ltlich](https://tibber.com/de/store/produkt/pulse-ir) erforderlich ist f�r einen st�ndlichen Tarif.

Wenn Sie einen Erdgastarif ben�tigen oder einen klassischen Stromtarif bevorzugen, k�nnen Sie das Projekt dennoch durch diesen [Octopus Energy Empfehlungslink](https://share.octopusenergy.de/glass-raven-58) unterst�tzen und einen 50 Euro Bonus f�r sich und das Projekt erhalten.

## Haftungsausschluss

Dieses Computerprogramm wird "wie besehen" zur Verf�gung gestellt, und der Benutzer tr�gt das volle Risiko bei der Verwendung.
Der Autor �bernimmt keine Garantien hinsichtlich der Genauigkeit, Zuverl�ssigkeit, Vollst�ndigkeit oder Eignung des Programms f�r einen bestimmten Zweck.
Der Autor haftet nicht f�r Sch�den, die aus der Verwendung oder Unf�higkeit zur Verwendung des Programms entstehen, einschlie�lich direkter, indirekter, zuf�lliger, besonderer oder Folgesch�den.
