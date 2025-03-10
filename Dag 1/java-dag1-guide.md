# Java för JavaScript-utvecklare - Dag 1

## Vad är Java?

När du skriver kod i JavaScript för webben tolkas den direkt av webbläsaren. Men hur fungerar program som körs utanför webbläsaren, på allt från mobila enheter till servrar eller vanliga datorprogram? Det är här språk som Java kommer in.

Java är ett programmeringsspråk som utvecklades på 1990-talet och är fortfarande ett av världens mest använda språk. Det skapades för att vara plattformsoberoende med principen "Write Once, Run Anywhere" (WORA).

### Vad gör en Java-utvecklare?

En Java-utvecklare arbetar med att:
- Skapa Android-appar
- Utveckla backend-tjänster för webbapplikationer
- Bygga robusta system för företag
- Skapa program som fungerar på olika operativsystem
- Utveckla inbyggda system i allt från hushållsapparater till industriella maskiner

### Javas roll i dagens teknikvärld

Java används fortfarande i stor utsträckning inom:
- Enterprise-system i stora företag
- Android-appar
- Webbtjänster och API:er
- Finanssystem och bankappar
- Big Data-applikationer

## Java vs JavaScript: Att förstå grundläggande skillnader

Trots det liknande namnet är Java och JavaScript helt olika språk:

### Kompilerat vs. tolkat språk

**JavaScript**:
- Tolkas direkt av webbläsaren
- Eventuella syntaxfel upptäcks först när koden körs
- Ingen kompileringsfas

**Java**:
- Kompileras först till bytecode innan det körs
- Många fel upptäcks vid kompilering innan programmet körs
- Kräver Java Virtual Machine (JVM) för att köra

### Typhantering

**JavaScript**:
- Dynamisk typning: variabler kan ändra typ
- `let x = 10; x = "text";` är helt tillåtet

**Java**:
- Statisk typning: variabeltyp måste deklareras och kan inte ändras
- `int x = 10; x = "text";` ger kompileringsfel

### Programstruktur

**JavaScript**:
- Kod kan skrivas direkt i en JS-fil
- Funktioner kan existera utanför klasser
- Mer flexibel struktur

**Java**:
- All kod måste finnas i klasser
- Varje fil måste ha samma namn som den publika klassen den innehåller
- Striktare regler för kod och filorganisation

## Java-miljön: Vad behöver du?

För att komma igång med Java behöver du:

### JDK (Java Development Kit)
Detta är den grundläggande utvecklingsmiljön med:
- **Javac**: Kompilatorn som översätter din kod till bytecode
- **JRE**: Miljön som kör Java-program
- **Standardbibliotek**: Java API med många färdiga klasser

### IDE (Integrated Development Environment)
För effektiv Java-utveckling rekommenderar vi:
- **IntelliJ IDEA**: Populär bland professionella utvecklare
- **Eclipse**: Öppen källkod med stort ekosystem
- **NetBeans**: Enkel att komma igång med

## Java - Grundläggande syntax

Låt oss se hur grundläggande Java-syntax skiljer sig från JavaScript:

### Programstruktur

Det allra enklaste Java-programmet:

```java
public class HejVarlden {
    public static void main(String[] args) {
        System.out.println("Hej, världen!");
    }
}
```

Viktiga punkter:
- `public class HejVarlden` - Klassnamnet måste matcha filnamnet (HejVarlden.java)
- `public static void main(String[] args)` - Huvudmetoden som körs när programmet startar
- `System.out.println()` - Metod för att skriva ut text till konsolen

### Variabler och datatyper

I Java måste du deklarera typen för varje variabel:

```java
// Primitiva datatyper
int heltal = 10;
double decimaltal = 10.5;
boolean santEllerFalskt = true;
char tecken = 'A';

// Referenstyper
String text = "Detta är en textsträng";
```

**Viktigt**: I Java skrivs String med stor begynnelsebokstav, eftersom det är en klass och inte en primitiv datatyp.

### Kommentarer

Kommentarer i Java fungerar precis som i JavaScript:

```java
// Detta är en enradskommentar

/*
   Detta är en
   flerradig kommentar
*/

/**
 * Detta är en dokumentationskommentar (JavaDoc)
 * som används för att dokumentera klasser och metoder
 */
```

### Operatorer

De flesta operatorer i Java liknar JavaScript:

```java
// Aritmetiska operatorer
int summa = 5 + 3;       // 8
int differens = 5 - 3;   // 2
int produkt = 5 * 3;     // 15
int kvot = 5 / 2;        // 2 (heltalsdivision!)
double exaktKvot = 5.0 / 2.0;  // 2.5
int rest = 5 % 2;        // 1 (modulus/rest)

// Jämförelseoperatorer
boolean storre = 5 > 3;   // true
boolean lika = 5 == 5;    // true

// Logiska operatorer
boolean ochOperator = true && false;  // false
boolean ellerOperator = true || false;  // true
boolean inteOperator = !true;  // false
```

### Strängkonkatenering

