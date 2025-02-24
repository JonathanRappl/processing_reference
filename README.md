# Grundlagen der Processing-Programmierung

1. [Umgebung](#umgebung) 
   - [Koordinatensystem](#koordinatensystem)  
   - [setup() und draw()](#setup-und-draw)  
   - [Variablen](#variablen)  
   - [Gültigkeitsbereich](#gültigkeitsbereich)  
   - [Farben und Transparenz](#farben-und-transparenz)  

2. [Vordefinierte Funktionen und Variablen](#vordefinierte-funktionen-und-variablen)  
   - [Zeichenfunktionen](#zeichenfunktionen)  
   - [Textfunktionen](#textfunktionen)  
   - [Weitere Funktionen](#weitere-funktionen)  
   - [Vordefinierte Variablen](#variablen)  

3. [Bedingungen](#bedingungen)  
   - [Vergleichsoperatoren](#vergleichsoperatoren)  
   - [Änderungsoperatoren](#änderungsoperatoren)  

4. [Schleifen](#schleifen)  
   - [while](#while)  
   - [for](#for)  

5. [Funktionen definieren und benutzen](#funktionen-definieren-und-benutzen)  
   - [Eigene Funktion mit Rückgabewert](#eigene-funktion-mit-rückgabewert)  
   - [Eigene Funktion ohne Rückgabewert](#eigene-funktion-ohne-rückgabewert)  
   - [Wichtige vordefinierte Funktionen](#wichtige-vordefinierte-funktionen-in-processing)  

6. [Arrays](#arrays)  
   - [Array-Deklaration und Initialisierung](#array-deklaration-und-initialisierung)  
   - [Dynamische Erstellung eines Arrays](#dynamische-erstellung-eines-arrays)  
   - [Array-Länge abrufen](#array-länge-abrufen)  
   - [Durchlaufen eines Arrays](#durchlaufen-eines-arrays-mit-einer-for-schleife)  
   - [Zufälligen Index aus einem Array wählen](#zufälligen-index-aus-einem-array-wählen)  

## Umgebung

### Koordinatensystem
```
(0,0) +---------------> x
      |
      |
      |
      |
      |
      v
      y
```

### setup() und draw()
Processing-Programme bestehen aus zwei wichtigen Funktionen:

**`setup()`**: Wird einmal zu Beginn des Programms aufgerufen. Hier werden die Grundeinstellungen vorgenommen, z. B. die Fenstergrösse.

**`draw()`**: Wird immer wieder ausgeführt.

```java
// Hier können wir Variablen initialisieren oder eigene Funktionen definieren

void setup() {
  // Code der einmal am Anfang ausgeführt werden soll.
}

void draw() {
  // Code der sich immer wiederholen soll.
}
```

### Variablen
Variablen speichern Werte, die später verwendet werden können. Sie werden mit einem Typ, einem Namen und einem optionalen Anfangswert deklariert.
In Processing verwenden wir verschiedene Typen zum speichern von Daten. Hier sind die häufigsten:

```java
int meineZahl = 10;                 // Ganze Zahl (Integer)
float meineKommazahl = 3.14;        // Fliesskommazahl (Dezimalzahlen)
boolean meinWert = false;           // Boolean (wahr/falsch)
char meinBuchstabe = 'A';           // Zeichen
String meinText = "Hallo, Welt!";   // Zeichenkette (String)
```

### Gültigkeitsbereich
Variablen haben einen bestimmten Gültigkeitsbereich:
- Variablen, die innerhalb einer Funktion definiert werden, existieren nur dort.
- Globale Variablen werden ausserhalb von Funktionen definiert und gelten im ganzen Programm.
- Generell ist eine Variable nur innerhalb den geschweiften Klammern `{}` gülti in denen sie definiert wurde.

```java
int globaleVariable = 100;

void setup() {
  int lokaleVariable = 50;
}

void draw() {
  globaleVariable = 50; // OK!
  lokaleVariable = 100; // ERROR!
}

```

### Farben und Transparenz
Farben werden in Processing mit RGB-Werten angegeben (es gibt auch andere Farbschemas aber ich empfehle RGB). Optional kann ein vierter Wert (Alpha) die Transparenz bestimmen.

```java
fill(255, 0, 0);      // Rote Füllfarbe
fill(255, 0, 0, 128); // Halbtransparente rote Füllfarbe
stroke(0, 255, 0);    // Grüne Linienfarbe
```

## Vordefinierte Funktionen und Variablen

### Zeichenfunktionen
```java
size(b, h);  
// Setzt die Grösse des Fensters.
// int b: Die Breite des Fensters in Pixeln.
// int h: Die Höhe des Fensters in Pixeln.

background(f);  
// Setzt die Hintergrundfarbe als Grauwert (0-255).
// int f: Der Grauwert für den Hintergrund.

background(r, g, b);  
// Setzt die Hintergrundfarbe mit RGB-Werten.
// int r, g, b: Die Rot-, Grün- und Blauanteile der Farbe (0-255).

point(x, y);  
// Zeichnet einen Punkt an der angegebenen Position.
// float x: Die X-Koordinate des Punkts.
// float y: Die Y-Koordinate des Punkts.

line(x1, y1, x2, y2);  
// Zeichnet eine Linie von (x1, y1) nach (x2, y2).
// float x1, y1: Startpunkt der Linie.
// float x2, y2: Endpunkt der Linie.

rect(x, y, w, h);  
// Zeichnet ein Rechteck mit der oberen linken Ecke bei (x, y).
// float x, y: Koordinaten der oberen linken Ecke des Rechtecks.
// float w, h: Breite und Höhe des Rechtecks.

ellipse(x, y, w, h);  
// Zeichnet eine Ellipse, zentriert um (x, y).
// float x, y: Mittelpunkt der Ellipse.
// float w, h: Breite und Höhe der Ellipse.

stroke(r, g, b);  
// Setzt die Farbe für Linien und Punkte.
// int r, g, b: Die RGB-Werte (0-255) für die Linienfarbe.

fill(r, g, b);  
// Setzt die Füllfarbe für nachfolgende Formen.
// int r, g, b: Die RGB-Werte (0-255) für die Füllfarbe. 
```
### Textfunktionen  
```java
text(m, x, y);  
// Zeichnet den Text m an der angegebenen Position.  
// String m: Der anzuzeigende Text.  
// int x: Die X-Koordinate der Textposition.  
// int y: Die Y-Koordinate der Textposition.  

textSize(s);  
// Setzt die Schriftgrösse für den Text.  
// int s: Die Grösse der Schrift in Pixeln.  

textAlign(a);  
// Legt die horizontale Ausrichtung des Textes fest.  
// int a: Eine der folgenden Konstanten: LEFT, CENTER oder RIGHT.  

textAlign(a, b);  
// Legt sowohl die horizontale als auch die vertikale Ausrichtung des Textes fest.  
// int a: Horizontale Ausrichtung: LEFT, CENTER oder RIGHT.  
// int b: Vertikale Ausrichtung: TOP, CENTER oder BOTTOM.  
```

Beispiel: 
```java
textSize(32);
textAlign(CENTER, CENTER);
text("Hallo, Welt!", width / 2, height / 2);

// Hier wird der Text "Hallo, Welt!" in der Mitte des Fensters zentriert dargestellt.
```
### Weitere Funktionen
```java
random(min, max);  
// Gibt eine zufällige Zahl zwischen `min` und `max` zurück.
// float min: Der kleinste mögliche Wert.
// float max: Der grösste mögliche Wert.

sin(winkel);  
// Gibt den Sinus des Winkels zurück.
// float winkel: Der Winkel in Radiant.

sqrt(zahl);  
// Gibt die Quadratwurzel der Zahl zurück.
// float zahl: Die Zahl, deren Wurzel berechnet wird.

max(a, b);  
// Gibt das grössere der beiden Argumente zurück.
// float a: Erste Zahl.
// float b: Zweite Zahl.

min(a, b);  
// Gibt das kleinere der beiden Argumente zurück.
// float a: Erste Zahl.
// float b: Zweite Zahl.

constrain(wert, min, max);  
// Begrenzung eines Wertes auf einen bestimmten Bereich.
// float wert: Der zu überprüfende Wert.
// float min: Die untere Grenze.
// float max: Die obere Grenze.

dist(x1, y1, x2, y2);  
// Berechnet die Distanz zwischen zwei Punkten.
// float x1: X-Koordinate des ersten Punktes.  
// float y1: Y-Koordinate des ersten Punktes.  
// float x2: X-Koordinate des zweiten Punktes.  
// float y2: Y-Koordinate des zweiten Punktes.
```
### Variablen

```java
width;              // (int) Breite des Zeichenfensters
height;             // (int) Höhe des Zeichenfensters
mouseX;             // (int) X-Koordinate der Maus
mouseY;             // (int) Y-Koordinate der Maus
keyPressed;         // (boolean) Ob eine Taste gedrückt ist
key                 // (char) Das zuletzt gedrückte Zeichen
mousePressed;       // (boolean) Ob die Maustaste gedrückt ist
mouseButton         // (int) Die zuletzt gedrückte Maustaste 
```

## Bedingungen

Mit `if` und `else` können Bedingungen geprüft werden.

```java
if (bedingung) {
  // Code für wenn bedingung wahr ist.
} else {
  // Code für wenn bedingung falsch ist.
}
```

### Vergleichsoperatoren
- `==` (gleich)
- `!=` (ungleich)
- `>` (grösser als)
- `<` (kleiner als)
- `>=` (grösser gleich)
- `<=` (kleiner gleich)

### Änderungsoperatoren

- `x += 1;` (erhöht `x` um 1)
- `x -= 1;` (verringert `x` um 1)
- `x *= 2;` (multipliziert `x` mit 2)
- `x /= 2;` (teilt `x` durch 2)

## Schleifen

### `while`

Die `while`-Schleife wiederholt Anweisungen, solange die Bedingung erfüllt ist.  
Sie überprüft die Bedingung vor jeder Iteration. Falls die Bedingung `false` ist, wird die Schleife beendet.  

```java
int zahl = 0;
while (zahl < 5) {
  println("Zahl ist: " + zahl);
  zahl++;  // Zahl wird in jeder Iteration erhöht
}

// Die Schleife beginnt mit zahl = 0 und wiederholt sich, solange zahl < 5 ist.
// In jeder Iteration wird zahl um 1 erhöht.
// Sobald zahl den Wert 5 erreicht, wird die Bedingung false und die Schleife stoppt.
```
Die `while`-Schleife kann auch für andere Bedingungen verwendet werden, z. B.:
```java
while (!mousePressed) {
  println("Warte auf Mausdruck ...");
}

// Hier läuft die Schleife, bis mousePressed true ist.
```
**Achtung**: Es muss sichergestellt werden, dass die Bedingung irgendwann `false` wird,
sonst entsteht eine Endlosschleife.
```java
while (true) {
  println("Diese Schleife läuft unendlich!");
}

// Diese Schleife würde niemals enden, da die Bedingung immer true bleibt.
// Um eine Endlosschleife zu vermeiden, sollte sich der Zustand in der Schleife verändern.
```

### `for`

Als Alternative zur `while`-Schleife gibt es auch die `for`-Schleife. 
Sie besteht aus drei Teilen:  

```java
for (Initialisierung; Bedingung; Aktualisierung) {
  // Anweisungen, die in jeder Iteration ausgeführt werden
}
```
- **Initialisierung**: Wird vor dem ersten Durchlauf ausgeführt (z. B. die Zählvariable setzen).
- **Bedingung**: Wird vor jeder Iteration geprüft. Ist sie true, wird der Schleifenblock ausgeführt. Ist sie `false`, ende die Schleife.
- **Aktualisierung**: Wird nach jedem Durchlauf ausgeführt (z. B. Erhöhung der Zählvariablen).

Jede `for`-Schleife kann in eine `while`-Schleife umgeschrieben werden:

```java
// Initialisierung
while (Bedingung) {
  // Anweisungen, die in jeder Iteration ausgeführt werden
  // Aktualisierung
}
```

Beispiel einer klassischen `for`-Schleife:
```java
for (int i = 0; i < 5; i++) {
  println("Durchlauf: " + i);
}

// Die Schleife startet mit i = 0 und läuft, solange i < 5 ist.
// Nach jedem Durchlauf wird i um 1 erhöht.
```
Die `for`-Schleife kann auch für andere Anwendungen genutzt werden:
```java
for (float winkel = 0; winkel < TWO_PI; winkel += 0.1) {
  float wert = sin(winkel);
  println("Sinus von " + winkel + " ist " + wert);
}

// Hier wird winkel von 0 bis TWO_PI (2*PI) in Schritten von 0.1 erhöht
// und der Sinuswert für jeden Winkel berechnet.
```


**Achtung**: Es muss darauf geachtet werden, dass die Schleifenvariable korrekt aktualisiert wird,
sonst kann eine Endlosschleife entstehen.
```java
for (int i = 0; i <= 10; i--) { 
  println("Diese Schleife läuft unendlich!");
}

// Hier wird i immer kleiner, bleibt desegen immer <= 10, sodass die Schleife nie endet.
```

## Funktionen definieren und benutzen

Eigene Funktionen ermöglichen wiederverwendbaren Code.  
Eine Funktion kann Parameter entgegennehmen und einen Wert zurückgeben.  

### Eigene Funktion mit Rückgabewert  

```java
int addiere(int a, int b) {
  return a + b;
}

// Diese Funktion nimmt zwei ganze Zahlen (int a und int b) entgegen
// und gibt die Summe der beiden Zahlen zurück.
```
Die Funktion kann dann so aufgerufen werden:
```java
int ergebnis = addiere(3, 5);
println("Ergebnis: " + ergebnis);

// Hier wird addiere(3, 5) ausgeführt und das Ergebnis 8 in ergebnis gespeichert.
```
### Eigene Funktion ohne Rückgabewert

Eine Funktion kann auch `void` sein, wenn sie keinen Wert zurückgibt.
```java
void begruessen(String name) {
  println("Hallo, " + name + "!");
}

// Diese Funktion gibt eine Begrüssung aus, abhängig vom Parameter name.
```
Aufruf der Funktion:
```java
begruessen("Alice");

// Gibt "Hallo, Alice!" auf der Konsole aus.
```
### Wichtige vordefinierte Funktionen in Processing

Processing stellt einige Funktionen bereit, die automatisch aufgerufen werden, wenn bestimmte Ereignisse eintreten. Wir müssen nur noch definieren was dann passieren soll.
#### mousePressed()

Wird aufgerufen, wenn die Maustaste gedrückt wird. 
```java
void mousePressed() {
  println("Maus wurde gedrückt!");
}

// Diese Funktion wird bei jedem Mausklick ausgeführt.
```
#### keyPressed()

Wird aufgerufen, wenn eine Taste gedrückt wird.
```java
void keyPressed() {
  println("Taste: " + key);
}

// Diese Funktion gibt die gedrückte Taste aus, gespeichert in der vordefinierten Variable key.
```

## Arrays  

Ein Array speichert mehrere Werte des gleichen Typs in einer geordneten Liste.  
Auf die Werte kann über Indizes zugegriffen werden, wobei der erste Index `0` ist.  

### Array-Deklaration und Initialisierung  

Ein Array kann direkt mit Werten gefüllt werden:  

```java
int[] zahlen = {1, 2, 3, 4, 5};
println(zahlen[0]); // Gibt 1 aus
println(zahlen[3]); // Gibt 4 aus

// Hier wird ein int-Array mit fünf Werten erstellt.
// zahlen[0] greift auf das erste Element (1) zu, zahlen[3] auf das vierte Element (4).
```
### Dynamische Erstellung eines Arrays

Ein Array kann auch ohne direkte Werte erstellt werden. Dabei wird nur die Grösse festgelegt:
```java
int[] zahlen = new int[5]; // Erstellt ein Array mit 5 Plätzen (Standardwert: 0)
zahlen[0] = 10;
zahlen[1] = 20;
println(zahlen[0]); // Gibt 10 aus
println(zahlen[1]); // Gibt 20 aus
println(zahlen[4]); // Gibt 0 aus (Standardwert)

// Arrays mit new werden mit Standardwerten gefüllt (0 für int, false für boolean).
```
### Array-Länge abrufen

Die Länge eines Arrays kann mit `.length` ermittelt werden:
```java
println("Das Array hat " + zahlen.length + " Elemente.");

// Gibt "Das Array hat 5 Elemente." aus, da zahlen.length den Wert 5 hat.
```
### Durchlaufen eines Arrays mit einer for-Schleife

Um alle Elemente eines Arrays auszugeben, kann eine `for`-Schleife verwendet werden:
```java
for (int i = 0; i < zahlen.length; i++) {
  println("Element " + i + ": " + zahlen[i]);
}

// Hier wird das Array von 0 bis zahlen.length - 1 durchlaufen und alle Werte ausgegeben.
```
### Zufälligen Index aus einem Array wählen

Ein zufälliges Element kann aus einem Array ausgewählt werden, indem ein zufälliger Index erzeugt wird:

```java
int zufallsIndex = int(random(zahlen.length));
int zufallsWert = zahlen[zufallsIndex];
println("Zufällig gewähltes Element: " + zufallsWert);

// `random(zahlen.length)` gibt eine Zufallszahl zwischen `0` und `zahlen.length - 1` zurück.  
// `int(random(...))` wandelt den Wert in eine ganze Zahl um.  
// Der zufällige Index wird verwendet, um ein Element aus dem Array auszuwählen.
```


## Benutzerdefinierte Klassen

### Warum Klassen?
Klassen sind eine Möglichkeit, eigene Datentypen zu erstellen. Sie ermöglichen es, Daten und zugehörige Funktionen (Methoden) zusammenzufassen.  
Statt mehrere Variablen zu verwalten, kann man ein Objekt erstellen, das alle benötigten Werte speichert.

### Eine einfache Klasse definieren

Eine Klasse wird mit dem `class`-Schlüsselwort definiert.  
Innerhalb der Klasse werden Variablen und eine `constructor`-Methode (`setup`-ähnlich) verwendet.

```java
class Ball {
  // Variablen der Klasse (Attribute):
  float x, y;     // Position
  float vx, vy;   // Geschwindigkeit

  // constructor-Methode, Sie muss den gleichen Namen haben wie die Klasse selbst.
  Ball(float startX, float startY) {
    x = startX;
    y = startY;
    vx = random(-2, 2);
    vy = random(-2, 2);
  }

  // Zwei Funktionen der Klasse (Methoden) um mit der Klasse zu interagieren.
  void move() {
    x += vx;
    y += vy;
  }

  void display() {
    ellipse(x, y, 20, 20);
  }
}
```

### Methoden in Klassen

Methoden sind Funktionen innerhalb einer Klasse, die für das Objekt arbeiten.  
Die Methoden `move()` und `display()` im obigen Beispiel lassen den Ball sich bewegen und zeichnen ihn.

### Mehrere Objekte erstellen

Mit einer Klasse können beliebig viele Objekte erzeugt werden.

```java
Ball ball1;
Ball ball2;

void setup() {
  size(400, 400);
  ball1 = new Ball(100, 100);
  ball2 = new Ball(200, 200);
}

void draw() {
  background(220);
  
  ball1.move();
  ball1.display();
  
  ball2.move();
  ball2.display();
}
```

Hier werden zwei Objekte der Klasse `Ball` erstellt, die sich unabhängig voneinander bewegen.


### Ein Array von Objekten erstellen

Anstatt einzelne Ball-Objekte zu verwalten, können wir ein Array von Bällen erstellen:

```java
Ball[] balls = new Ball[10];

void setup() {
  size(400, 400);
  for (int i = 0; i < balls.length; i++) {
    balls[i] = new Ball(random(width), random(height));
  }
}

void draw() {
  background(220);
  for (int i = 0; i < balls.length; i++) {
    balls[i].move();
    balls[i].display();
  }
}
```

Hier erstellen wir ein Array mit 10 Ball-Objekten, die zufällig positioniert werden. Jeder Ball bewegt sich unabhängig und wird in der `draw()`-Methode aktualisiert und gezeichnet.
