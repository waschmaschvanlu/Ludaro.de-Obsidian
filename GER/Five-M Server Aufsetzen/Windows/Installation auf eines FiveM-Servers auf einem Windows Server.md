#FiveM #Einrichten #Windows #Einfach #ger
Bevor wir beginnen, ist es wichtig sicherzustellen, dass du bereits Remote-Desktop-Zugriff auf deinen Windows Server hast. Remote Desktop ermöglicht die Fernsteuerung deines Servers über eine grafische Benutzeroberfläche. Wenn du dies noch nicht eingerichtet hast, solltest du dich an deinen Serveranbieter wenden, um Unterstützung zu erhalten.

## Firewall-Konfiguration

Bevor wir den FiveM-Server installieren, müssen wir sicherstellen, dass die Windows-Firewall richtig konfiguriert ist. Dazu gehören das Öffnen der erforderlichen Ports und die Möglichkeit, die Firewall nach Bedarf auszuschalten.

### Ports öffnen

Du solltest die folgenden Ports für deinen FiveM-Server öffnen:

- TCP-Port 40120 (eingehend und ausgehend)
- UDP-Port 40120 (eingehend und ausgehend)
- TCP-Port 30120 (eingehend und ausgehend)
- UDP-Port 30120 (eingehend und ausgehend)

Öffne diese Ports in der Windows-Firewall, damit Spieler auf deinen Server zugreifen können.

**Hinweis**: Das Ausschalten der Firewall ist nicht empfohlen, da dies ein erhebliches Sicherheitsrisiko darstellen kann. Stattdessen sollten nur die erforderlichen Ports geöffnet werden.

#### So öffnest du Ports in der Windows-Firewall:

1. Gehe zu deinem Windows Server und öffne die "Windows Defender Firewall mit erweiterter Sicherheit".

2. Klicke auf "Eingehende Regeln" in der linken Seitenleiste.

3. Klicke auf "Neue Regel erstellen" in der rechten Seitenleiste.

4. Wähle "Port" und klicke auf "Weiter".

5. Gib die Portnummer ein, die du öffnen möchtest (z. B. 40120) und klicke auf "Weiter".

6. Wähle "Verbindung zulassen" und klicke auf "Weiter".

7. Gib einen Namen für die Regel ein (z. B. FiveM-Server-Port) und klicke auf "Fertig stellen".

8. Wiederhole die Schritte 3 bis 7 für die anderen Ports (UDP-Port 40120, TCP-Port 30120, UDP-Port 30120).

Jetzt sollten die Ports für deinen FiveM-Server geöffnet sein.

## FiveM-Server-Installation

### Was du benötigst

Diese Programme müssen auf deinem Windows Server installiert sein:

- [XAMPP](https://www.apachefriends.org/de/index.html)
- Ein Entpackungs-Tool, wie [WinRAR](http://winrar.de)

Lade außerdem die neueste Version von [FXServer](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) herunter.

### Server-Datenbank einrichten

1. Öffne XAMPP und starte die MySQL- und Apache-Dienste.

2. Gehe auf [http://**DEINE_SERVER_IP**/phpmyadmin](http://**DEINE_SERVER_IP**/phpmyadmin) in deinem Webbrowser, um auf deine MySQL-Datenbank zuzugreifen. Die Zugangsdaten sind normalerweise Benutzername: "root" und kein Passwort.

3. Deine Datenbank ist jetzt einsatzbereit und wird während der FiveM-Server-Einrichtung mit Daten gefüllt.

**Hinweis**: Die Datenbank ist standardmäßig nicht von außen erreichbar. Du kannst nur über phpMyAdmin darauf zugreifen. Weitere Konfigurationen sind erforderlich, um die externe Erreichbarkeit sicherzustellen.

### FiveM-Server-Einrichtung

1. Erstelle einen Ordner an einem Ort, den du dir merken kannst, auf deinem Windows Server.

2. In diesem Ordner erstelle einen weiteren Ordner namens "fx-server" und entpacke die zuvor heruntergeladene FXServer-Version in diesen Ordner.

3. Starte "FXServer.exe". Dies ist dein FiveM-Server. Warte, bis er initialisiert ist und dir einen Code anzeigt.

4. Rufe [http://**DEINE_SERVER_IP**:40120](http://**DEINE_SERVER_IP**:40120) in deinem Webbrowser auf und gib den Code ein, um deinen Server zu verifizieren.

5. Du wirst aufgefordert, deinen Server zum ersten Mal einzurichten. Verwende am besten die "Popular Templates" (beliebte Vorlagen). Andere Optionen sind FiveM-Server ohne RP-Framework, was nicht empfohlen wird. Empfohlene Frameworks sind QBCore oder ESX Legacy (Legacy = neueste Version).

6. Gib deinen Keymaster-Schlüssel ein, den du von [keymaster.fivem.net](https://keymaster.fivem.net) erhalten hast.

7. Sobald der Server initialisiert ist, kannst du FiveM öffnen und dich mit deinem Server verbinden.

Du hast es geschafft! Dein FiveM-Server auf deinem Windows Server ist jetzt einsatzbereit. Du kannst Servereinstellungen in der "server.cfg" im Ordner "ESXLEGACY" oder "QBCore" vornehmen.

>[!info] Die Website [http://**DEINE_SERVER_IP**:40120](http://**DEINE_SERVER_IP**:40120) ist dein txAdmin-Panel. Hierüber kannst du deinen gesamten Server verwalten.

Diese Website ist eine erweiterte Version der [offiziellen CFX-Website](https://docs.fivem.net/docs/server-manual/setting-up-a-server/), die die Installation einer Datenbank einschließt. Alle Credits für diese Seite gehen an CFX. 😊