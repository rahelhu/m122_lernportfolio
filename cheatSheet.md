~: Kürzel für das Heimatverzeichnis

;: trennt einzelne Befehle voneinander (Sequenz)

|: verkettet einzelne Befehle (Piping)

#: leitet einen Kommentar ein

\: (am Ende einer Zeile) Befehlszeile lässt sich auf der nächsten Zeile weiter fahren.

&: (am Ende eines Befehls) führt Befehl im Hintergrund aus 

### Hilfe
man {Befehlsname}: öffnet manual von Befehle

apropos {Stichwort}: dursucht Hilfeseiten nach Stichwort

which {Befehl}: findet den Ort eines installierten Programmes

### systemspezifisch
reboot: startet System neu

halt: schaltet System ab

### verzeichnisrelevant
pwd: zeigt aktuelles Verzeichnis

cd {Zielverzeichnis}: ändert Verzeichnis

mkdir {Verzeichnisname}: erstellt neues Verzeichnis

rmdir {Verzeichnisname}: löscht Verzeichnis

ls {Verzeichnisname}: listet Verzeichnisinhalt auf

find: sucht Dateien innerhalb eines Verzeichnisses inkl. Unterverzeichnis

### dateirelevant
cp: kopiert Dateien/Verzeichnisse

rm: löscht Dateien/Verzeichnisse

mv: verschiebt oder benennt eine Datei um

touch: erstellt neue Datei

cat: gibt Dateiinhalt aus

wc: zählt Wörter oder Linien eines Datei-Inhaltes

echo: gibt Zeichenkette aus

### Aliase
alias: nutzerspezifisches Kürzel für einen Befehl oder eine Befehlskombination

alias {aliasname}="{befehl mit params/args}"
