# Java för JavaScript-utvecklare - Loopar

## Introduktion till loopar i Java

Loopar är en grundläggande del av programmeringsspråk och används för att upprepa kodblock flera gånger. För JavaScript-utvecklare kommer många loopkoncept att kännas bekanta, men det finns några viktiga skillnader i syntax och beteende som är värda att notera.

I denna guide kommer vi att gå igenom de olika typerna av loopar i Java och jämföra dem med deras motsvarigheter i JavaScript.

## For-loopar

### Grundläggande for-loop

For-loopar i Java har samma grundläggande struktur som i JavaScript:

```java
for (initiering; villkor; uppdatering) {
    // Kod som upprepas
}
```

Exempel:

```java
// Skriv ut talen 0 till 4
for (int i = 0; i < 5; i++) {
    System.out.println("Värdet av i: " + i);
}
```

**Viktigt att notera för JavaScript-utvecklare:**
- I Java måste variabeln deklareras med en datatyp (`int i` istället för bara `i`)
- Variabeln `i` är endast synlig (i scope) inom for-loopen
- Om du försöker använda `i` utanför loopen får du ett kompileringsfel

### Utelämna delar av for-loopen

Du kan utelämna vilken som helst av de tre delarna i en for-loop, men semikolonen måste finnas kvar:

```java
// Initiering utanför loopen
int i = 0;
for (; i < 5; i++) {
    System.out.println(i);
}

// Uppdatering inuti loopen
for (int j = 0; j < 5;) {
    System.out.println(j);
    j++;
}

// Oändlig loop med villkor inuti
for (;;) {
    System.out.println("Oändlig loop!");
    // Måste ha ett break-villkor någonstans för att avsluta
    break;
}
```

## For-each loop (Enhanced for loop)

För att iterera över arrays och collections finns en förenklad syntax som kallas for-each loop eller enhanced for loop:

```java
for (datatyp variabel : samling) {
    // Kod som utförs för varje element
}
```

Exempel med array:

```java
String[] frukter = {"Äpple", "Banan", "Apelsin", "Kiwi"};

for (String frukt : frukter) {
    System.out.println("Frukt: " + frukt);
}
```

**Skillnader från JavaScript:**
- Du måste ange datatypen för elementet (t.ex. `String frukt`)
- I JavaScript motsvaras detta av `for...of` loopen, inte `for...in` (som i JavaScript ger nycklarna/indexen)

## While-loopar

While-loopar utför en kodblock så länge ett villkor är sant:

```java
while (villkor) {
    // Kod som upprepas
}
```

Exempel:

```java
int i = 0;
while (i < 5) {
    System.out.println("i: " + i);
    i++;
}
```

**Viktigt att notera:**
- Precis som med villkor i if-satser måste villkoret i en while-loop returnera en boolean
- Du måste vanligtvis uppdatera en variabel inuti loopen för att undvika oändliga loopar

## Do-while loopar

Do-while loopar är som while-loopar, men de utför kodblocket minst en gång innan villkoret kontrolleras:

```java
do {
    // Kod som upprepas
} while (villkor);
```

Exempel:

```java
int i = 0;
do {
    System.out.println("i: " + i);
    i++;
} while (i < 5);
```

**Skillnad från while-loop:**
- Do-while loopar utför alltid kodblocket minst en gång, även om villkoret är falskt från början
- Observera semikolonet efter while-villkoret

## Kontrollera loopexekvering

### Break

`break`-satsen avslutar närmaste omslutande loop:

```java
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break; // Avsluta loopen när i är 5
    }
    System.out.println(i);
}
// Utskrift: 0, 1, 2, 3, 4
```

### Continue

`continue`-satsen hoppar över den aktuella iterationen och fortsätter med nästa:

```java
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue; // Hoppa över jämna tal
    }
    System.out.println(i);
}
// Utskrift: 1, 3, 5, 7, 9
```

### Labeled Breaks och Continues

Java stöder "labeled" break och continue, vilket gör att du kan avsluta eller fortsätta specifika yttre loopar:

```java
ytterLoop: for (int i = 0; i < 3; i++) {
    innerLoop: for (int j = 0; j < 3; j++) {
        if (i == 1 && j == 1) {
            break ytterLoop; // Avsluta både inre och yttre loopen
        }
        System.out.println("i = " + i + ", j = " + j);
    }
}
```

Detta är särskilt användbart i nestade loopar när du vill avsluta eller hoppa över en yttre loop från en inre loop.

## Nestade loopar

Loopar kan placeras inuti varandra för att hantera mer komplexa iterationer:

```java
// Skriv ut en multiplikationstabell 5x5
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= 5; j++) {
        System.out.print(i * j + "\t");
    }
    System.out.println(); // Ny rad efter varje rad i tabellen
}
```

## Iterera över arrays

### Iterera med index (for-loop)

```java
int[] siffror = {10, 20, 30, 40, 50};

// Använda traditionell for-loop med index
for (int i = 0; i < siffror.length; i++) {
    System.out.println("Element " + i + ": " + siffror[i]);
}
```

