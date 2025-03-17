# Java Metoder - Övningslösningar

Detta dokument innehåller lösningar till övningarna från "Java för JavaScript-utvecklare - Metoder Del 1".

## Lösning Övning 1: Grundläggande metodanrop

```java
public class MetodÖvning1 {
    public static void main(String[] args) {
        // Anropa metoden med olika värden
        skrivUtInfo("Erik", 25);
        skrivUtInfo("Anna", 30);
        skrivUtInfo("Sven", 45);
    }
    
    public static void skrivUtInfo(String namn, int ålder) {
        System.out.println(namn + " är " + ålder + " år gammal.");
        
        if (ålder < 18) {
            System.out.println(namn + " är inte myndig.");
        } else {
            System.out.println(namn + " är myndig.");
        }
    }
}
```

**Viktiga koncept:**
- Metoden `skrivUtInfo` tar två parametrar: en `String` och en `int`
- Metoden har returtyp `void` (returnerar inget värde)
- Metoden använder parametrarna för att skapa och skriva ut meddelanden

## Lösning Övning 2: Returvärden

```java
public class MetodÖvning2 {
    public static void main(String[] args) {
        // Testa metoderna
        double rektArea = rektangelArea(5.0, 3.0);
        System.out.println("Rektangelns area: " + rektArea);
        
        System.out.println("Triangelns area: " + triangelArea(4.0, 6.0));
        
        double radie = 2.5;
        double cirkelA = cirkelArea(radie);
        System.out.println("Cirkelns area med radie " + radie + ": " + cirkelA);
    }
    
    public static double rektangelArea(double bredd, double höjd) {
        return bredd * höjd;
    }
    
    public static double triangelArea(double bas, double höjd) {
        return (bas * höjd) / 2;
    }
    
    public static double cirkelArea(double radie) {
        return Math.PI * radie * radie;
    }
}
```

**Viktiga koncept:**
- Alla metoder returnerar ett `double`-värde
- Resultatet av metoden kan sparas i en variabel och användas senare
- Resultatet av metoden kan också användas direkt i ett uttryck
- För cirkelarean används konstanten `Math.PI` från Java-biblioteket

## Lösning Övning 3: Scope

```java
public class ScopeÖvning {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        
        System.out.println("I main - a: " + a + ", b: " + b);
        
        testScope();
        
        // Lokal scope-demonstration
        if (a > 5) {
            int c = 30;
            System.out.println("I if-block - a: " + a + ", b: " + b + ", c: " + c);
        }
        // System.out.println(c); // Kompileringsfel - c finns inte här
        
        for (int i = 0; i < 3; i++) {
            int temp = a + i;
            System.out.println("I for-loop - i: " + i + ", temp: " + temp);
        }
        // System.out.println(i); // Kompileringsfel - i finns inte här
        // System.out.println(temp); // Kompileringsfel - temp finns inte här
    }
    
    public static void testScope() {
        // System.out.println(a); // Kompileringsfel - a finns inte här
        
        int x = 100;
        int y = 200;
        
        System.out.println("I testScope - x: " + x + ", y: " + y);
    }
}
```

**Viktiga koncept:**
- Variabler deklarerade i `main`-metoden är inte tillgängliga i `testScope`-metoden
- Variabler deklarerade i `testScope`-metoden är inte tillgängliga i `main`-metoden
- Variabler deklarerade i ett kodblock (t.ex. `if` eller `for`) är bara tillgängliga inom det blocket
- Man kan referera till variabler från "yttre" scope i ett "inre" scope, men inte tvärtom

## Lösning Övning 4: Metodkombination

