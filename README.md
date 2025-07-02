1. Einrichtung des GitHub-Repositories „MeinProjekt“:
   
Ich habe auf GitHub ein neues Repository mit dem Namen "MeinProjekt" erstellt, mit ReadMe.

2. Erstellen eines SSH-Schlüssels:

Ich hatte keine SSH-Schlüssel, deshalb habe ich einen neuen erstellt:$ ssh-keygen -t rsa -b 4096 -C "francescaintrovaia@gmail.com"
Ich habe den öffentlichen Schlüssel mit `cat ~/.ssh/id_rsa.pub` kopiert.
Dann habe ich ihn in GitHub unter Einstellungen → SSH Keys eingefügt mit der Name: ssh Key projekt TP

## Lokales Repository einrichten und Workflow ##

3. Zielverzeichnis öffnen:

Zuerst wurde das Terminal geöffnet und in das gewünschte Verzeichnis gewechselt, in dem das lokale Git-Repository gespeichert werden soll:
cd ~/git

4. Repository von GitHub klonen
   
Anschließend wurde das Repository „MeinProjekt“ über SSH von GitHub geklont. Dazu wurde folgender Befehl verwendet (mit dem eigenen GitHub-Benutzernamen):
git clone git@github.com:francescaintrovaia/MeinProjekt.git
Nach dem Klonen befindet sich nun eine lokale Kopie des Repositories im Verzeichnis ~/git/MeinProjekt.

5. In das geklonte Repository wechseln
   
Mit dem folgenden Befehl wurde in das geklonte Projektverzeichnis gewechselt:
cd MeinProjekt
Nun befindet man sich im lokalen Repository „MeinProjekt“, das mit dem Remote-Repository auf GitHub verbunden ist.

7. Git-Konfiguration (Name und E-Mail)
   
Git wurde mit dem eigenen Namen und der mit GitHub verknüpften E-Mail-Adresse konfiguriert:
git config user.name "Francesca Introvaia"
git config user.email "francescaintrovaia@gmail.com"
Mit diesen Einstellungen werden zukünftige Commits korrekt mit dem GitHub-Account verknüpft.

8. Initialer Commit im lokalen Repository:
    
Ich habe versucht, die Datei `main.py` hinzuzufügen, aber sie existierte noch nicht:
   git add main.py
   fatal: pathspec 'main.py' did not match any files
Dann habe ich die Datei mit dem Befehl touch erstellt:
touch main.py
Danach konnte ich die Datei erfolgreich zum Staging-Bereich hinzufügen:
git add main.py
Schließlich habe ich den ersten Commit durchgeführt:
git commit -m "Initialer Commit"
[main 79d3873] Initialer Commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.py
 
9.Neue Datei im Feature-Branch hinzufügen

Zum Branch feature gewechselt:
git switch feature
Neue Datei im Unterverzeichnis erstellt:
mkdir -p utils
touch utils/database.py
Funktion in database.py geschrieben:
def connect_to_database():
    print("Datenbankverbindung erfolgreich!")
Datei zum Staging-Bereich hinzugefügt und Commit erstellt:
git add utils/database.py
git commit -m "Neue Funktion hinzugefügt"

10.Hauptdatei im Feature-Branch aktualisieren

Sichergestellt, dass man sich im feature-Branch befindet.
Mit git add main.py versucht, Änderungen zu übernehmen.
Keine Änderungen vorhanden, daher:
nothing to commit, working tree clean

11. Wechsel zum Haupt-Branch und Commit
    
Beim Versuch, zum Branch `master` zu wechseln, trat ein Fehler auf, da dieser Branch nicht existiert. Stattdessen wurde erfolgreich zum Branch `main` gewechselt:
git switch main
Anschließend wurde versucht, main.py zu committen. Da keine Änderungen vorlagen, wurde kein neuer Commit erstellt:
git add main.py
git commit -m "Hauptdatei aktualisiert"
nothing to commit, working tree clean

12. Merge-Konflikt:
    
Ich habe zuerst den Branch `feature` mit `git switch feature` gewechselt.
Dort habe ich die Datei `main.py` mit `notepad` geöffnet und Änderungen vorgenommen.
Änderungen wurden mit `git add main.py` und `git commit -m "Änderung im feature-Branch"` festgeschrieben.
Danach bin ich mit `git switch main` zurück zum `main`-Branch gewechselt.
Auch im `main`-Branch habe ich `main.py` bearbeitet und die Änderungen committed.
Beim Versuch, den `feature`-Branch in `main` zu mergen (`git merge feature`), trat ein Merge-Konflikt auf:Auto-merging main.py
CONFLICT (content): Merge conflict in main.py
Automatic merge failed; fix conflicts and then commit the result.
Der Konflikt entstand, weil beide Branches die gleiche Datei `main.py` verändert hatten.

13. Merge-Konflikt lösen und abschließen
    
Öffnen der Datei `main.py` mit einem Texteditor (z. B. `notepad`).
Git markiert die konfliktierenden Stellen mit speziellen Markierungen.
Die gewünschten Änderungen werden ausgewählt und die Konflikt-Markierungen entfernt.
Datei wird gespeichert.
Datei mit `git add main.py` zum Commit vorgemerkt.
Merge mit `git commit -m "Merge-Konflikt in main.py manuell gelöst"` abgeschlossen.

14.Untracked Files hinzufügen:

git status zeigt untracked Dateien (feature.py, main.txt).
Versuch git add feature schlägt fehl, da kein solches File existiert.
Stattdessen einzeln mit git add feature.py und git add main.txt hinzufügen.

15. Änderungen pushen
    
Mit git push werden alle lokalen Commits ins Remote-Repository übertragen.
Ausgabe zeigt erfolgreiches Pushen und Hinweis auf neues Repository-URL.
