# Java för JavaScript-utvecklare - Metoder Del 2

I den första delen av vår guide om metoder i Java lärde vi oss grunderna - hur man definierar metoder, hur man använder parametrar och returvärden, samt hur variabelscope fungerar. Nu är det dags att fördjupa oss i några mer avancerade koncept: method overloading och rekursion.

## Method Overloading

I JavaScript kan du inte ha flera funktioner med samma namn. I Java kan du däremot definiera flera metoder med samma namn, så länge de har olika parametrar. Detta kallas för method overloading och är ett kraftfullt verktyg.

### Grundläggande method overloading

```java
public class MethodOverloadingDemo {
    public static void main(String[] args) {
        // Anrop av olika versioner av samma metod
        hälsa();                 // Version utan parametrar
        hälsa("Erik");           // Version med namnparameter
        hälsa("Anna", 25);       // Version med namn och ålder
    }
    
    // Version utan parametrar
    public static void hälsa() {
        System.out.println("Hej, okänd person!");
    }
    
    // Version med en parameter för namn
    public static void hälsa(String namn) {
        System.out.println("Hej " + namn + "!");
    }
    
    // Version med parametrar för namn och ålder
    public static void hälsa(String namn, int ålder) {
        System.out.println("Hej " + namn + "! Du är " + ålder + " år gammal.");
    }
}
```

När du anropar metoden `hälsa()`, bestämmer Java vilken version som ska användas baserat på antalet och typen av parametrar.

### Regler för method overloading

För att overloading ska fungera måste metoderna skilja sig åt i parameterlistorna. Det räcker inte med olika returtyper.

```java
// Korrekt overloading: olika parametertyper
public static int addera(int a, int b) {
    return a + b;
}

public static double addera(double a, double b) {
    return a + b;
}

// FELAKTIGT: samma parametertyper, bara olika returtyp
/*
public static double addera(int a, int b) {
    return (double)(a + b);
}
*/
```

### Praktiska användningsområden

Method overloading gör din kod mer läsbar och flexibel genom att:

1. Tillåta olika sätt att anropa samma funktion
2. Eliminera behovet av olika metodnamn för liknande operationer
3. Hantera olika datatyper på ett naturligt sätt

#### Exempel: Beräkningsmetoder

```java
public class Beräkningar {
    // Area för en cirkel
    public static double area(double radie) {
        return Math.PI * radie * radie;
    }
    
    // Area för en rektangel
    public static double area(double längd, double bredd) {
        return längd * bredd;
    }
    
    // Area för en triangel
    public static double area(double bas, double höjd, boolean ärTriangel) {
        if (ärTriangel) {
            return (bas * höjd) / 2;
        } else {
            return bas * höjd; // Default till rektangel om false
        }
    }
}
```

I detta exempel kan samma metodnamn `area()` användas för att beräkna arean av olika geometriska figurer.

### Method Overloading och Autoboxing

Java tillåter automatisk konvertering mellan primitiva typer och deras motsvarande wrapper-klasser (t.ex. `int` och `Integer`). Detta kan leda till intressanta situationer med method overloading:

```java
public class AutoboxingDemo {
    public static void main(String[] args) {
        visa(42);        // Anropar visa(int)
        visa(Integer.valueOf(42));  // Anropar visa(Integer)
    }
    
    public static void visa(int värde) {
        System.out.println("visa(int): " + värde);
    }
    
    public static void visa(Integer värde) {
        System.out.println("visa(Integer): " + värde);
    }
}
```

Java väljer den metod som passar bäst utan konvertering om möjligt, men kommer att konvertera om det behövs.

### Överblick av Method Overloading

| Aspekt | JavaScript | Java |
|--------|------------|------|
| Stöd för overloading | Nej | Ja |
| Samma namn, olika parametrar | Nej (senare funktion skriver över) | Ja |
| Samma namn, olika returtyp | Nej | Nej (om parameterlistorna är identiska) |

## Rekursion

Rekursion innebär att en metod anropar sig själv. Det är ett kraftfullt koncept som kan användas för att lösa komplexa problem på ett elegant sätt.

### Grundläggande rekursion