I Java används `+` för att kombinera strängar:

```java
String halsning = "Hallo, " + "världen!";  // "Hallo, världen!"
String namn = "Maria";
String personligHalsning = "Hej " + namn;  // "Hej Maria"
String nummer = "42";
int tal = 10;
String kombination = nummer + tal;  // "4210" (tal konverteras till sträng)
```

### Kontrollflöden

Kontrollflöden i Java liknar även de JavaScript:

#### If-satser
```java
int alder = 18;

if (alder >= 18) {
    System.out.println("Du är myndig");
} else if (alder >= 15) {
    System.out.println("Du får se ungdomsfilmer");
} else {
    System.out.println("Du behöver barnrabatt");
}
```

#### Loopar
```java
// For-loop
for (int i = 0; i < 5; i++) {
    System.out.println("Iteration " + i);
}

// While-loop
int j = 0;
while (j < 5) {
    System.out.println("While iteration " + j);
    j++;
}

// Do-while loop
int k = 0;
do {
    System.out.println("Do-while iteration " + k);
    k++;
} while (k < 5);
```

## Användarinput med Scanner

I konsollapplikationer använder vi ofta Scanner-klassen för att läsa input från användaren:

```java
import java.util.Scanner;

public class AnvandarInput {
    public static void main(String[] args) {
        // Skapa ett Scanner-objekt
        Scanner scanner = new Scanner(System.in);
        
        // Be om namn
        System.out.print("Vad heter du? ");
        String namn = scanner.nextLine();
        
        // Be om ålder
        System.out.print("Hur gammal är du? ");
        int alder = scanner.nextInt();
        
        // Skriv ut resultat
        System.out.println("Hej " + namn + "! Du är " + alder + " år gammal.");
        
        // Stäng Scanner (good practice)
        scanner.close();
    }
}
```

## Vanliga fallgropar för JavaScript-utvecklare i Java

När man kommer från JavaScript är det lätt att falla i vissa fallgropar. Här är några att vara uppmärksam på:

### 1. Semikolon är obligatoriska

I JavaScript kan du ofta skippa semikolon. I Java är de obligatoriska.

```java
// Korrekt
int x = 5;

// Felaktigt (ger kompileringsfel)
int x = 5
```

### 2. Allt måste finnas i klasser

I JavaScript kan du ha fristående funktioner och variabler. I Java måste all kod vara inom klasser.

```java
// Korrekt
public class MinApp {
    public static void main(String[] args) {
        int x = 5;
    }
}

// Felaktigt (ger kompileringsfel)
int x = 5;
```

### 3. Strikt typning

I JavaScript kan variabeltyper ändras. I Java är det inte möjligt.

```java
// Korrekt
String text = "Hej";
int tal = 5;

// Felaktigt (ger kompileringsfel)
String text = "Hej";
text = 5;
```

### 4. Primitiva typer vs. objekttyper

I JavaScript är allt objekt. I Java finns primitiva typer och objekttyper.

```java
// Primitiva typer använder ==
int a = 5;
int b = 5;
boolean arLika = (a == b);  // true

// Objekttyper ska jämföras med equals()
String s1 = new String("Hej");
String s2 = new String("Hej");
boolean strLika = s1.equals(s2);  // true
boolean refLika = (s1 == s2);     // false, jämför referenser
```

### 5. Array har fast storlek

I JavaScript kan arrays växa dynamiskt. I Java har arrays fast storlek.

```java
// Javas array har fast storlek
int[] arr = new int[5];
// arr.length är 5 och kan inte ändras
```

## Resurser för fortsatt lärande

Här är några bra resurser för att lära dig mer om Java:

- **Oracle Java Tutorials**: https://docs.oracle.com/javase/tutorial/
- **W3Schools Java Tutorial**: https://www.w3schools.com/java/
- **Codecademy Java Course**: https://www.codecademy.com/learn/learn-java
- **Boken "Head First Java"**: Utmärkt för nybörjare som kommer från andra språk
- **Boken "Effective Java" av Joshua Bloch**: När du är redo för mer avancerade koncept

## Sammanfattning

I denna introduktion har vi utforskat:

1. **Vad är Java** och hur det skiljer sig från JavaScript
2. **Java-miljön** och verktygen du behöver för att komma igång
3. **Grundläggande Java-syntax** inklusive variabler, datatyper och operatorer
4. **Kontrollflöden** med if-satser och loopar
5. **Användarinput** med Scanner-klassen
6. **Vanliga fallgropar** för JavaScript-utvecklare som lär sig Java


Java är ett starkt typat, kompilerat språk som erbjuder stabilitet och prestanda. För JavaScript-utvecklare kan övergången till Java innebära en lärokurva när det gäller typhantering och kompilering, men många koncept som kontrollflöden och grundläggande syntax är bekanta.

Kom ihåg att Java-utveckling bygger på en solid förståelse för grunderna, så ta tiden att bli bekväm med dessa koncept innan vi går vidare till mer avancerade ämnen.
