# Grundlagen der Processing-Programmierung

## 1. Datentypen und Variablen
Variablen speichern Werte, die später verwendet werden können. Sie werden mit einem Typ, einem Namen und einem optionalen Anfangswert deklariert.
In Processing verwenden wir verschiedene Typen zum speichern von Daten. Hier sind die häufigsten:

```java
int meineZahl = 10;                 // Ganze Zahl (Integer)
float meineKommazahl = 3.14;        // Fließkommazahl (Dezimalzahlen)
boolean meinWert = false;            // Boolean (wahr/falsch)
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
boolean mousePressed;   // Ob die Maustaste gedrückt ist
boolean keyPressed;     // Ob eine Taste gedrückt ist

// auch praktisch:
random(x)               // 0-x
random(x, y)            // x-y
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
Arrays speichern mehrere Werte des gleichen Typs und ermöglichen deren gezielte Nutzung über Indizes.

### Deklaration und Initialisierung
```java
int[] zahlen = {10, 20, 30, 40}; // Ein Array mit 4 Werten
println(zahlen[0]); // Gibt den ersten Wert aus: 10
```

### Zugriff über Indizes
Jedes Element in einem Array kann über seinen Index angesprochen werden. Die Indizes beginnen bei 0.
```java
int[] werte = {5, 10, 15, 20};
println(werte[0]); // Zugriff auf das erste Element: 5
println(werte[1]); // Zugriff auf das zweite Element: 10
```

### Array mit einer bestimmten Größe erstellen
```java
int[] daten = new int[5]; // Erstellt ein Array mit 5 Elementen
```

### Array-Werte mit einer Schleife durchlaufen
```java
int[] zahlen = {2, 4, 6, 8, 10};
for (int i = 0; i < zahlen.length; i++) {
  println("Index " + i + ": " + zahlen[i]);
}
```
Dies gibt aus:
```
Index 0: 2
Index 1: 4
Index 2: 6
Index 3: 8
Index 4: 10
```

### Werte im Array ändern
```java
int[] liste = {1, 2, 3, 4};
liste[2] = 99; // Ändert das dritte Element (Index 2) auf 99
println(liste[2]); // Gibt 99 aus
```