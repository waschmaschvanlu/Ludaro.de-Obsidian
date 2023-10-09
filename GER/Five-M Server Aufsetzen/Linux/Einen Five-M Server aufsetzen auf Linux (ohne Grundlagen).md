#FiveM #Einrichten #Linux #Schwer #ger
>[!information] Diese Anleitung setzt voraus, dass du bereits grundlegende Kenntnisse in der Verwendung von Linux-Systemen hast.

## Schritt 1: Verzeichnis erstellen
```shell
mkdir -p ~/FXServer/server
```
Erstelle ein neues Verzeichnis, das als Speicherort für die Server-Dateien dienen wird.

## Schritt 2: Server-Dateien herunterladen
Besuche die [Linux Server Build-Liste von FiveM](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/) und kopiere die URL der empfohlenen Server-Version. Verwende dann den `wget`-Befehl, um die Dateien herunterzuladen. Ersetze `<url>` durch die kopierte URL.
```shell
wget <url>
```

## Schritt 3: Dateien extrahieren
Wechsle in das Verzeichnis, in dem du die Server-Dateien heruntergeladen hast, und extrahiere sie. Stelle sicher, dass du das `xz`-Dienstprogramm installiert hast, falls es noch nicht installiert ist. Auf Debian/Ubuntu-Systemen findest du es im Paket `xz-utils`.
```shell
cd ~/FXServer/server
tar xf fx.tar.xz
```

## Schritt 4: MySQL installieren
Installiere MySQL, um eine Datenbank für deinen FiveM-Server zu erstellen:

```shell
sudo apt-get update
sudo apt-get install mysql-server
```

Während der Installation wirst du nach einem Passwort für den MySQL-Root-Benutzer gefragt. Merke dir dieses Passwort.

## Schritt 5: phpMyAdmin installieren
Installiere phpMyAdmin, um die MySQL-Datenbank zu verwalten:

```shell
sudo apt-get install phpmyadmin
```

Während der Installation wirst du nach dem Webserver, den du verwenden möchtest, gefragt. Wähle "Apache2" aus und bestätige.

Wähle dann "Ja" aus, um phpMyAdmin mit der Apache-Webserver-Konfiguration zu verknüpfen.

Setze ein Passwort für den phpMyAdmin-Benutzer. Merke dir dieses Passwort.

## Schritt 6: Server starten
Du kannst den Server nun starten, indem du die `run.sh`-Datei ausführst. Dies startet deinen FiveM-Server auf Linux.

```shell
./run.sh
```

## Schritt 7: Server im Screen starten und verwalten
Wenn du den FiveM-Server auf einem Linux-Server im Hintergrund laufen lassen möchtest, ohne dass er sich beim Schließen des Terminals beendet, kannst du das Tool "Screen" verwenden. Screen ist ein Terminal-Multiplexer, der es dir ermöglicht, Sitzungen zu erstellen und zu verwalten.

### Schritt 7.1: Screen installieren (falls noch nicht installiert)
Falls Screen auf deinem Linux-Server noch nicht installiert ist, kannst du es mit folgendem Befehl nachinstallieren:

```shell
sudo apt-get install screen
```

### Schritt 7.2: Server in einem Screen starten
1. Erstelle eine neue Screen-Sitzung, indem du den folgenden Befehl eingibst:

   ```shell
   screen -S fivem
   ```

   Hierbei wird eine neue Screen-Sitzung mit dem Namen "fivem" erstellt. Du kannst den Namen nach Belieben ändern.

2. Innerhalb der Screen-Sitzung starte deinen FiveM-Server, wie du es zuvor getan hast, indem du die `run.sh`-Datei ausführst:

   ```shell
   ./run.sh
   ```

   Dein FiveM-Server wird jetzt innerhalb der Screen-Sitzung gestartet.

### Schritt 7.3: Screen-Sitzung verlassen
Um die Screen-Sitzung zu verlassen, drücke die Tastenkombination `Ctrl` + `A`, gefolgt von `D` (für "detach"). Damit kehrst du zur normalen Befehlszeile zurück, ohne die Screen-Sitzung zu beenden.

#### Schritt 7.4: Zurück zur Screen-Sitzung wechseln
Wenn du zu einem späteren Zeitpunkt zu deiner Screen-Sitzung zurückkehren möchtest, kannst du den folgenden Befehl verwenden:

```shell
screen -r fivem
```

Das ist die aktualisierte Anleitung ohne die Grundlagen für Linux.