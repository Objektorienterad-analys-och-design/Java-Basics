# Java för JavaScript-utvecklare - Villkorssatser

## Introduktion till villkorssatser i Java

Villkorssatser (conditionals) är grundläggande komponenter i programmeringsspråk som låter oss kontrollera programflödet baserat på olika förutsättningar. För JavaScript-utvecklare är många koncept bekanta, men Java har vissa skillnader i syntax och regler som är viktiga att förstå.

## Boolska värden i Java

I Java är datatypen för sant/falskt-värden `boolean`, som kan ha värdena `true` eller `false`.

```java
boolean sann = true;
boolean falsk = false;
```

**Viktig skillnad från JavaScript:** I Java kan endast boolska värden användas i villkor. JavaScript tillåter typkonvertering där värden som 0, "", null, undefined automatiskt konverteras till false. I Java måste du explicit jämföra med sådana värden.

```java
// JavaScript (fungerar)
let x = 0;
if (x) {  // x konverteras automatiskt till false
    console.log("Detta körs inte");
}

// Java (kompileringsfel!)
int x = 0;
if (x) {  // Kompileringsfel: incompatible types: int cannot be converted to boolean
    System.out.println("Detta kompilerar inte");
}

// Korrekt Java-kod
int x = 0;
if (x != 0) {
    System.out.println("Detta körs inte");
}
```

## If-satser

### Grundläggande If-satser

Syntaxen för if-satser i Java liknar JavaScript:

```java
if (villkor) {
    // Kod som körs om villkoret är sant
}
```

Exempel:

```java
int ålder = 20;

if (ålder >= 18) {
    System.out.println("Du är myndig!");
}
```

### If-else-satser

För att hantera alternativa vägar:

```java
if (villkor) {
    // Kod som körs om villkoret är sant
} else {
    // Kod som körs om villkoret är falskt
}
```

Exempel:

```java
int ålder = 16;

if (ålder >= 18) {
    System.out.println("Du är myndig!");
} else {
    System.out.println("Du är inte myndig än.");
}
```

### If-else if-else-satser

För att hantera flera villkor:

```java
if (villkor1) {
    // Kod som körs om villkor1 är sant
} else if (villkor2) {
    // Kod som körs om villkor1 är falskt och villkor2 är sant
} else {
    // Kod som körs om båda villkoren är falska
}
```

Exempel:

```java
int poäng = 75;

if (poäng >= 90) {
    System.out.println("Utmärkt!");
} else if (poäng >= 70) {
    System.out.println("Bra jobbat!");
} else if (poäng >= 50) {
    System.out.println("Godkänt.");
} else {
    System.out.println("Underkänt.");
}
```

## Jämförelseoperatorer

Java använder samma jämförelseoperatorer som JavaScript:

- `==` - lika med
- `!=` - inte lika med
- `>` - större än
- `<` - mindre än
- `>=` - större än eller lika med
- `<=` - mindre än eller lika med

```java
int a = 5;
int b = 10;

boolean ärLika = (a == b);        // false
boolean ärOlika = (a != b);       // true
boolean ärStörre = (a > b);       // false
boolean ärMindre = (a < b);       // true
boolean ärStörreLika = (a >= b);  // false
boolean ärMindreLika = (a <= b);  // true
```

### Viktigt om jämförelse av objekt!

I Java fungerar `==` för att jämföra primitiva datatyper (int, boolean, etc.), men för objekt som String bör du använda `.equals()` metoden:

```java
// Jämföra primitiva datatyper
int a = 5;
int b = 5;
if (a == b) {  // Detta fungerar som förväntat
    System.out.println("Talen är lika");
}

// Jämföra strängar (fel sätt)
String s1 = new String("Hej");
String s2 = new String("Hej");
if (s1 == s2) {  // Detta jämför referenserna, inte innehållet!
    System.out.println("Detta kanske inte skrivs ut!");
}

// Jämföra strängar (rätt sätt)
if (s1.equals(s2)) {  // Detta jämför innehållet
    System.out.println("Strängarna är lika");
}
```

I vissa fall kan `==` fungera med strängliteraler på grund av strängpoolen i Java, men det är alltid säkrare att använda `.equals()`.

