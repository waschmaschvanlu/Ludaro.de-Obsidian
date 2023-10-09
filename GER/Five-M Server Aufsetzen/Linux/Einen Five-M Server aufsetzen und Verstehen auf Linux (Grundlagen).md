#FiveM #Einrichten #Linux #Einfach #ger
# Schritt 1: Vorbereitungen
Bevor du deinen FiveM-Server auf Linux einrichtest, benötigst du einen Linux-Server und SSH-Zugang. Hier sind die grundlegenden Schritte:

## 1.1 Server erstellen
Erstelle einen Linux-Server bei einem Hosting-Anbieter und sorge dafür, dass du vollen Zugriff darauf hast.

## 1.2 SSH-Client installieren
Installiere einen SSH-Client auf deinem Computer. Für Windows-Benutzer empfehle ich PuTTY, während auf macOS und Linux bereits ein SSH-Client namens `ssh` vorhanden ist.

# Schritt 2: Server-Zugriff
Sobald du Zugang zu deinem Server hast, verbinde dich über SSH. Öffne das Terminal auf deinem Computer und verwende den folgenden Befehl:

```shell
ssh root@deine_server_ip
```

Ersetze `deine_server_ip` durch die IP-Adresse deines Servers. Du wirst nach dem Passwort für den Benutzer "root" gefragt.

> Hinweis: Der Benutzer "root" hat Administratorrechte. Du kannst dich nur von deinem originellen Server-PC aus als "root" anmelden.

# Schritt 3: MySQL installieren
Installiere MySQL, um eine Datenbank für deinen FiveM-Server zu erstellen:

```shell
sudo apt-get update
sudo apt-get install mysql-server
```

Während der Installation wirst du nach einem Passwort für den MySQL-Root-Benutzer gefragt. Merke dir dieses Passwort.

# Schritt 4: phpMyAdmin installieren
Installiere phpMyAdmin, um die MySQL-Datenbank zu verwalten:

```shell
sudo apt-get install phpmyadmin
```

Während der Installation wirst du nach dem Webserver, den du verwenden möchtest, gefragt. Wähle "Apache2" aus und bestätige.

Wähle dann "Ja" aus, um phpMyAdmin mit der Apache-Webserver-Konfiguration zu verknüpfen.

Setze ein Passwort für den phpMyAdmin-Benutzer. Merke dir dieses Passwort.

# Schritt 5: MySQL-Benutzer und Datenbank erstellen
Öffne phpMyAdmin in deinem Webbrowser, indem du die URL http://deine_server_ip/phpmyadmin aufrufst. Melde dich als "root" mit dem Passwort an, das du während der MySQL-Installation festgelegt hast.

Erstelle eine neue Datenbank für deinen FiveM-Server und einen neuen Benutzer:

1. Klicke auf "Benutzerkonten" (User accounts) und dann auf "Benutzer hinzufügen" (Add user).

2. Wähle einen Benutzernamen und ein sicheres Passwort aus.

3. Klicke auf die Registerkarte "Datenbankbenutzer" (Database for user) und wähle "Datenbank erstellen und dem Benutzer Berechtigungen für die Datenbank erteilen" (Create database with the same name and grant all privileges).

4. Wähle die zuvor erstellte Datenbank aus und klicke auf "OK".

# Schritt 6: Verzeichnis erstellen
Verwende den Befehl `mkdir`, um ein Verzeichnis für deine Server-Dateien zu erstellen. Dieses Verzeichnis wird im Home-Verzeichnis deines Benutzers angelegt:

```shell
mkdir -p ~/FXServer/server
```

# Schritt 7: Server-Dateien herunterladen
Besuche die [Linux Server Build-Liste von FiveM](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/), kopiere die URL der empfohlenen Server-Version und füge sie in den folgenden Befehl ein:

```shell
wget <url>
```

# Schritt 8: Dateien extrahieren
Wechsle zum Verzeichnis, in dem du die Server-Dateien heruntergeladen hast:

```shell
cd ~/FXServer/server
```

Extrahiere die Dateien mit diesem Befehl:

```shell
tar xf fx.tar.xz
```

# Schritt 9: Server starten
Starte deinen FiveM-Server, indem du die `run.sh`-Datei ausführst:

```shell
./run.sh
```

Nun ist dein FiveM-Server aktiv.

Folge diesen Schritten, um deinen FiveM-Server auf Linux einzurichten, MySQL und phpMyAdmin zu installieren, eine Datenbank zu erstellen und phpMyAdmin zu verwenden.