# LA1550

# Robocode

## Aufgabenstellung und Ziele

Im Lernatelier durften wir mithilfe von Robocode einen "Juniorbot", also einen kleinen Roboter programmieren, welches danach gegen anderen Robotern antreten und mit ihnen kämpfen kann. Der Roboter wurde mit Javascript programmiert. Ich werde Ihnen erklären, welche Strategie ich für das Programmieren des Roboters ausegewählt habe. 

**Ziele**:
1. Der Leser versteht, was die Strategie meines Roboters ist.

## Inhalt 1
Damit man im Spiel mit den anderen Robotern gewinnen kann, braucht man eine Strategie zum Ausweichen der Angriffe anderen Computer oder zum Angreifen vom eigenen Roboter. Meine Strategie war, dass mein Roboter, namens EVA01, sich bewegt und nach jeder Bewegung das Umfeld scannt, um zu sehen, ob es Gegner im Umfeld hat. Wenn ein Roboter gescannt wird, schaut EVA01 zuerst, ob der gescannte Roboter mehr als 41 Energiepunkte hat. Wenn es mehr als 41 Energiepunkte hat, wird der Roboter ignoriert, damit mein Roboter nur die Gegner angreift, welche weniger Energie haben, damit EVA01 mehr "kills" hat. Wenn der Abstand zum gescannten Roboter zu gross ist, wird es auch ignoriert, weil Schüsse einer grösseren Distanz mehr Energie meines Roboters aufbraucht. Wenn die Energie kleiner als 41 ist und der Gegner sich in der Nähe befindet, greift mein Roboter an, indem es sich in die Richtung des Gegners dreht, zum Gegner fährt, schiesst, und dann wieder scannt, wo der Gegner jetzt ist, um dies zu wiederholen. Sobald mein Roboter einen Gegner trifft, wird dieser Roboter mehrmals angegriffen bis er stirbt, wenn die Energie vom Gegner tiefer als 16 ist, weil das Töten des Gegners einfacher ist, wenn sie wenig Energie haben. Wenn EVA01 angegriffen wird, dreht es sich 200° weg vom Gegner, von dem es angegriffen wurde und fährt weg. 


## Inhalt 2
Hier ist ein Beispiel für die Angriffe auf den gescannten Gegner:
```javascript
public void onScannedRobot() {
		if (scannedBearing >= 0) {
			turnDirection = 1;
		} else {
			turnDirection = -1;
	    }
		bearGunTo(scannedBearing);
		if(scannedEnergy > 41) {
		   //wenn die Energie tiefer als 41 ist
		fire(1);
		turnRight(200);
		ahead(500);
		} else if (scannedDistance >= 200) {
		   //wenn der Gegner zu weit entfernt ist
		fire(1);
		} else {
		ahead(scannedDistance + 10);
		bearGunTo(scannedBearing);
		fire();
		fire(3);
		fire();
		turnRight(scannedBearing);
		bearGunTo(scannedBearing);
		ahead(scannedDistance + 10);
		fire(3);
		fire(2);
	    }
	}
```

## Inhalt 3

Hier zeige ich, wie mein Roboter aussieht beim Spielen
[YouTube Video von EVA01](https://www.youtube.com/watch?v=6XaXqMKtn0o)

## Verifikation + Reflexion 

**Reflexion**:
Ich habe gelernt, wie man mit Robocode programmiert. Das schwierige war die Strategie, da ich nicht wusste, wie die Gegner spielen würden, und ich konnte darum nicht eine Strategie erstellen, die alles ausweicht. Ich hatte also keinen bestimmten Plan für eine Strategie, was das Programmieren schwierig machte. Mein letztes VBV war, dass ich meine Gruppenmitglieder anspreche und mit ihnen zusammen arbeite, jedoch war dieser Auftrag keine Gruppenarbeit, also konnte ich dieses Ziel nicht erreichen.

VBV: Das nächste Mal werde ich eine Strategie erstellen, bevor ich anfange zu programmieren, damit ich weiss, was ich überhaupt programmieren muss.

**Verifikation**:
Ziel 1: Ich habe dieses Portfolio meinem Pultnachbar gezeigt, *Ziel erreicht*
