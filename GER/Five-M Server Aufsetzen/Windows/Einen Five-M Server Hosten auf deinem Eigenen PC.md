#FiveM #Einrichten #Windows #eigenerpc #Einfach #ger
> [!warning] Wenn du einen FiveM Server auf deinem eigenen PC hosten möchtest, solltest du wissen, dass du diesen NICHT für die Öffentlichkeit freischalten solltest, da dies ein Sicherheitsrisiko darstellen kann und unbefugten Zugriff ermöglichen könnte. Es ist ratsam, deinen eigenen PC-Server nur für persönliche Tests und Experimente zu verwenden.

Lokal = Auf deinem eigenen PC

# Was benötige ich?
Diese Programme müssen installiert werden:
- [ ] [XAMPP](https://www.apachefriends.org/de/index.html)
- [ ] Ein beliebiges Entpackungs-Tool, z.B. [Winrar](http://winrar.de)

Diese Dateien müssen heruntergeladen werden:
- [ ] [FXServer](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) am besten die neueste Version (6271)
### Optional
- [ ] [HeidiSQL](https://www.heidisql.com/) (für einen besseren Datenbankzugriff)

Du benötigst mindestens 10 GB freien Speicherplatz (mehr ist besser) und etwas Zeit. 😄

Sobald du XAMPP installiert hast, sieht es so aus, wenn du es startest:

(BILD von XAMPP)

Jetzt klicke auf "MYSQL" und "Apache" und wähle "Start", dann warte, bis beide Dienste gestartet sind.

Hurra! Du hast jetzt deine eigene Datenbank! Du kannst dich entweder mit HeidiSQL oder über phpMyAdmin (ein Tool im Webbrowser) auf deine Datenbank verbinden, indem du die Website [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) aufrufst.

>[!info] Wichtig! Da dies deine Datenbank ist, muss sie **immer** gestartet sein, bevor du deinen Server startest. Öffne einfach XAMPP und starte MySQL und Apache. 🙂

Diese Datenbank ist noch leer (die Zugangsdaten sind Benutzername: root und kein Passwort). Sie wird mit Daten gefüllt, wenn du deinen FiveM-Server einrichtest.

Jetzt erstellen wir deinen FiveM-Server. Erstelle an einem Ort deiner Wahl einen neuen Ordner, den du dir merken kannst. In diesem neuen Ordner erstellst du einen weiteren Ordner namens "fx-server" und entpackst dort die FXServer-Daten, die du zuvor heruntergeladen hast. Sobald das erledigt ist, starte FXServer.exe (dies ist dein Server). Sobald der Server gestartet ist, erhältst du einen Code, den du auf der Website [http://127.0.0.1:40120](http://127.0.0.1:40120) eingibst, um deinen Server zu verifizieren. Dann wirst du aufgefordert, deinen Server zum ersten Mal zu installieren. Am besten verwendest du die "Popular Templates" (beliebte Vorlagen). Andere Optionen sind FiveM-Server ohne RP-Framework, was nicht empfohlen wird. Ich empfehle entweder QBCore oder ESX Legacy aus den beliebten Frameworks. (Legacy = neueste Version) Jetzt gib einfach deinen Keymaster-Schlüssel ein, den du von [keymaster.fivem.net](https://keymaster.fivem.net) erhalten hast, und du kannst FiveM öffnen und dich mit deinem Server verbinden, sobald er gestartet ist!

In dem Ordner "txData" ist ein neuer Ordner mit dem Namen "ESXLEGACY" oder "QBCore" entstanden. Dort findest du deine server.cfg (für Servereinstellungen) und deinen "resources"-Ordner, in den du deine Ressourcen hochladen kannst. 😊

>[!info] Die Website [http://localhost:40120](http://localhost:40120) oder [http://127.0.0.1:40120](http://127.0.0.1:40120) ist dein txAdmin-Panel. Hier kannst du deinen gesamten Server verwalten.

Diese Website ist eine erweiterte Version der [offiziellen CFX-Website](https://docs.fivem.net/docs/server-manual/setting-up-a-server/), die die Installation einer Datenbank einschließt. Alle Credits für diese Seite gehen an CFX. 😄