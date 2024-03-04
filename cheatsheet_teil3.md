# Anhang
## REGEX
beliebiges Zeichen: .

Zeichenauswahl: [axz] [2–7]

Zeichenauswahl Zeichen ausschliessen: [^a–f]

Whitespace-Zeichen: /s

alle Zeichen ausser Whitespace: /S

?:	Der Ausdruck, der voransteht, ist optional, d. h., er kann ein Mal vorkommen, muss aber nicht.

+:	Der Ausdruck muss mindestens ein Mal vorkommen, darf aber auch mehrmals vorhanden sein.
  
*:	Der Ausdruck darf beliebig oft oder auch gar nicht vorkommen.
  
{min,}:	Der voranstehende Ausdruck muss mindestens min-mal vorkommen.

{min,max}:	Der voranstehende Ausdruck muss mindestens min-mal, darf aber nicht mehr als max-mal vorkommen.

{n}:	Der voranstehende Ausdruck muss genau n-mal vorkommen.

Alternativen: | (Beispiel: (asdf|ASDF))

## Grep
sucht nach einem Muster und gibt die passenden Zeilen aus.

**Varianten:**

egrep: extended grep -> versteht mehr reguläre Ausdrücke

fgrep: fixed grep -> versteht weniger reguläre Ausdrücke und ist somit schneller

rgrep: rekursive grep -> für die rekursive Suche in Unterverzeichnissen verwendet

**Syntax:**
grep muster datei1 [datei2] ... [datein]

**reguläre Ausdrücke von grep:**
| Zeichen | Funktion               | Beispiel        | Bedeutung                                                                           |
| ------- | ---------------------- | --------------- | ----------------------------------------------------------------------------------- |
| ^       | Anfang der Zeile       | `^wort`         | Gibt alle Zeilen aus, die mit »wort« beginnen.                                     |
| $       | Ende der Zeile         | `wort$`         | Gibt alle Zeilen aus, die mit »wort« enden.                                        |
| ^$      | komplette Zeile        | `^wort$`        | Gibt alle vollständigen Zeilen mit dem Muster »wort« aus.                           |
| .       | beliebiges Zeichen     | `w.rt`          | Gibt alle Zeilen aus, die ein »w«, einen beliebigen Buchstaben und »rt« enthalten. |
| *       | beliebig oft           | `wort*`         | Gibt alle Zeilen aus mit beliebig vielen (oder auch gar keinen) des vorangegangenen Zeichens. |
| .*      | beliebig viele         | `wort.*wort`    | Die Kombination .* steht für beliebig viele Zeichen.                                |
| []      | ein Zeichen aus dem Bereich | `[Ww]ort`  | Gibt alle Zeilen aus, welche Zeichen in dem angegebenen Bereich (im Beispiel nach »Wort« oder »wort«) enthalten. |
| [^]     | kein Zeichen aus dem Bereich | `[^A–VX–Za–z]ort` | Die Zeichen, die im angegebenen Bereich stehen, werden nicht beachtet (im Beispiel kann »Wort« gefunden werden, nicht aber »Tort« oder »Sort« und auch nicht »wort«). |
| \<      | Anfang eines Wortes    | `\<wort`        | Findet hier alles, was mit »wort« beginnt (bspw. »wort«, »wortreich« aber nicht »Vorwort« oder »Nachwort«). |
| \>      | Ende eines Wortes      | `wort\>`        | Findet alle Zeilen, welche mit »wort« enden (bspw. »Vorwort« oder »Nachwort«, nicht aber »wort« oder »wortreich«). |
| \<\>    | ein Wort               | `\<wort\>`      | Findet exakt »wort« und nicht »Nachwort« oder »wortreich«.                          |



## Sed
Es ermöglicht die Manipulation von Textdateien durch das Ersetzen, Einfügen und Löschen von Text mit Hilfe von regulären Ausdrücken 2.

**Syntax:**
sed [-option] 'Kommando' [Datei] ... [Datei_n]


Wenn Sie mehrere Dateien auf einmal mit sed bearbeiten wollen bzw. müssen, kann es sinnvoll sein, anstatt eines Kommandos eine Kommandodatei zu verwenden – man darf hierzu gern auch sed-Script sagen. Der Vorteil: Diese Kommandodatei können Sie jederzeit wieder verwenden. Also, statt eine Datei wie folgt mit sed zu bearbeiten

sed -n 'kommando ; kommando; kommando' Datei > Zieldatei
