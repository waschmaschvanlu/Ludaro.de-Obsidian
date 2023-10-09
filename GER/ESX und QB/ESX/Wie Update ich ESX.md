#ESX #update #ger
> [!info] Diese Website ist noch zu 0% fertig und enthält nur meine Notizen.

# Von EssentialMode (1.1) auf Legacy umsteigen

Es ist bedauerlicherweise nicht möglich, von ESX 1.1 auf neuere Versionen zu aktualisieren. Es wird empfohlen, den gesamten Server neu aufzusetzen und alle benötigten Ressourcen einzeln zu übertragen, da sich die Struktur von 1.1 zu ESX Legacy vollständig geändert hat.

Eine Möglichkeit, dies in txAdmin zu tun, besteht darin, die "Master Actions" zu verwenden und den Server neu einzurichten. Beachte, dass dies NICHT den Serverordner löscht, sondern lediglich einen neuen erstellt. Dort kannst du dann ESX Legacy auswählen und direkt mit der neuesten Version von ESX beginnen.

# Von ESX 1.2 auf ESX Legacy umsteigen

Um von ESX 1.2 auf ESX Legacy umzusteigen, gehe auf den [esx_core](https://github.com/esx-framework/esx_core) GitHub und lade das gesamte Repository herunter. Importiere dann die [SQL](https://github.com/esx-framework/esx_core/blob/main/database.sql) in deine Datenbank und lade [oxmysql](https://github.com/overextended/oxmysql/releases/tag/v2.7.5) herunter. Starte oxmysql VOR es_extended und entferne den es_extended Ordner. Lade stattdessen den [core](https://github.com/esx-framework/esx_core/tree/main/core) Ordner in deinen Server hoch und starte diesen anstelle von es_extended.

Überprüfe, ob bereits Skripte im core Ordner existieren. Wenn ja, lösche diese entweder im core Ordner oder in deinem Resource Ordner.

Um mehr darüber zu erfahren, lies bitte die [ESX-Wiki](https://documentation.esx-framework.org/legacy/installation/).