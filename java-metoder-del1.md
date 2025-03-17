# Java för JavaScript-utvecklare - Metoder Del 1

## Vad är metoder i Java?

I JavaScript kallar vi dem funktioner, i Java kallar vi dem metoder - men konceptet är liknande. Metoder är återanvändbara kodblock som utför specifika uppgifter och kan anropas från olika delar av programmet.

I Java finns en viktig skillnad: alla metoder måste definieras inuti en klass. Men eftersom vi ännu inte har fokuserat på OOP-koncept, kommer vi att arbeta med `static` metoder inom vår `main`-klass.

## Grundläggande metoder

En metod i Java har följande grundstruktur:

```java
public static returtyp metodNamn(parametertyp parameterNamn) {
    // Metodens kod
    return värde; // Om returtypen inte är void
}
```

Låt oss bryta ner delarna:

- `public` - Åtkomstnivå (vem som kan använda metoden)
- `static` - Gör att metoden tillhör klassen, inte instanser av klassen
- `returtyp` - Vilken typ av data metoden returnerar (t.ex. `int`, `String`, `void`)
- `metodNamn` - Namn på metoden (använd camelCase i Java)
- `parametertyp parameterNamn` - Data som skickas in till metoden

### Exempel på enkel metod

```java
public class MetodDemo {
    public static void main(String[] args) {
        // Anropa vår metod
        hälsa();
    }
    
    // En enkel metod utan parametrar och utan returvärde
    public static void hälsa() {
        System.out.println("Hej från metoden!");
    }
}
```

## Parametrar

Parametrar är värden som skickas in till en metod när den anropas. I Java måste du specificera vilken datatyp varje parameter har.

### Exempel med parametrar

```java
public class ParameterDemo {
    public static void main(String[] args) {
        // Anropa metod med två parametrar
        hälsaTill("Erik", 25);
        hälsaTill("Anna", 30);
    }
    
    public static void hälsaTill(String namn, int ålder) {
        System.out.println("Hej " + namn + "! Du är " + ålder + " år gammal.");
    }
}
```

## Returvärden

Returvärden är data som en metod skickar tillbaka när den är klar. Returtypen måste deklareras när metoden definieras.

### Exempel med returvärde

```java
public class ReturvärdeDemo {
    public static void main(String[] args) {
        int summa = addera(5, 3);
        System.out.println("Summan är: " + summa);
        
        // Vi kan också använda returvärdet direkt
        System.out.println("Produkten är: " + multiplicera(4, 2));
    }
    
    public static int addera(int tal1, int tal2) {
        return tal1 + tal2;
    }
    
    public static int multiplicera(int tal1, int tal2) {
        return tal1 * tal2;
    }
}
```

Om en metod inte ska returnera något värde, använder vi returtypen `void`:

```java
public static void skrivUtHälsning() {
    System.out.println("Hej!");
    // Ingen return-sats behövs
}
```

### Viktigt om returvärden

1. Alla vägar genom metoden måste returnera ett värde (om returtypen inte är `void`)
2. När en `return`-sats exekveras, avslutas metoden omedelbart

```java
public static int getBetyg(int poäng) {
    if (poäng >= 90) {
        return 5;
    } else if (poäng >= 80) {
        return 4;
    } else if (poäng >= 70) {
        return 3;
    } else if (poäng >= 60) {
        return 2;
    } else {
        return 1;
    }
    // Koden här kommer aldrig att köras
}
```

## Scope (variablers synlighet)

I Java begränsas variablers synlighet till det kodblock där de definieras. Detta kallas för variabelns "scope".

```java
public class ScopeDemo {
    public static void main(String[] args) {
        int x = 10; // Variabel i main-metoden
        
        System.out.println("x i main: " + x);
        
        testScope();
        
        // System.out.println(y); // Skulle ge kompileringsfel - y finns inte här
    }
    
    public static void testScope() {
        // System.out.println(x); // Skulle ge kompileringsfel - x finns inte här
        
        int y = 20; // Lokal variabel i testScope-metoden
        System.out.println("y i testScope: " + y);
    }
}
```

### Variabelsynlighet i kodblock

Variabler definierade i ett kodblock (mellan `{ }`) är bara synliga inom det blocket:

