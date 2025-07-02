# Einrichtung des GitHub-Repositories „MeinProjekt“:
1. Ich habe auf GitHub ein neues Repository mit dem Namen "MeinProjekt" erstellt, mit ReadMe.
Erstellen eines SSH-Schlüssels: 1. Ich hatte keine SSH-Schlüssel, deshalb habe ich einen neuen erstellt:$ ssh-keygen -t rsa -b 4096 -C "francescaintrovaia@gmail.com"
2. Ich habe den öffentlichen Schlüssel mit `cat ~/.ssh/id_rsa.pub` kopiert.
3. Dann habe ich ihn in GitHub unter Einstellungen → SSH Keys eingefügt mit der Name: ssh Key projekt TP
## Lokales Repository einrichten und Workflow
### 1. Zielverzeichnis öffnen
Zuerst wurde das Terminal geöffnet und in das gewünschte Verzeichnis gewechselt, in dem das lokale Git-Repository gespeichert werden soll:
```bash
cd ~/git
2. Repository von GitHub klonen
Anschließend wurde das Repository „MeinProjekt“ über SSH von GitHub geklont. Dazu wurde folgender Befehl verwendet (mit dem eigenen GitHub-Benutzernamen):
git clone git@github.com:francescaintrovaia/MeinProjekt.git
Nach dem Klonen befindet sich nun eine lokale Kopie des Repositories im Verzeichnis ~/git/MeinProjekt.
3. In das geklonte Repository wechseln
Mit dem folgenden Befehl wurde in das geklonte Projektverzeichnis gewechselt:
cd MeinProjekt
Nun befindet man sich im lokalen Repository „MeinProjekt“, das mit dem Remote-Repository auf GitHub verbunden ist.
4. Git-Konfiguration (Name und E-Mail)
Git wurde mit dem eigenen Namen und der mit GitHub verknüpften E-Mail-Adresse konfiguriert:
git config user.name "Francesca Introvaia"
git config user.email "francescaintrovaia@gmail.com"
Mit diesen Einstellungen werden zukünftige Commits korrekt mit dem GitHub-Account verknüpft.
5. Initialer Commit im lokalen Repository:
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
5.Neue Datei im Feature-Branch hinzufügen
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
6.Hauptdatei im Feature-Branch aktualisieren
Sichergestellt, dass man sich im feature-Branch befindet.
Mit git add main.py versucht, Änderungen zu übernehmen.
Keine Änderungen vorhanden, daher:
nothing to commit, working tree clean
7. Wechsel zum Haupt-Branch und Commit
Beim Versuch, zum Branch `master` zu wechseln, trat ein Fehler auf, da dieser Branch nicht existiert. Stattdessen wurde erfolgreich zum Branch `main` gewechselt:
git switch main
Anschließend wurde versucht, main.py zu committen. Da keine Änderungen vorlagen, wurde kein neuer Commit erstellt:
git add main.py
git commit -m "Hauptdatei aktualisiert"
# → nothing to commit, working tree clean
8. Merge des Feature-Branches in den Main-Branch und Push auf GitHub
Wechsel auf den Main-Branch:
git switch main
Merge des Feature-Branches in Main:
git merge feature
In diesem Fall erfolgte der Merge als Fast-Forward, da keine Konflikte auftraten.
Die Änderungen aus dem Feature-Branch (z.B. utils/database.py) wurden in Main integriert.
Push der Änderungen auf das Remote-Repository:
git push origin main
Die Änderungen sind nun auch auf GitHub sichtbar.
