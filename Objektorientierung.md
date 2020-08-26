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
1. Modelliere die Klasse "Auto" in einem vollständigen UML-Klassendiagramm. Mit den folgenden Attributen, ihren get- und set-Methoden, vier Konstruktoren und den Methoden tanken(double menge) und fahren(double strecke):  

- Kennzeichen
- Kilometerstand
- Tankvolumen
- Verbrauch
- Tankinhalt

2. Implementiere die Klasse Auto abgesehen von der Methode fahren.

### Aufgabe: Fahren Methode
Analysiere und beschreibe die Methode fahren:

    public void fahren(double strecke) {
        double verbrauchFuerStrecke = (strecke * this.verbrauch) / 100;
        if (verbrauchFuerStrecke > this.tankinhalt) {
        strecke = this.tankinhalt / this.verbrauch * 100;
        this.kilometerstand = this.kilometerstand + strecke;
        Tankinhalt = 0;
      } else {
        this.kilometerstand = this.kilometerstand + strecke;
        this.tankinhalt = this.tankinhalt - verbrauchFuerStrecke;
      }
    } 
    
### Aufgabe: Fahrschule
<font size="5">

- Implementiere die beiden auf der nächsten Folie folgenden Klassen Fahrschueler und Auto.
- Bei Erstellung eines neuen Fahrschülers über den Konstruktor hat dieser noch keine Theorie- und Praxisstunden abgelegt und somit auch noch keine der beiden Prüfungen bestanden. Außerdem sitzt er in keinem Auto.
- Die Methoden machePraxisstunde und macheTheoriestunde erhöhen das jeweilige Attribut jeweils um 1.
- Die Methoden theorieBestanden und praxisBestanden setzen das jeweilige Attribut jeweils auf true, wenn in dem jeweiligen Bereich mindestens 14 Stunden erreicht wurden.
- Die Methode hatFuehrerschein gibt genau dann true zurück, wenn Theorie und Praxis bestanden wurden.
- Die Methode einsteigen ändert das Attribut auto zum übergebenen Auto.
- Die Methode losfahren gibt true zurück, wenn das Attribut auto ein Fahrschulauto ist oder er bereits seinen Führerschein hat.
- Die Methode aussteigen setzt das Attribut auto auf "null", d.h. der Wert ist leer.

</font>

### Aufgabe: Fahrschule
<img src=".\Abbildungen\Klassen.png" style="max-width:45%">

### Vererbung
- In Java können Klassen Attribute und Methoden vererben
- Die vererbende Klasse wird Superklasse genannt
- Die erbende Klasse wird Subklasse genannt
- Vererbung dient der Wiederverwendbarkeit

### Generalisierung und Spezialisierung
Bei der Vererbung spricht man auch von Generalisierung und Spezialisierung.  
Beispiel: Tier ist eine Superklasse von der Subklasse Hund.  
Vom Tier zum Hund spricht man von Spezialisierung.  
Vom Hund zum Tier spricht man von Generalisierung.

### Vererbung in UML
- In UML wird die Vererbung durch einen Pfeil von der Subklasse zur Superklasse dargestellt
- Geerbte Attribute und Methoden müssen nicht nochmal enthalten sein

### Vererbung in Java
In Java wird die Vererbung durch das Schlüsselwort extends verursacht:

    public class Superklasse {
      ...
    }
    public class Subklasse extends Superklasse{
      ...
    }
    
### Sichtbarkeit protected
- Ist die Sichtbarkeit eines Attributes private, kann sie auch keine Subklasse erreichen
- Soll ein Attribut der Superklasse im Allgemeinen privat sein, aber für eine Subklasse erreichbar, muss das Schlüsselwort protected statt private verwendet werden

### Beispiel Vererbung

    public class Fahrzeug{
      private String marke;
      public void hupen(){
        System.out.println("Tuut tuut!");
      }
      public String getMarke(){
        return this.marke;
      }
      public void setMarke(String marke){
        this.marke = marke;
      }
    }
    
    public class Auto extends Fahrzeug{
      private String modell;
      public String getModell(){
        return this.Modell;
      }
      public void setModell(String modell){
        this.modell = modell;
      }
    }
    
    public class MainClass{
      public static void main(String... args){
        Auto meinAuto = new Auto();
        meinAuto.setMarke("Ford");
        meinAuto.setModell("Mustang");
        meinAuto.hupen();
        System.out.println("Mein Auto ist ein "+meinAuto.getMarke()+" "+meinAuto.getModell()+".");
        meinAuto.hupen();
      }
    }

### Beispiel Schlüsselwort protected

    public class Fahrzeug{
      protected String marke;  //hier protected, damit marke von Subklassen verändert werden kann
      public void hupen(){
        System.out.println("Tuut tuut!");
      }
    }
    
    public class Auto extends Fahrzeug{
      private String modell;
      public String getModell(){
        return this.Modell;
      }
      public void setModell(String modell){
        this.modell = modell;
      }
      public String getMarke(){  //hier nur möglich, weil marke in der Superklasse protected statt private ist
        return this.marke;
      }
      public void setMarke(String marke){  //hier nur möglich, weil marke in der Superklasse protected statt private ist
        this.marke = marke;
      }
    }
    
### Polymorphie
<font size="6">Polymorphie bedeutet, dass die gleiche Methode durch Vererbung und Überschreibung der Methoden unterschiedliche Auswirkungen hat:</font>  

    public class Tier{
      public void tierLaut(){
        System.out.println("Das Tier macht einen Laut.");
      }
    }
    public class Hund extends Tier{
      public void tierLaut(){
        System.out.println("Wuff wuff!");
      }
    }
    public class Katze extends Tier{
      public void tierLaut(){
        System.out.println("Miau miau!");
      }
    }

### Aufgabe Vererbung in UML und Java
<font size="6">

- Modelliere die Klassen Schueler, Grundschueler, Unterstufenschueler, Mittelstufenschueler und Oberstufenschueler in UML.
- Implementiere die Klassen in Java.
- Schueler ist die Superklasse der anderen Klassen.
- Jeder Schueler hat einen Namen und eine Methode print, die alle Daten des Schülers in der Konsole ausgibt.
- Grundschueler haben eine AG (String).
- Unterstufenschueler haben eine zweite Fremdsprache (String).
- Mittelstufenschueler haben eine zweite Fremdsprache (String) und zwei Wahlpflichtfächer (jeweils ein String).
- Oberstufenschueler haben zwei Leistungskurse (jeweils ein String) und mehrere Grundkurse (String[]).

</font>

### Abstrakte Klassen und Interfaces
Sollen Superklassen nur gemeinsame Eigenschaften von mehreren Subklassen bündeln, können abstrakte Klassen und Interfaces verwendet werden.  
Abstrakte Methoden in abstrakten Klassen werden nur deklariert, aber nicht implementiert.  
Abstrakte Klassen können aber auch implementierte Klassen enthalten.  
Interfaces enthalten nur abstrakte Methoden.
Abstrakte Klassen und Interfaces können nicht instanziiert werden, sondern nur von Subklassen erweitert und implementiert werden.
Subklassen können mehrere Interfaces implementieren.

### Abstrakte Klassen
In UML werden abstrakte Klassen und Methoden kursiv geschrieben.  
In Java wird das Schlüsselwort abstract verwendet:  

    public abstract class AbstrakteSuperklasse{
      public abstract String abstrakteMethode(){
        return "Hallo";
      }
    }

Sie werden wie gewohnt durch das Schlüsselwort extends von einer Subklasse erweitert.