## Logiska operatorer

Java använder samma logiska operatorer som JavaScript:

- `&&` - logiskt OCH (båda villkoren måste vara sanna)
- `||` - logiskt ELLER (minst ett av villkoren måste vara sant)
- `!` - logiskt INTE (negerar villkoret)

```java
int ålder = 25;
boolean harKörkort = true;

// OCH-operator
if (ålder >= 18 && harKörkort) {
    System.out.println("Du får köra bil");
}

// ELLER-operator
if (ålder < 18 || !harKörkort) {
    System.out.println("Du får inte köra bil");
}

// INTE-operator
if (!(ålder >= 18)) {
    System.out.println("Du är inte myndig");
}
```

### Kortslutningsutvärdering

Precis som i JavaScript använder Java kortslutningsutvärdering:

- Med `&&` utvärderas det högra villkoret endast om det vänstra är sant
- Med `||` utvärderas det högra villkoret endast om det vänstra är falskt

```java
int x = 10;

// Om x > 5 är sant, utvärderas aldrig x < 0
if (x > 5 && x < 0) {
    System.out.println("Detta körs aldrig");
}

// Eftersom x > 5 är sant, utvärderas aldrig x < 0
if (x > 5 || x < 0) {
    System.out.println("Detta körs");
}
```

## Ternära operatorer

Den ternära operatorn fungerar som en förkortad if-else-sats:

```java
// syntax: villkor ? värde-om-sant : värde-om-falskt
```

Exempel:

```java
int ålder = 20;
String status = (ålder >= 18) ? "Vuxen" : "Minderårig";
System.out.println(status);  // Skriver ut "Vuxen"
```

Ternära operatorer kan kedjas, men det kan göra koden svårläslig:

```java
int poäng = 75;
String betyg = (poäng >= 90) ? "A" : 
               (poäng >= 80) ? "B" : 
               (poäng >= 70) ? "C" : 
               (poäng >= 60) ? "D" : "F";
System.out.println(betyg);  // Skriver ut "C"
```

## Switch-satser

Switch-satser är användbara när du behöver jämföra en variabel mot flera specifika värden:

```java
int dag = 3;
String dagNamn;

switch (dag) {
    case 1:
        dagNamn = "Måndag";
        break;
    case 2:
        dagNamn = "Tisdag";
        break;
    case 3:
        dagNamn = "Onsdag";
        break;
    case 4:
        dagNamn = "Torsdag";
        break;
    case 5:
        dagNamn = "Fredag";
        break;
    case 6:
        dagNamn = "Lördag";
        break;
    case 7:
        dagNamn = "Söndag";
        break;
    default:
        dagNamn = "Ogiltig dag";
        break;
}

System.out.println("Dag " + dag + " är " + dagNamn);
```

### Viktiga regler för switch i Java:

1. `break` krävs i slutet av varje `case` för att avsluta switch-satsen. Utan break, "faller" exekveringen igenom till nästa case (fall-through).
2. `default` är valfritt, men bra att ha för att hantera oväntade värden.
3. I klassisk Java kan switch-satser bara användas med vissa datatyper:
   - byte, short, int, char
   - Enum typer
   - String (från Java 7 och framåt)

### Medveten fall-through (utan break)

Ibland kan vi vilja utnyttja fall-through beteendet:

```java
int månad = 4;
String säsong;

switch (månad) {
    case 12:
    case 1:
    case 2:
        säsong = "Vinter";
        break;
    case 3:
    case 4:
    case 5:
        säsong = "Vår";
        break;
    case 6:
    case 7:
    case 8:
        säsong = "Sommar";
        break;
    case 9:
    case 10:
    case 11:
        säsong = "Höst";
        break;
    default:
        säsong = "Ogiltig månad";
        break;
}

System.out.println("Månad " + månad + " tillhör " + säsong);
```

I exemplet ovan tillhör månaderna 3, 4 och 5 våren, så vi låter dem dela samma kod utan break förrän efter den sista.

## Praktiska övningar

### Övning 1: Ålderskontroll
Skapa en klass `ÅldersKontroll` som, baserat på en given ålder, skriver ut olika meddelanden:
- Under 13: "Du är ett barn"
- 13-19: "Du är en tonåring"
- 20-64: "Du är en vuxen"
- 65 eller äldre: "Du är en pensionär"

