# Grundlagen der Processing-Programmierung

## 1. Datentypen und Variablen
Variablen speichern Werte, die später verwendet werden können. Sie werden mit einem Typ, einem Namen und einem optionalen Anfangswert deklariert.
In Processing verwenden wir verschiedene Typen zum speichern von Daten. Hier sind die häufigsten:

```java
int meineZahl = 10;                 // Ganze Zahl (Integer)
float meineKommazahl = 3.14;        // Fließkommazahl (Dezimalzahlen)
boolean meinWert = true;            // Boolean (wahr/falsch)
char meinBuchstabe = 'A';           // Zeichen
String meinText = "Hallo, Welt!";   // Zeichenkette (String)
```

### Vordefinierte Variablen in Processing
Processing stellt einige vordefinierte Variablen zur Verfügung, die oft verwendet werden:

```java
int width;              // Breite des Zeichenfensters
int height;             // Höhe des Zeichenfensters
int mouseX;             // X-Koordinate der Maus
int mouseY;             // Y-Koordinate der Maus
int pmouseX;            // Vorherige X-Koordinate der Maus
int pmouseY;            // Vorherige Y-Koordinate der Maus
boolean mousePressed;   // Ob die Maustaste gedrückt ist
boolean keyPressed;     // Ob eine Taste gedrückt ist
```

## 2. Zeichenfunktionen
Processing bietet viele Funktionen zur Manipulation der Zeichenfläche und zum Zeichnen von Formen:

### Zeichenfläche einrichten
```java
size(500, 500);     // Setzt die Breite und Höhe der Zeichenfläche
background(255);    // Setzt die Hintergrundfarbe (weiss in diesem Fall,
                    // 0 wäre schwarz)
```

### Grundlegende Formen
```java
point(100, 100);            // Zeichnet einen Punkt bei (100,100)
line(50, 50, 150, 150);     // Zeichnet eine Linie von (50,50) nach (150,150)
ellipse(200, 200, 80, 80);  // Zeichnet einen Kreis mit Mittelpunkt (200,200) und Breite/Höhe von 80
rect(300, 300, 100, 50);    // Zeichnet ein Rechteck bei (300,300) mit Breite 100 und Höhe 50
```

### Farben
```java
fill(255, 0, 0); // Setzt die Füllfarbe auf Rot
stroke(0);       // Setzt die Linienfarbe auf Schwarz
strokeWeight(3); // Setzt die Liniendicke
```

## 3. Die `setup()`- und `draw()`-Struktur
Processing-Programme bestehen aus zwei Hauptfunktionen:

```java
void setup() {      // Wird einmal zu Beginn ausgeführt
  size(500, 500);
  background(220);
}

void draw() {
  ellipse(mouseX, mouseY, 50, 50); // Zeichnet kontinuierlich einen Kreis an der Mausposition
}
```
- `setup()`: Wird einmal zu Beginn des Programms ausgeführt.
- `draw()`: Wird kontinuierlich ausgeführt, um die Zeichenfläche zu aktualisieren.

## 5. Schleifen
Schleifen ermöglichen es, Code mehrfach auszuführen, solange eine Bedingung erfüllt ist.

### `while`-Schleife
Die `while`-Schleife führt den Codeblock aus, solange die Bedingung `true` ist.
```java
int i = 0;
while (i < 5) {
  println("Iteration: " + i);
  i++; // Erhöht i um 1
}
```
Ablauf:
1. Die Bedingung `(i < 5)` wird geprüft.
2. Falls `true`, wird der Codeblock ausgeführt.
3. Die Variable `i` wird um 1 erhöht.
4. Der Prozess wiederholt sich, bis die Bedingung `false` wird.


### `for`-Schleife
Die `for`-Schleife ist eine kompakte Möglichkeit, eine Schleife mit einer Start-, Abbruch- und Änderungsbedingung zu schreiben.
```java
for (int i = 0; i < 5; i++) {
  println("Iteration: " + i);
}
```
Aufbau:
1. `int i = 0;` → Initialisierung (läuft nur einmal zu Beginn)
2. `i < 5;` → Bedingung (Schleife läuft solange `true`)
3. `i++` → Inkrement (wird nach jedem Durchlauf ausgeführt)


## 6. Arrays
Arrays speichern mehrere Werte des gleichen Typs.

```java
int[] zahlen = {10, 20, 30, 40};
println(zahlen[0]); // Ausgabe: 10

for (int i = 0; i < zahlen.length; i++) {
  println(zahlen[i]);
}
```

Dies gibt aus:
```
10
20
30
40
```

Man kann auch ein leeres Array erstellen und später Werte hinzufügen:
```java
int[] werte = new int[5];
werte[0] = 100;
werte[1] = 200;
```