```java
public static void blockScope() {
    int a = 1;
    
    if (a == 1) {
        int b = 2; // b är bara synlig inom if-blocket
        System.out.println("a: " + a + ", b: " + b);
    }
    
    // System.out.println(b); // Kompileringsfel - b finns inte här
    
    for (int i = 0; i < 3; i++) {
        System.out.println("i: " + i); // i är bara synlig i for-loopen
    }
    
    // System.out.println(i); // Kompileringsfel - i finns inte här
}
```

## Praktiska övningar

### Övning 1: Grundläggande metodanrop
Skapa en klass `MetodÖvning1` med en `main`-metod och en metod `skrivUtInfo` som tar ett namn och en ålder som parametrar och skriver ut information om personen.

```java
public class MetodÖvning1 {
    public static void main(String[] args) {
        // Anropa metoden med olika värden
        // Din kod här
    }
    
    // Skapa metoden skrivUtInfo här
}
```

### Övning 2: Returvärden
Skapa en klass `MetodÖvning2` med metoder för att beräkna arean av olika geometriska figurer (rektangel, triangel, cirkel). Testa metoderna från `main`-metoden.

```java
public class MetodÖvning2 {
    public static void main(String[] args) {
        // Testa dina metoder här
    }
    
    // Skapa metoder för areaBeräkning här
    // public static double rektangelArea(double bredd, double höjd) { ... }
    // public static double triangelArea(double bas, double höjd) { ... }
    // public static double cirkelArea(double radie) { ... }
}
```

### Övning 3: Scope
Skapa en klass `ScopeÖvning` och skriv kod som demonstrerar hur variabler påverkas av scope.

```java
public class ScopeÖvning {
    public static void main(String[] args) {
        // Skapa några variabler i main
        
        // Anropa en metod och försök använda variablerna
    }
    
    // Skapa en metod som definierar egna variabler och försöker använda
    // variabler från main-metoden
}
```

### Övning 4: Metodkombination
Skapa en klass `ArrayMetoder` med metoder för att:
1. Skapa och returnera en array med slumpmässiga tal
2. Beräkna summan av värdena i en array
3. Hitta det största värdet i en array
4. Skriva ut innehållet i en array

Testa alla metoder från `main`-metoden.

```java
import java.util.Random;

public class ArrayMetoder {
    public static void main(String[] args) {
        // Testa alla dina metoder här
    }
    
    // Skapa och implementera metoderna här
}
```

### Övning 5: Temperaturomvandlare
Skapa en klass `TemperaturOmvandlare` med metoder för att omvandla mellan Celsius och Fahrenheit. Låt användaren mata in temperaturer via Scanner.

```java
import java.util.Scanner;

public class TemperaturOmvandlare {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Implementera användarinteraktion här
        
        scanner.close();
    }
    
    // Skapa metoder för celsiusTillFahrenheit och fahrenheitTillCelsius
}
```

## Slutsats

I denna del har vi utforskat grunderna i metoder i Java, inklusive:
- Hur man definierar och anropar metoder
- Hur man arbetar med parametrar
- Hur man använder returvärden
- Hur variablers scope fungerar

Genom att använda metoder kan vi:
- Strukturera vår kod i återanvändbara block
- Göra koden mer läsbar
- Undvika duplicering av kod
- Bygga komplexare program genom att kombinera enkla, testbara delar

I nästa del kommer vi att utforska mer avancerade metodkoncept som method overloading och en introduktion till rekursion.

**Notera:** Lösningar till övningarna finns i det separata dokumentet "Java Metoder - Övningslösningar".

## Slutsats

I denna del har vi utforskat grunderna i metoder i Java, inklusive:
- Hur man definierar och anropar metoder
- Hur man arbetar med parametrar
- Hur man använder returvärden
- Hur variablers scope fungerar

Genom att använda metoder kan vi:
- Strukturera vår kod i återanvändbara block
- Göra koden mer läsbar
- Undvika duplicering av kod
- Bygga komplexare program genom att kombinera enkla, testbara delar

I nästa del kommer vi att utforska mer avancerade metodkoncept som method overloading och en introduktion till rekursion.