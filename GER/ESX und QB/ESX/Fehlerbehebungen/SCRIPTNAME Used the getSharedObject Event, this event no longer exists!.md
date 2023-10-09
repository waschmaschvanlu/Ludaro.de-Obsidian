#sharedobject #getsharedobject #oldesx #help #error #Scripting #ger

# Was bedeutet dieser Fehler?

Die oben genannte Fehlermeldung besagt:

**SCRIPTNAME** verwendet das Event **getSharedObject**, aber dieses Event existiert nicht mehr!

Dieser Fehler tritt auf, da in den neueren Versionen von ESX (ab Version 1.9) ein Event namens **GetSharedObject** nicht mehr verwendet wird. Stattdessen wurde es durch einen Export ersetzt.

# Warum tritt dieser Fehler auf?

Dieser Fehler tritt auf, da **Events** in FiveM als **unperformant** angesehen werden, was bedeutet, dass sie die Leistung beeinträchtigen können. Aus diesem Grund wurde das Event, das zuvor verwendet wurde, durch einen Export ersetzt. Allerdings stellte sich später heraus, dass dies ein Fehler war, da der Export im Wesentlichen dasselbe wie das Event ist.

## In Skripten sieht das dann so aus:

> [!warning] Das gezeigte Event kann in verschiedenen Skripten unterschiedlich implementiert sein und von dem abweichen, was hier gezeigt wird.

> [!warning] Das hier gezeigte Event kann in verschiedenen Skripten abweichen, da viele Skripte es unterschiedlich umsetzen. Einige schreiben sogar ESX = nil davor, was nicht erforderlich ist und vermieden werden sollte!

### Altes Event:
```lua
TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
```

### Neuer Export:
```lua
ESX = exports["es_extended"]:getSharedObject()
```

# Wie kann ich diesen Fehler beheben?

Es gibt zwei Methoden, um diesen Fehler zu beheben:

1. Ersetzen Sie das Event in jedem Skript durch den Export.
>[!info] Diese Methode wird von ESX unterstützt und empfohlen. Sie ist jedoch etwas anspruchsvoller umzusetzen, spart jedoch an Leistung!

2. Schreiben Sie ESX so um, dass das Event wieder verwendet wird.
>[!warning] Diese Methode wird NICHT von ESX empfohlen, da sie die Leistung beeinträchtigen kann.

Beide Methoden werden hier ausführlich erklärt:

## 1. Ersetzen des Events in jedem Skript durch den Export

Um dies zu erreichen, müssen Sie in dem jeweiligen Skript (Client- und Server-Lua-Dateien) nach dem alten Event suchen:

```lua
TriggerEvent("esx:getSharedObject", function(obj) ESX = obj end)
```

Suchen Sie nach dieser Zeile und ersetzen Sie sie durch den neuen Export:

```lua
ESX = exports["es_extended"]:getSharedObject()
```

Dies kann manchmal schwierig sein, da diese Zeile möglicherweise in einer verschlüsselten Datei steht, auf die Sie keinen Zugriff haben. In diesem Fall sollten Sie Methode 2 in Erwägung ziehen.

## 2. Schreiben Sie ESX so um, dass das Event wieder verwendet wird
>[!warning] Diese Methode sollte nur in Betracht gezogen werden, wenn Methode 1 nicht funktioniert oder wenn Sie auf die Leistung verzichten möchten!

Um dies zu erreichen, öffnen Sie Ihren ESX-Ordner (es_extended) und suchen Sie zuerst in der Datei `client/common.lua` nach folgendem Code:

>[!info] Zur Klarstellung: Dies ist das alte Event, das wir umschreiben, damit es wieder wie früher funktioniert!

```lua
AddEventHandler("esx:getSharedObject", function()
	local Invoke = GetInvokingResource()
	print(("[^1ERROR^7] Resource ^5%s^7 Used the ^5getSharedObject^7 Event, this event ^1no longer exists!^7 Visit https://documentation.esx-framework.org/tutorials/tutorials-esx/sharedevent for how to fix!"):format(Invoke))
end)
```

Ersetzen Sie diesen Codeabschnitt durch:

```lua
AddEventHandler("esx:getSharedObject", function(cb)
	cb(ESX)
end)
```

Führen Sie denselben Schritt auch in der Datei `es_extended/server/common.lua` durch.