### Iterera med for-each

```java
int[] siffror = {10, 20, 30, 40, 50};

// Använda for-each loop
for (int tal : siffror) {
    System.out.println("Tal: " + tal);
}
```

**För- och nackdelar med for-each:**
- Fördel: Enklare, mer läsbar syntax
- Nackdel: Du får inte tillgång till index
- Nackdel: Du kan inte tilldela nya värden till arrayens element (eftersom du arbetar med en kopia av värdet, inte en referens till arrayplatsen)

## Iterera över String-tecken

Strings kan behandlas som sekvenser av tecken:

```java
String text = "Hej Java!";

// Traditionell for-loop
for (int i = 0; i < text.length(); i++) {
    char c = text.charAt(i);
    System.out.println("Tecken på position " + i + ": " + c);
}

// Alternativt, konvertera till char-array och använd for-each
for (char c : text.toCharArray()) {
    System.out.println("Tecken: " + c);
}
```

## Oändliga loopar och hur man undviker dem

En oändlig loop skapas när stopvillkoret aldrig blir sant:

```java
// Medveten oändlig loop
while (true) {
    // Koden körs för evigt om det inte finns ett break-villkor
    if (användareVillAvsluta()) {
        break;
    }
}

// Oavsiktlig oändlig loop (glömt inkrementera i)
int i = 0;
while (i < 10) {
    System.out.println(i);
    // Glömt i++, så i är alltid 0 och villkoret är alltid sant
}
```

För att undvika oavsiktliga oändliga loopar:
- Dubbelkolla att loopvillkoret kan bli falskt
- Säkerställ att variabler som kontrollerar loopen uppdateras
- Överväg att lägga till en säkerhetsventil (räknare som avbryter efter ett visst antal iterationer)

## Prestandaöverväganden

När du arbetar med loopar, särskilt med stora datamängder, är det viktigt att tänka på prestanda:

1. **Undvik att skapa objekt i loopar** om det inte är nödvändigt
2. **Minimera scope för looparnas variabler** för bättre läsbarhet och möjligtvis bättre prestanda
3. **Spara array-längden i en variabel** när du itererar över stora arrays:

```java
int[] storArray = new int[1000000];
int längd = storArray.length; // Beräkna längden en gång

for (int i = 0; i < längd; i++) {
    // Använd den sparade längden istället för att anropa .length varje iteration
}
```

## Vilken loop ska man välja?

Olika typer av loopar passar bättre för olika situationer. Här är några riktlinjer som hjälper dig välja rätt:

### När använda for-loop?
- När du vet i förväg exakt hur många iterationer loopen ska köra
- När du arbetar med index, t.ex. för att gå igenom en array med index
- När du behöver en räknare som ökar eller minskar i ett fördefinierat mönster

```java
// Exempel: Gå igenom en array med index
int[] siffror = {10, 20, 30, 40, 50};
for (int i = 0; i < siffror.length; i++) {
    System.out.println("Element på index " + i + ": " + siffror[i]);
}

// Exempel: Nedräkning
for (int i = 10; i > 0; i--) {
    System.out.println(i);
}
```

### När använda for-each loop?
- När du behöver gå igenom alla element i en samling (array, lista, etc.)
- När du inte behöver veta indexet för varje element
- När du inte behöver modifiera samlingen under iteration

```java
// Exempel: Enkel iteration över en array
String[] namn = {"Anna", "Erik", "Maria", "Johan"};
for (String person : namn) {
    System.out.println("Hej " + person + "!");
}
```

### När använda while-loop?
- När du inte vet i förväg hur många iterationer som behövs
- När loopens fortsättning beror på en kondition som kan förändras inom loopen
- När du kanske behöver skippa loopen helt (om villkoret är falskt från början)

```java
// Exempel: Läsa input tills användaren skriver "sluta"
Scanner scanner = new Scanner(System.in);
String input = "";
while (!input.equals("sluta")) {
    System.out.print("Skriv något (eller 'sluta' för att avsluta): ");
    input = scanner.nextLine();
    if (!input.equals("sluta")) {
        System.out.println("Du skrev: " + input);
    }
}
```

### När använda do-while loop?
- När loopen måste köras minst en gång oavsett villkoret
- För menybaserade program där användaren först ser en meny, gör ett val, och sedan kanske upprepar
- För validering av användarinput där du vill be om input och sedan validera den

```java
// Exempel: Enkel meny som körs minst en gång
Scanner scanner = new Scanner(System.in);
int val;
do {
    System.out.println("\nMeny:");
    System.out.println("1. Visa information");
    System.out.println("2. Uppdatera");
    System.out.println("0. Avsluta");
    System.out.print("Ditt val: ");
    val = scanner.nextInt();
    
    switch (val) {
        case 1:
            System.out.println("Visar information...");
            break;
        case 2:
            System.out.println("Uppdaterar...");
            break;
        case 0:
            System.out.println("Avslutar...");
            break;
        default:
            System.out.println("Ogiltigt val!");
    }
} while (val != 0);
```