```java
public class ÅldersKontroll {
    public static void main(String[] args) {
        int ålder = 25; // Testa med olika värden
        
        // Din kod här
    }
}
```

### Övning 2: BetygsKalkylator
Skapa en klass `BetygsKalkylator` som tar in ett poängvärde (0-100) och skriver ut motsvarande betyg:
- 90-100: A
- 80-89: B
- 70-79: C
- 60-69: D
- 0-59: F

```java
public class BetygsKalkylator {
    public static void main(String[] args) {
        int poäng = 85; // Testa med olika värden
        
        // Din kod här
    }
}
```

### Övning 3: Miniräknare
Skapa en klass `Miniräknare` som tar in två tal och en operator (+, -, *, /) och utför beräkningen. Använd både if-satser och switch för att implementera detta.

```java
public class Miniräknare {
    public static void main(String[] args) {
        double tal1 = 10.5;
        double tal2 = 5.2;
        char operator = '+'; // Testa med olika operatorer: '+', '-', '*', '/'
        
        // Din kod här - implementera med if-satser
        
        // Din kod här - implementera med switch
    }
}
```

### Övning 4: VeckoplaneringsApp
Skapa en klass `VeckoPlaneringApp` som, baserat på en veckodag (1-7), skriver ut olika aktiviteter:
- Måndag: Skola/Jobb
- Tisdag: Gym
- Onsdag: Studiecirkel
- Torsdag: Ledig kväll
- Fredag: Socialt umgänge
- Lördag och Söndag: Vila och återhämtning

```java
public class VeckoPlaneringApp {
    public static void main(String[] args) {
        int dag = 5; // 1 = Måndag, 7 = Söndag
        
        // Din kod här - använd switch
    }
}
```

### Övning 5: BMI-Kalkylator
Skapa en klass `BMIKalkylator` som beräknar BMI (Body Mass Index) baserat på vikt (kg) och längd (m), och tolkar resultatet:
- Under 18.5: Undervikt
- 18.5–24.9: Normalvikt
- 25–29.9: Övervikt
- 30 eller högre: Fetma

```java
public class BMIKalkylator {
    public static void main(String[] args) {
        double vikt = 70.0; // kg
        double längd = 1.75; // m
        
        // Din kod här
    }
}
```

### Övning 6: Skottår
Skapa en klass `Skottår` som avgör om ett givet år är ett skottår eller inte. Ett år är ett skottår om det är delbart med 4 men inte med 100, ELLER om det är delbart med 400.

```java
public class Skottår {
    public static void main(String[] args) {
        int år = 2024; // Testa med olika årtal
        
        // Din kod här
    }
}
```

### Övning 7: Förbättrad Miniräknare med Scanner
Uppdatera din `Miniräknare` för att använda Scanner-klassen för att ta emot användarinput:

```java
import java.util.Scanner;

public class FörbättradMiniräknare {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Din kod här
        
        scanner.close();
    }
}
```

### Övning 8: KärleksKalkylator
Skapa en klass `KärleksKalkylator` som tar in två namn och, baserat på längden av namnen och antalet gemensamma bokstäver, beräknar en "kärleksprocent" (0-100%). Använd sedan ternära operatorer för att skriva ut olika meddelanden baserat på resultatet.

```java
public class KärleksKalkylator {
    public static void main(String[] args) {
        String namn1 = "Alice";
        String namn2 = "Bob";
        
        // Din kod här
    }
}
```

## Sammanfattning

I denna guide har vi utforskat:
- Grundläggande villkorssatser (if, if-else, if-else if-else)
- Jämförelseoperatorer och viktiga skillnader vid jämförelse av objekt
- Logiska operatorer och kortslutningsutvärdering
- Ternära operatorer
- Switch-satser och fall-through beteende

Villkorssatser är kritiska för att skapa dynamiska och användbara program. Genom att förstå dessa koncept har du lagt grunden för att utveckla mer komplexa applikationer i Java.

**Notera:** Lösningar till övningarna finns i det separata dokumentet "Java Villkorssatser - Övningslösningar".