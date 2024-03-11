# Teil 2: Shellprogrammierung
Bash-Script erstellen:
- leere Datei erstellen (touch meinscript.sh)
- mit Texteditor bearbeiten (nano meinscript.sh)
- im Script mit "#!/bin/bash" festlegen, dass das Script mit Bash ausgeführt werden soll
- Script ausführbar machen (sudo chmod +x meinscript.sh)
- Script ausführen (./meinscript.sh)


## Variablen
- Variablenname darf niemals mit einer Zahl beginnen!
- wird mit dem Zuweisungsoperator = gesetzt. (Ohne Leerzeichen!)
- Auf den Inhalt von Variablen kann mit einem vorangestellten $ zugegriffen werden.
- Variablenname ist case-sensitiv
- Ein auszuwertender Ausdruck muss in $( ) gesetzt werden
- Eine Variable kann mit dem readonly-Befehl als Konstante gesetzt werden


Es gibt in der Bash mind. zwei grundsätzliche Varianten, um einen arithmetischen Ausdruck zu berechnen:

var=$(( Int-Arithmetik ))

var=$[ Int-Arithmetik ]

## Zeichenketten Verarbeitung (Strings)
String-Länge: echo ${#STRING} ($STRING ist eine Variable)

expr index "$STRING" "$SUBSTRING": sucht, an welcher Position der $SUBSTRING von $STRING ist

echo ${STRING:$POS:$LEN}: Extrahiere einen Substring der Länge $LEN von $POS ausgehend aus $STRING.

echo ${STRING[@]/sein/essen}: Ersetze das erste Vorkommen des Substrings ("sein" wird mit "essen" ersetzt)

## Text Processing Tools
grep {options} pattern {files}: gibt alle Linien aus, welche einem Muster entsprechen

cut {option} {datei}: extrahiert spaltenweise Ausschnitte aus Textzeilen

grep: Alle Zeilen, welche nicht gamma enthalten: grep -v "gamma" uebung4.txt

Alle Zeilen, welche 1, 2 oder 3 enthalten (benutzen Sie -E und eine regex): grep --color=auto -E "1|2|3" uebung4.txt

cut: Alle Begriffe vor dem ersten :-Zeichen: cut -d ':' -f  1 uebung4.txt

Alle Begriffe zwischen den beiden :-Zeichen: cut -d ':' -f  2 uebung4.txt

## Arrays
Array erstellen Beispiel: my_array=(apfel banane "Frucht Korb" orange)

Anzahl Elemente im Array: echo  ${#my_array[@]}       

## Shell Funktionen
Grundlegendes Konstrukt: 
function_name {
  Befehle...
}

## Parameterübergabe beim Aufruf eines Scripts
Argumente können einem Skript übergeben werden, wenn es ausgeführt wird. Man schreibt sie, mit Leerzeichen getrennt, nach dem Skriptnamen.

In dem Skript kann das erste Argument mit der Variable $1 referenziert werden, das Zweite mit $2, etc.

## Entscheidungen (If, Case)
grundlegendes Konstrukt: if  [ ausdruck ]; then

Beispiel If:

NAME="George"

if [ "$NAME" = "John" ]; then
  echo "John Lennon"
  
elif [ "$NAME" = "George" ]; then

  echo "George Harrison"
  
else

  echo "Somit bleiben uns Paul und Ringo."
  
fi


Beispiel Case:

mycase=1

case $mycase in

  1) echo "Sie haben Bash gewählt.";;
    
  2) echo "Sie haben Perl gewählt.";;
    
  3) echo "Sie haben Python gewählt.";;
    
  4) echo "Sie haben C++ gewählt.";;
    
  5) exit
    
esac

## Schleifen

**grundlegendes Konstrukt for-Schleife**

for argument in [list]

do

  Befehle...
  
done


**grundlegendes Konstukt while-Schleife**

while [ Bedingung ]

do

  Befehle...
  
done


## Informationskanäle

stdin - Standardeingabekanal (0) 

(z.B. sie geben Zeichen über die Tastatur ein)


stdout - Standardausgabekanal (1) 

(z.B. ein Programm zeigt den Inhalt eines Verzeichnisses am
Bildschirm an)


sterr - Standardfehlerausgabekanal (2) 

(z.B. ein Programm erzeugt einen Fehler und zeigt diesen am
Bildschirm an)


">>" hängt Inhalt an bestehende Datei an, ">" überschreibt den Inhalt
komplett mit Neuem (bsp: ls -la > liste.txt)


2>: füllt die Fehlermeldungen in eine Datei
1>: füllt die Ausgabe in eine Datei


## Cronjobs
auszuführender Befehl

┬ ┬ ┬ ┬ ┬     

│ │ │ │ │

│ │ │ │ └──── Wochentag (0-7, Sonntag ist 0 oder 7)

│ │ │ └────── Monat (1-12)

│ │ └──────── Tag (1-31)

│ └────────── Stunde (0-23)

└──────────── Minute (0-59)


*= Ausführung immer (zu jeder…)
  
*/n = Ausführung aller n

n,x,y = Ausführung um/am n, x und y

Beispiel:

0 10 1 * * 

An jedem 1.Tag im Monat um 10:00 Uhr
