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
von Software.

### UML Einheiten
UML besteht u.a. aus den Spracheinheiten...  
<ul>
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
<ul>
<li>public (+): auch andere Klassen können darauf zugreifen</li>
<li>private (-): nur die Klasse selbst kann darauf zugreifen</li>
</ul>

### Methoden in UML (Vereinfacht)
Notation:  
[Sichtbarkeit] name [({Parameter})] [:Rückgabetyp]  
Notation von Parametern:  
name : Typ

### Konstruktoren
Um ein Objekt einer Klasse zu erstellen, muss der Konstruktor mit dem Schlüsselwort new aufgerufen werden:  

    Schueler peter = new Schueler();

Ein Konstruktor ähnelt einer Methode und wird in der UML bei den Methoden gelistet, wird aber in Java groß geschrieben und hat keinen Rückgabetyp (auch nicht void):  

    public class Schueler{
      public Schueler(){
      }
    }

### Konstruktoren 
Ein Konstruktor kann verwendet werden, um Attribute eines Objektes bei seiner Erstellung festzulegen:  

    public class Schueler{
      private String name;
      private double groesse;
      private double gewicht;
      public Schueler(String name, double groesse, double gewicht){
        this.name = name;
        this.groesse = groesse;
        this.gewicht = gewicht;
      }
    }

Mit "this" wird auf die Variablen des aktuellen Objektes zugegriffen.

### Unterschied public und private
Öffentliche Attribute können zu Fehlern im System führen:  

    public class Schueler{
      public double groesse;
      public double gewicht;
      public double bmi;
      public double bmiBerechnen(){
        return this.gewicht/(this.groesse*this.groesse);
      }
    }
    public class Anwendung{
      public static void main(args...){
        Schueler peter = new Schueler();
        peter.groesse = 1.80;
        peter.gewicht = 70;
        peter.bmi = peter.bmiBerechnen();
        peter.gewicht = 75;
        System.out.println(peter.bmi); //falscher Wert, denn nicht mehr aktuell!
        System.out.println(peter.bmiBerechnen()); //richtiger Wert
      }
    }
    
### get- und set-Methoden
Um die Problematik von öffentlichen Attributen zu umgehen, können get- und set-Methoden verwendet werden:  

    public class Schueler{
      private double groesse;
      private double gewicht;
      private double bmi;
      public Schueler(double groesse, double gewicht){
        this.groesse = groesse;
        this.gewicht = gewicht;
        this.bmi = bmiBerechnen();
      }
      public double bmiBerechnen(){
        return this.gewicht/(this.groesse*this.groesse);
      }
      public double getGroesse(){
        return this.groesse;
      }
      public void setGroesse(double groesse){
        this.groesse = groesse;
        this.bmi = bmiBerechnen();
      }
      public double getGewicht(){
        return this.gewicht;
      }
      public void setGewicht(){
        this.gewicht = gewicht;
        this.bmi = bmiBerechnen;
      }
      public double getBmi(){
        return this.bmi;
      }
    }

### Beispiel: Klasse Buch
Modelliere die Klasse "Buch" in einem vollständigen UML-Klassendiagramm. Mit den folgenden Attributen, ihren get- und set-Methoden sowie einem Konstruktor:  

- Einen Author
- Einen Titel
- Eine ISBN
- Ein Erscheinungsjahr

### Methoden und Konstruktoren überladen
Methoden und Konstruktoren können überladen werden. D.h. es können mehrere Methoden und Konstruktoren mit dem gleichen Namen, aber unterschiedlichen Parametern existieren:  

    public class Schueler{
      private double gewicht;
      private double groesse;
      private double bmi;
      public Schueler(){}
      public Schueler(double gewicht, double groesse){
        this.gewicht = gewicht;
        this.groesse = groesse;
        this.bmi = bmiBerechnen();
      }
      public double bmiBerechnen(){
        return this.gewicht/(this.groesse*this.groesse);
      }
    }
    
### Aufgabe: Klasse Auto
1. Modelliere die Klasse "Auto" in einem vollständigen UML-Klassendiagramm. Mit den folgenden Attributen, ihren get- und set-Methoden, vier Konstruktoren und den Methoden tanken(double Menge) und fahren(double Strecke):  

- Kennzeichen
- Kilometerstand
- Tankvolumen
- Verbrauch
- Tankinhalt

2. Implementiere die Klasse Auto abgesehen von der Methode fahren.
