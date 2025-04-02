Praktikum

Meilensteine

Einarbeitung in Dämmwerk Gui
Einarbeitung in die Dämmwerk Installationsdateien 
Einarbeitung in die Lybaris zur Automatisierung 
Auslesen der Daten von Dataholz.eu 
Jasondatei mit den Ausgelesenen Daten erstellen
Gui programmieren zur Steuerung der .csv Dateien
Listenzuordnung der Bauteiletypen programmieren
eine .csv Datei mit einem Bauteil in Dämmwerk importieren
	Grafik korrekt darstellen lassen 
Außenwände aus Deutschland importieren
	Grafik der Außenwände korrekt darstellen
Innenwände aus Deutschland importieren
	Grafik der Innenwände korrekt darstellen
Trennwände aus Deutschland importieren 
	Grafik der Trennwände korrekt darstellen
Geschossdecken aus Deutschland importieren 
	Grafik der Geschossdecken korrekt darstellen
Decke gegen unbeheizt aus Deutschland importieren
	Grafik der Decke gegen unbeheizt korrekt darstellen
Geneigtes Dach aus Deutschland importieren
	Grafik des Geneigtes Dach korrekt darstellen


*** Beispieldatei für DÄMMWERK Bauteilimport
*** Kennwort "Bauteil" für neues Bauteil
*** BtTyp: 1-Decke gegen außen, Dachdecke, 2-Decke zum Dachraum, hinterlüftet, 3-Außenwand / Außentür, 4-AW hinterlüftet, 5-AW gegen Erdreich, 6/12-Trennwand,
***        8-Kellerdecke, 9-Fußboden zum Erdreich, 7/13/14/15-Whg-Trenndecken, 16-Decke nach unten hinterlüftet, 17-Decke aufgeständert, 20-Fenster 
*** oder k.A. -> später einstellen  
*** folgende Zeilen = Baustoffparameter, Schichten von innen nach außen
*** Typ (DW) = DÄMMWERK Baustoffgruppe oder k.A. 
**************************************** Beginn Struktur
* Bauteil;Beschreibung 1;BtTyp;
* Baustoffname 1;Rohdichte kg/m³;Schichtdicke m;Flächengewicht kg/m²;lambda-Wert W/(mK);R-Wert m²K/W;mü min;mü max;cspez J/(kgK);Typ (DW); 
* Baustoffname 2;Rohdichte kg/m³;Schichtdicke m;Flächengewicht kg/m²;lambda-Wert W/(mK);R-Wert m²K/W;mü min;mü max;cspez J/(kgK);Typ (DW); 
* Baustoffname 3;...
* Bauteil;Beschreibung 2;Bttyp;
* Baustoffname 1;Rohdichte kg/m³;Schichtdicke m;Flächengewicht kg/m²;lambda-Wert W/(mK);R-Wert m²K/W;mü min;mü max;cspez J/(kgK);Typ (DW); 
* Baustoffname 2;...
* Baustoffname 3;...
*Schichtdicke mm-> /1000
*cspez kJ/(kgK) -> J/(kgK) mal 1000



*************************************** Ende Struktur
*************************************** Beginn Beispieldaten
Bauteil;Aussenwand awmhhi01a 03;4;
Gipsplatte Typ DF (GKF);1000,00;0,0125;0,00;0,320;0,00;0,00;0,00;1100;33;
Gipsplatte Typ DF (GKF);800,00;0,0125;0,00;0,250;0,00;0,00;0,00;1050;33;
Mineralwolle (variierbarer Daemmstoff);11,00;0,3;0,00;0,040;0,00;0,00;0,00;1030;51;
Holz Fichte Lattung 60/60 auf Schwingbuegel, e=625;450,00;0,01;0,00;0,120;0,00;0,00;0,00;1050;106;
Brettsperrholz (verklebt) (mind. 3-lagig, Decklage mind. 30 mm);500,00;0,03;0,00;0,130;0,00;0,00;0,00;1600;61;
Mineralwolle (variierbarer Daemmstoff);11,00;0,3;0,00;0,040;0,00;0,00;0,00;1030;51;
Leichter Holzbautraeger (I-Traeger) mit Vollholzgurten (60/45) und Hartfasersteg;800,00;0,03;0,00;0,400;0,00;0,00;0,00;0,1700;65;
MDF;600,00;0,015;0,00;0,140;0,00;0,00;0,00;0,1700;63;
Holz Fichte Lattung (30/60) - Hinterlueftung;450,00;0,3;0,00;0,120;0,00;0,00;0,00;1600;140;
Holzfassade;450,00;0,024;0,00;0,120;0,00;0,00;0,00;1600;61;
************************************** Ende Beispieldaten