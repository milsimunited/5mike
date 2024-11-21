# 5mike
Enfusion in 5 Minuten

Für alle die keinen Bock haben, stundenlang Video-Tutorials zu gucken und sich rumzuärgern, 
weil alles so anders ist als in Arma 3.


## Tipps
Prefabs: Alles was wir im Resource Browser suchen, nehmen wir aus dem Ordner "Prefabs". Das sind funktionsfähig vorkonfigurierte Pakete, wo alle nötigen Komponenten schon dabei sind. Rechts in der Leiste kann man diese samt Unterkomponenten konfigurieren. Dabei nichts löschen, sondern nur deaktivieren.

Positionierung: Dazu gibt es den Trick, ein vorhandenes Objekt auf der auszuwählen und in der rechten Leiste bei Transformation auf das Label "Coords" Rechtsklick und Copy zu machen, was alle drei Koordinaten mitnimmt, die man dann bei z.B. der Area reinpasten kann. Geht oft erheblich schneller.


## Basis-Module und Spieler-Slots
Von Steam die Reforger Tools installieren.

Alle Dependencies müssen in den Tools als Projekt der Liste hinzugefügt werden.

Links in der Seitenleiste eine "world" auswählen und die .ent Datei in dem Ordner doppelklicken. 

Im  World-Editor auf File->New World->Sub-scene.
Dann "Save As" in den Projekt-Ordner am besten in einen Unterordner "worlds" so wie da wo man es her hat. 
Dort liegt dann eine .ent, eine .ent.meta und ein Ordner mit _Layers. Die .layer-Dateien darin enthalten am Ende alles was im World Editor platziert wird.

Jetzt kann man im eigentlichen Sinne loslegen.

Folgende Prefabs platzieren:
SCR_GameModeEditor
PerceptionManager
SCR_AIWorld_Eden
SpawnPoint_ der gewünschten Faction

Den FactionManager auswählen (Unterpunkt von GameMode) und in der Leiste rechts bei der gewünschten Faction ein Häkchen bei "Is Playable" setzen.

Ab diesem Zeitpunkt kann man auf Play drücken und es testen.

Den LoadoutManager auswählen (Unterpunkt von GameMode) und in der Leiste rechts die Player Loadouts aufklappen. Die mit der gewünschten Affiliated Faction stehen später zur Auswahl. Wenn man bei einer bereits ausgefüllten Loadout Resource auf dei Lupe klickt, öffnet sich direkt der Ordner mit den eigentlichen Charakter Prefabs. DIe kann man dann auf das Feld drag&droppen.


## Spawn-Trigger mit dem "Scenario Framework"
Im Resource Browser nach SF-Sample-TaskClearArea.ent suchen und doppelklicken. 

"Save World As" in den eigenen Projektordner neben die eigene World. 
Ordner \worlds\SF-Sample-TaskClearArea_Layers öffnen.
default.layer in etwas anderes wie z.B. scenario.layer umbenennen und in den Layer Ordner unserer World kopieren.

Unsere World wieder öffnen durch Doppelklick auf die .ent-Datei.

Wir haben jetzt den neuen Layer mit einer "Area". Das ist sowas wie ein Trigger in Arma 3 Eden, mit dem man Zeug spawnen und despawnen kann.

Jetzt die Area an eine gewünschte Stelle schieben.

Bei der Area in der rechten Leiste kann man jetzt unter anderem die Dimensionen und Dynamic Despwan konfigurieren. 

Als Unterpunkt der Area findet man Layer_AI mit drei Slots. Es heißt zwar AI, aber man kann hier beliebige Prefabs auf das "Object To Spawn"-Feld ziehen.


## Missions-Config um es im Multiplayer starten zu können
Diese IDs hier {8FD22B90CBC1D494} bekommt man, wenn man Zeug aus dem eigenen Addon-Ordner via Editor einfügt.

Missions/5mike.conf
```SCR_MissionHeader {
 World "{8FD22B90CBC1D494}worlds/Arland.ent"
 m_sName "5mike"
 m_sAuthor "MilSim United"
 m_sDescription "5mike"
 m_sIcon "{218F67A2EC0351AA}Assets/images/u.edds"
 m_sLoadingScreen "{218F67A2EC0351AA}Assets/images/u.edds"
 m_sPreviewImage "{218F67A2EC0351AA}Assets/images/u.edds"
 m_iPlayerCount 32
 m_eEditableGameFlags 7
 m_eDefaultGameFlags 7
 m_bIsSavingEnabled 1
 m_sSaveFileName "5mike_arland"
 m_bOverrideScenarioTimeAndWeather 1
 m_iStartingHours 7
 m_fDayTimeAcceleration 6
 m_fNightTimeAcceleration 12
 m_bMapMarkerEnableDeleteByAnyone 1
 m_iMapMarkerLimitPerPlayer 32
}```

Missions/scenario.conf.meta
```MetaFileClass {
 Name "{FA38849EE56C68EB}Missions/5mike.conf"
 Configurations {
  CONFResourceClass PC {
  }
  CONFResourceClass XBOX_ONE : PC {
  }
  CONFResourceClass XBOX_SERIES : PC {
  }
  CONFResourceClass PS4 : PC {
  }
  CONFResourceClass HEADLESS : PC {
  }
 }
}```