Låt oss börja med ett klassiskt exempel: beräkning av fakultet.

```java
public class FakultetDemo {
    public static void main(String[] args) {
        int n = 5;
        System.out.println(n + "! = " + fakultet(n));
    }
    
    public static int fakultet(int n) {
        // Basfall: om n är 0 eller 1
        if (n <= 1) {
            return 1;
        }
        // Rekursivt fall: n! = n * (n-1)!
        else {
            return n * fakultet(n - 1);
        }
    }
}
```

Hur fungerar detta?
1. Om n är 0 eller 1, returneras 1 (basfallet)
2. Annars beräknas n * fakultet(n-1) (det rekursiva fallet)

För n = 5:
- fakultet(5) beräknar 5 * fakultet(4)
- fakultet(4) beräknar 4 * fakultet(3)
- fakultet(3) beräknar 3 * fakultet(2)
- fakultet(2) beräknar 2 * fakultet(1)
- fakultet(1) returnerar 1 (basfall)
- Nu beräknas 2 * 1 = 2
- Sen 3 * 2 = 6
- Sen 4 * 6 = 24
- Sen 5 * 24 = 120
- Resultatet är 120

### Nyckelkomponenter i rekursion

Alla rekursiva lösningar har två viktiga delar:

1. **Basfall**: Villkoret som stoppar rekursionen. Utan detta skulle metoden anropa sig själv i all oändlighet (stack overflow).
2. **Rekursivt fall**: Där metoden anropar sig själv, vanligtvis med en "mindre" version av problemet.

### Ett annat exempel: Fibonacci-sekvens

Fibonacci-sekvensen är en serie tal där varje tal är summan av de två föregående: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

```java
public class FibonacciDemo {
    public static void main(String[] args) {
        int n = 7;  // Beräkna det 7:e Fibonacci-talet
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
        
        // Skriv ut de första 10 Fibonacci-talen
        System.out.print("Fibonacci-sekvens: ");
        for (int i = 0; i < 10; i++) {
            System.out.print(fibonacci(i) + " ");
        }
    }
    
    public static int fibonacci(int n) {
        // Basfall
        if (n <= 1) {
            return n;
        }
        // Rekursivt fall: fib(n) = fib(n-1) + fib(n-2)
        else {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }
    }
}
```

Denna implementation är enkel att förstå men ineffektiv för större värden av n eftersom den beräknar samma Fibonacci-tal flera gånger.

### För- och nackdelar med rekursion

**Fördelar:**
- Kan göra koden mer läsbar och elegant
- Lämpar sig naturligt för problem som har rekursiv natur (t.ex. träd, grafer)
- Kan förenkla lösningen av komplexa problem

**Nackdelar:**
- Kan vara mindre effektivt än iterativa lösningar
- Använder mer minne (varje rekursivt anrop lägger till en ram på stack)
- Risk för stack overflow vid för många rekursiva anrop
- Ibland svårare att felsöka

### Optimera rekursiva lösningar

För Fibonacci-exemplet ovan kan vi använda en teknik som kallas "memoization" för att undvika att beräkna samma värden flera gånger:

```java
public class OptimeradFibonacci {
    public static void main(String[] args) {
        int n = 40;  // Ett större värde nu när vi är mer effektiva
        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
    }
    
    public static long fibonacci(int n) {
        // Skapa en array för att lagra redan beräknade värden
        long[] memo = new long[n + 1];
        return fibonacciMemo(n, memo);
    }
    
    private static long fibonacciMemo(int n, long[] memo) {
        // Basfall
        if (n <= 1) {
            return n;
        }
        
        // Om vi redan har beräknat detta värde
        if (memo[n] != 0) {
            return memo[n];
        }
        
        // Beräkna och spara värdet
        memo[n] = fibonacciMemo(n - 1, memo) + fibonacciMemo(n - 2, memo);
        return memo[n];
    }
}
```

I denna optimerade version lagrar vi beräknade värden i en array så att vi inte behöver beräkna dem igen.

### Rekursion vs Iteration

Många rekursiva problem kan också lösas iterativt (med loopar). Här är Fibonacci igen, men med en iterativ lösning:

