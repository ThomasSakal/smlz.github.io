class: center, middle
# Scripting 1

TSBE Frühlingssemester 2016  
`http://smlz.github.io/tsbe-2016fs/scri/`  

Marco Schmalz  
`marco.schmalz@gibb.ch`  
  
.footnote.bottom[<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="/assets/cc88x31.png" /></a>]
---
# Kursübersicht

1. **Bash und UNIX-Tools**

2. Einführung in Python

3. Python: Datei und Prozessoperationen

4. (Auffahrt)

5. Repetition

---
# Heute

1. Administratives

2. Gruppenarbeit zu Bash

3. Übung Bash

4. Einführung in Python

---

# Gruppenpuzzle (30')

* If und test ([)

* while loop

* find

* for loops

* sed/grep/cut

---
# Einstiegsübung (5')

Schreiben sie ein Skript, welches den Benutzer nach dem Jahrgang fragt, diesen in einer Variabel abspeichert, und danach das Alter ausgibt.

Tipps:
* 
```bash
read name
```
   speichert die Benutzereingabe unter `name` ab.
* 
```bash
man echo
``` 
Gibt Auskunft, wie man Zeilenumbrüche bei der Ausgabe verhindern kann.
---
# Verzweigung - IF

```bash
if [ "$a" -gt 0 ]
then
  if [ "$a" -lt 5 ]
  then
    echo "Der Wert von \"a\" liegt zwischen 0 und 5."
  fi
fi
```


Gleiches Resultat mit 
```bash
if [ "$a" -gt 0 ] && [ "$a" -lt 5 ]
then
  echo "Der Wert von \"a\" liegt zwischen 0 und 5."
fi
```
---

# Werte testen mit [

**Achtung:** `[ ` ist ein Programm. Darum muss immer ein Leerschlag nach `[ ` folgen.

Siehe auch:  
```bash
man [
```

**Achtung**: 

* `[` ist ein Programm!
* Ebenso wie `true` und `false`
---
# Strings vergleichen:
```bash
if [ "$a" = "$b" ]
then
  echo "a und b sind gleich"
fi
```
* `=` : Gleich
* `!=` : Ungleich
* `[ -n "$a" ]` : `$a` ist **nicht** ein leerer String
* `[ -z "$a" ]` : `$a` **ist** ein leerer String
---
# Zahlen vergleichen:

```bash
if [ "$a" -gt "$b" ]
then
  echo "a ist grösser als b"
elif [ "$a" -eq "$b" ]
then
  echo "a ist gleich gross wie b"
else
  echo "a ist kleiner als b"
fi
```

* `-eq` (equal): Gleich
* `-ne` (not equal): Ungleich
* `-gt` (greater than): Grösser
* `-ge` (greater or equal): Grösser oder gleich
* `-lt` (lesser than): Kleiner
* `-le` (lesser or equal): Kleiner oder gleich
---
# Tests mit Dateien

```bash
if [ -e "$file" ]
then
  echo "Datei $file existiert"
fi
```

* `-e` (exists): Datei existiert
* `-f` (file exists): Datei existiert und ist eine normale Datei
* `-d` (directory exists): Datei existiert und ist ein Verzeichnis
* `-w` (writable): Datei existiert darf geschrieben werden
* `-x` (eXecute): Datei existiert und darf ausgeführt werden
---
class: smaller
# Übung (15')

Erweitern sie ihr Script von vorher:
* Entscheiden sie anhand des Jahrgangs ob der Benutzer volljährig ist
* Falls ja:
  * Überpüfen sie ob eine ausführbare Datei mit dem Namen `autofahren` existiert.
  * Erstellen sie die Datei automatisch, fall sie nicht existiert.
  * Machen sie falls nötig die Datei ausführbar.
  * Führen sie die Datei `autofahren` aus.
  * `autofahren` soll "WROOOM" auf dem Bildschirm ausgeben
* Falls nein:
  * Überpüfen sie ob eine ausführbare Datei mit dem Namen `velofahren` existiert.
  * Erstellen sie die Datei automatisch, fall sie nicht existiert.
  * Machen sie falls nötig die Datei ausführbar.
  * Führen sie die Datei `velofahren` aus.
  * `velofahren` soll "KLAPPERKLAPPER" auf dem Bildschirm ausgeben

---
# Schleifen - for

Beispiel:
```bash
for file in *.JPEG
do
  echo mv "$file" "${file/.JPEG/.jpg}"
done
```

* Dateinamen-Komplementierung mit * (Stern)

---
# Übung

Verschieben sie alle PNG-Bilder im aktuellen Verzeichnis in ein Unterverzeichnis mit den Name `bilder`.

---
# Schleifen - while

Beispiel:
```bash
while true
do
  echo "Endlosschleife"
done
```
* Bedinung gleich wie bei **if**

---
#  Übung

Geben sie mit einem Skript die endlose Fibonacci-Reihe aus:

* 1
* 1
* 2
* 3 
* 5
* 8
* 13
* 21
* ...