### Sammanfattning för val av loop:

| Loop-typ | Bäst för | Exempel |
|----------|----------|---------|
| for | När antalet iterationer är känt | Gå igenom array med index, räkna upp/ner |
| for-each | Gå igenom alla element i en samling | Bearbeta alla element utan att behöva index |
| while | När antal iterationer är okänt och loopen kan behöva skippas | Körning baserad på användarinput, sökning |
| do-while | När loopen måste köras minst en gång | Validering av input, menyer |

### Övning 1: Grundläggande For-loop
Skapa en klass `TalUtskrift` som använder en for-loop för att skriva ut alla tal från 1 till 10.

```java
public class TalUtskrift {
    public static void main(String[] args) {
        // Din kod här
    }
}
```

### Övning 2: Summer tal
Skapa en klass `TalSummering` som använder en loop för att beräkna summan av alla tal från 1 till 100.

```java
public class TalSummering {
    public static void main(String[] args) {
        // Din kod här
    }
}
```

### Övning 3: Fakultetsberäkning
Skapa en klass `Fakultet` som beräknar fakulteten (n!) av ett positivt heltal. 
Fakulteten av ett tal n är produkten av alla positiva heltal mindre än eller lika med n.
Exempel: 5! = 5 × 4 × 3 × 2 × 1 = 120

```java
public class Fakultet {
    public static void main(String[] args) {
        int n = 5; // Testa med olika värden
        
        // Din kod här
    }
}
```

### Övning 4: Multiplikationstabell
Skapa en klass `Multiplikationstabell` som skriver ut en multiplikationstabell för talen 1 till 10. Använd nestade loopar.

```java
public class Multiplikationstabell {
    public static void main(String[] args) {
        // Din kod här
    }
}
```

### Övning 5: Primtalstest
Skapa en klass `Primtalstest` som avgör om ett tal är ett primtal eller inte. Ett primtal är ett naturligt tal större än 1 som inte kan delas jämnt med något annat naturligt tal än 1 och sig självt.

```java
public class Primtalstest {
    public static void main(String[] args) {
        int tal = 17; // Testa med olika värden
        
        // Din kod här
    }
}
```

### Övning 6: Array-summering
Skapa en klass `ArraySummering` som beräknar och skriver ut summan av alla element i en array.

```java
public class ArraySummering {
    public static void main(String[] args) {
        int[] siffror = {5, 10, 15, 20, 25};
        
        // Din kod här
    }
}
```

### Övning 7: Palindromtest
Skapa en klass `Palindromtest` som kontrollerar om en given sträng är ett palindrom. Ett palindrom är en sekvens av tecken som läses likadant framifrån som bakifrån (ignorera mellanslag, skiljetecken och skiftläge).
Exempel: "A man, a plan, a canal, Panama!" är ett palindrom.

```java
public class Palindromtest {
    public static void main(String[] args) {
        String text = "A man, a plan, a canal, Panama!";
        
        // Din kod här
    }
}
```

### Övning 8: Mönstergenerering
Skapa en klass `Mönstergenerering` som skriver ut ett triangelmönster med asterisker (*). Använd nestade loopar.

```java
public class Mönstergenerering {
    public static void main(String[] args) {
        int höjd = 5; // Testa med olika värden
        
        // Din kod här
        // Resultat för höjd 5:
        // *
        // **
        // ***
        // ****
        // *****
    }
}
```

### Övning 9: Fibonacci-sekvens
Skapa en klass `Fibonacci` som skriver ut de första n termerna i Fibonacci-sekvensen. Fibonacci-sekvensen börjar med 0 och 1, och varje efterföljande tal är summan av de två föregående.
Exempel: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

```java
public class Fibonacci {
    public static void main(String[] args) {
        int n = 10; // Antal termer att visa
        
        // Din kod här
    }
}
```

### Övning 10: Lottery Number Generator
Skapa en klass `LotteryGenerator` som genererar 7 unika slumpmässiga tal mellan 1 och 35 (som i ett lotteri). Alla tal måste vara olika.

```java
import java.util.Random;

public class LotteryGenerator {
    public static void main(String[] args) {
        // Din kod här
    }
}
```

## Sammanfattning

I denna guide har vi utforskat:
- Grundläggande looptyper i Java: for, for-each, while, och do-while
- Kontrollera loopexekvering med break och continue
- Nestade loopar och labeled break/continue
- Metoder för att iterera över arrays och strängar
- Tips för att undvika oändliga loopar
- Prestandaöverväganden när det gäller loopar

Loopar är en av de viktigaste byggstenarna i programmeringsspråk och ger dig möjlighet att automatisera repetitiva uppgifter. Genom att bemästra dem tar du ett viktigt steg i din utveckling som Java-programmerare.

**Notera:** Lösningar till övningarna finns i det separata dokumentet "Java Loopar - Övningslösningar".