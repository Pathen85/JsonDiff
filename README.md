Dieses Tool vergleicht eure JSON-Datei mit der von SP Consulting. Es werden KEINE Zahlen verglichen! Es wird lediglich überprüft, ob euer JSON alle Kombinationen aus den Attributen SBU, Product Main Group, Region, Subregion, Sales Type, Entry Type (und KPI) enthält, die auch im SP JSON vorkommen. Die Kombinationen die fehlen, werden direkt in die Konsole ausgegeben.


Voraussetzungen:
das SP-JSON muss im gleichen Ordner wie die jar-Datei liegen und wie folgt benannt sein: "spJson.json"
euer JSON muss ebenfalls im gleichen Ordner wie die jar-Datei liegen und wie folgt benannt sein: "resultJson.json"
beide JSON-Dateien müssen natürlich auf den gleichen Werten für die Parameter plan_year, period und currency basieren
Java 8 muss installiert sein und als PATH-Systemvariable gesetzt sein, damit die Kommandozeile den java Befehl kennt (Google hilft euch gerne weiter ;) )


Benutzung:
öffnet die Kommandozeile und navigiert in den Ordner, in dem die jar-Datei liegt
führt folgenden Befehl aus:

java -cp jsonDiff.jar jsonDiff.JsonDiff <parameter1> <parameter2>


Parameter 1 ist entweder “true” oder “false”. True bedeutet dass die KPI mit ausgegeben wird. False blendet das Attribut aus.
Parameter 2 ist auch entweder “true” oder “false”. True bedeutet, dass ausgegeben wird, was im SP-Json vorkommt aber bei euch fehlt. False bedeutet, dass ausgegeben wird, was bei euch vorkommt, aber im SP-Json fehlt.
Beispiel Befehl (ohne KPI-Attribut; was fehlt bei euch):

java -cp jsonDiff.jar jsonDiff.JsonDiff false true


falls die Ausgabe zu lang wird, kann der Output direkt in eine Datei geschrieben werden:

java -cp jsonDiff.jar jsonDiff.JsonDiff <parameter1> <parameter2> > output.txt



Mögliche Ergebnisse:

Ideal: Es werden keine Elemente aufgeführt → Euer JSON enthält alle Einträge, die auch SP in seinem JSON hat

Vorsicht: Es werden Elemente aufgeführt → Euer JSON ist zwar generell im korrekten Format, aber es gibt Einträge im SP JSON, die in eurem JSON fehlen

Kritisch: Euer JSON ist strukturell fehlerhaft und kann deshalb nicht gemappt werden. Unbedingt Fehler suchen und beheben!