```java
public static long fibonacciIterativ(int n) {
    if (n <= 1) {
        return n;
    }
    
    long fib = 1;
    long prevFib = 0;
    
    for (int i = 2; i <= n; i++) {
        long temp = fib;
        fib = fib + prevFib;
        prevFib = temp;
    }
    
    return fib;
}
```

Denna iterativa lösning är snabbare och använder mindre minne än den ursprungliga rekursiva versionen.

## Praktiska övningar

### Övning 1: Method Overloading med Miniräknare
Skapa en klass `Miniräknare` med flera versioner av metoden `beräkna`:
- En version som tar två integers och en operator (char) och utför den valda operationen
- En version som tar två doubles och en operator
- En version som tar två integers och automatiskt adderar dem
- En version som tar en array av integers och adderar alla värden

```java
public class Miniräknare {
    public static void main(String[] args) {
        // Testa dina olika versioner av beräkna här
    }
    
    // Implementera de olika beräkna-metoderna här
}
```

### Övning 2: Method Overloading med Formatering
Skapa en klass `Formaterare` med olika versioner av metoden `formatera`:
- En version som tar en heltalssumma och formaterar den med tusentalsavgränsare
- En version som tar ett namn (String) och returnerar det i formatet "Efternamn, Förnamn" (anta att namnet har formatet "Förnamn Efternamn")
- En version som tar ett telefonnummer och formaterar det snyggt

```java
public class Formaterare {
    public static void main(String[] args) {
        // Testa dina olika versioner av formatera här
    }
    
    // Implementera de olika formatera-metoderna här
}
```

### Övning 3: Enkel Rekursion
Skapa en klass `RekursionsÖvningar` med en rekursiv metod `summa` som beräknar summan av alla heltal från 1 till n.

```java
public class RekursionsÖvningar {
    public static void main(String[] args) {
        int n = 5;
        System.out.println("Summan av 1 till " + n + " är: " + summa(n));
    }
    
    // Implementera den rekursiva summa-metoden här
}
```

### Övning 4: Rekursiv Palindromkontroll
Skapa en klass `Palindrom` med en rekursiv metod `ärPalindrom` som kontrollerar om en sträng är ett palindrom (läses likadant framifrån och bakifrån).

```java
public class Palindrom {
    public static void main(String[] args) {
        String[] testSträngar = {"anna", "palindrom", "level", "java"};
        
        for (String s : testSträngar) {
            System.out.println(s + " är palindrom: " + ärPalindrom(s));
        }
    }
    
    // Implementera den rekursiva ärPalindrom-metoden här
}
```

### Övning 5: Binärsökning (Rekursiv)
Implementera en rekursiv binärsökningsalgoritm. Binärsökning är en effektiv metod för att hitta ett element i en sorterad array.

```java
public class BinärSökning {
    public static void main(String[] args) {
        int[] sortedArray = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
        int sökTal = 23;
        
        int index = binärSök(sortedArray, sökTal, 0, sortedArray.length - 1);
        
        if (index != -1) {
            System.out.println(sökTal + " finns på index " + index);
        } else {
            System.out.println(sökTal + " finns inte i arrayen");
        }
    }
    
    // Implementera den rekursiva binärSök-metoden här
}
```

## Sammanfattning

I den här delen av vår guide om metoder i Java har vi utforskat:

1. **Method Overloading**
   - Hur man definierar flera metoder med samma namn men olika parametrar
   - Regler och begränsningar för method overloading
   - Praktiska användningsområden

2. **Rekursion**
   - Grundläggande principer för rekursiva metoder
   - Basfall och rekursiva fall
   - För- och nackdelar med rekursion
   - Optimering av rekursiva lösningar

Dessa koncept är viktiga verktyg i en Java-utvecklares verktygslåda. Method overloading ger dig flexibilitet och tydlighet i din kod, medan rekursion erbjuder eleganta lösningar på vissa typer av problem. Med övning kommer du att lära dig när och hur du bäst använder dessa tekniker.

**Notera:** Lösningar till övningarna finns i det separata dokumentet "Java Metoder Del 2 - Övningslösningar".