```java
import java.util.Random;

public class ArrayMetoder {
    public static void main(String[] args) {
        // Skapa en array med slumpmässiga tal
        int[] minArray = skapaSlumpArray(10, 1, 100);
        
        // Skriv ut arrayen
        skrivUtArray(minArray);
        
        // Beräkna summan
        int summa = beräknaSumma(minArray);
        System.out.println("Summan av elementen: " + summa);
        
        // Hitta största värdet
        int störst = hittaStörsta(minArray);
        System.out.println("Största värdet: " + störst);
    }
    
    // Skapar och returnerar en array med slumpmässiga tal
    public static int[] skapaSlumpArray(int längd, int min, int max) {
        int[] array = new int[längd];
        Random rand = new Random();
        
        for (int i = 0; i < array.length; i++) {
            array[i] = rand.nextInt(max - min + 1) + min;
        }
        
        return array;
    }
    
    // Beräknar summan av värdena i en array
    public static int beräknaSumma(int[] array) {
        int summa = 0;
        
        for (int i = 0; i < array.length; i++) {
            summa += array[i];
        }
        
        return summa;
    }
    
    // Hittar det största värdet i en array
    public static int hittaStörsta(int[] array) {
        if (array.length == 0) {
            return Integer.MIN_VALUE; // Om arrayen är tom
        }
        
        int störst = array[0];
        
        for (int i = 1; i < array.length; i++) {
            if (array[i] > störst) {
                störst = array[i];
            }
        }
        
        return störst;
    }
    
    // Skriver ut innehållet i en array
    public static void skrivUtArray(int[] array) {
        System.out.print("Array: [");
        
        for (int i = 0; i < array.length; i++) {
            System.out.print(array[i]);
            
            if (i < array.length - 1) {
                System.out.print(", ");
            }
        }
        
        System.out.println("]");
    }
}
```

**Viktiga koncept:**
- Metoden `skapaSlumpArray` returnerar en hel array, inte bara ett enstaka värde
- Vi kan skicka arrays som parametrar till metoder
- Olika metoder kan fokusera på specifika uppgifter, vilket gör koden mer läsbar och återanvändbar
- Felhantering för särskilda fall (t.ex. tom array i `hittaStörsta`-metoden)

## Lösning Övning 5: Temperaturomvandlare

```java
import java.util.Scanner;

public class TemperaturOmvandlare {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Temperaturomvandlare");
        System.out.println("1. Celsius till Fahrenheit");
        System.out.println("2. Fahrenheit till Celsius");
        System.out.print("Välj alternativ (1 eller 2): ");
        
        int val = scanner.nextInt();
        
        if (val == 1) {
            System.out.print("Ange temperatur i Celsius: ");
            double celsius = scanner.nextDouble();
            double fahrenheit = celsiusTillFahrenheit(celsius);
            System.out.println(celsius + " °C = " + fahrenheit + " °F");
        } else if (val == 2) {
            System.out.print("Ange temperatur i Fahrenheit: ");
            double fahrenheit = scanner.nextDouble();
            double celsius = fahrenheitTillCelsius(fahrenheit);
            System.out.println(fahrenheit + " °F = " + celsius + " °C");
        } else {
            System.out.println("Ogiltigt val!");
        }
        
        scanner.close();
    }
    
    public static double celsiusTillFahrenheit(double celsius) {
        return (celsius * 9/5) + 32;
    }
    
    public static double fahrenheitTillCelsius(double fahrenheit) {
        return (fahrenheit - 32) * 5/9;
    }
}
```

**Viktiga koncept:**
- Metoder med tydligt definierat syfte gör koden mer läsbar
- Användarinput samlas i `main`-metoden
- Omvandlingslogiken är separerad i egna metoder
- Metoderna kan återanvändas var som helst i programmet

## Ytterligare utmaningar

För elever som vill ha mer utmaningar rekommenderas:

1. Ändra `ArrayMetoder` för att lägga till:
   - En metod som sorterar en array utan att använda Arrays.sort()
   - En metod som vänder på ordningen i en array
   - En metod som hittar medianen i en sorterad array

2. Utöka `TemperaturOmvandlare` för att också hantera:
   - Kelvin till och från Celsius
   - Fahrenheit till och från Kelvin

3. Skapa en metod som kontrollerar om en sträng är ett palindrom (läses likadant från båda håll)

4. Skapa en metod som omvandlar romerska siffror till heltal (t.ex. "XIV" till 14)