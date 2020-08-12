% Objektorientierung

---
revealjs-url: ../../reveal.js
theme: white
width: \"95%\"
height: \"95%\"
header-includes:
    <style>
    .beispiel {
      border:3px;
      border-style:solid;
      border-color:black;
      width:fit-content;
      margin:auto;
    }
    .wichtig {
      border:3px;
      border-style:solid;
      border-color:red;
      width:fit-content;
      margin:auto;
    }
    </style>
...

### Objektorientierung
- Objektorientierung nennt man die Sichtweise auf komplexe Systeme als Zusammenspiel kooperierender Objekte.
- Die Idee der Objektorientierung stammt aus der realen Welt.  
Vorteile sind:
- Wiederverwendbarkeit
- Übersichtlichkeit

### Objekte
- Ein Objekt hat Attribute (Eigenschaften) und Methoden (Prozeduren oder Funktionen).
- Attribute (Eigenschaften) sind Daten in Form von Variablen, die einem Objekt zugeordnet sind.
- Methoden sind Unterprogramme in Form von Prozeduren und Funktionen, die das Verhalten von Objekten - insbesondere zur Datenverarbeitung und Kooperation mit anderen Objekten - beschreibt.

### Klassen
- Eine Klasse ist eine zusammenfassende Beschreibung gleichartiger Objekte.

### Unified Modeling Language (UML)
UML ist eine grafische Modellierungssprache zur...
<ul style="text-align:left; align-items:left">
<li>Spezifikation</li>
<li>Konstruktion</li>
<li>Dokumentation und</li>
<li>Visualisierung</li>
</ul>
<span style="text-align:left">von Software.</span>

### UML Einheiten
UML besteht u.a. aus den Spracheinheiten...
<ul style="align-items:left">
<li>Aktionen</li>
<li>Aktivitäten</li>
<li>Anwendungsfälle</li>
<li>Interaktionen</li>
<li>Klassen</li>
<li>Profile</li>
<li>Verteilungen</li>
<li>Zustandsautomaten</li>
</ul>

### UML Klassendiagramme
- Klassendiagramme dienen der Modellierung von Klassen, Schnittstellen und deren Beziehung zueinander.
- Aus Klassendiagrammen kann Quellcode generiert werden.

### UML Klassen (Vereinfacht)
- Klassen werden durch Rechtecke dargestellt.
- Das Rechteck enthält mittig den Klassennamen fett gedruckt als Überschrift.
- Attribute können nach einer horizontalen Linie linksbündig folgen.
- Methoden können nach einer weiteren horizontalen Linie linksbündig folgen.

### Attribute in UML (Vereinfacht)
Notation:  
[Sichtbarkeit] name [:Typ]  
Sichtbarkeiten können u.a. sein:
<ul style="text-align:left">
<li>public (+): auch andere Klassen können darauf zugreifen</li>
<li>private (-): nur die Klasse selbst kann darauf zugreifen</li>
</ul>

### Methoden in UML (Vereinfacht)
Notation:  
[Sichtbarkeit] name [({Parameter})] [:Rückgabetyp]  
Notation von Parametern:  
name : Typ
