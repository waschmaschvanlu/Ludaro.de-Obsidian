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


# Schritt 3 Ausführen des Skripts:
nun gebt dashier ein: 
```bash
curl -s https://raw.githubusercontent.com/Twe3x/fivem-installer/main/setup.sh
```

und nun werdet ihr durch eine Installation durchgeführt