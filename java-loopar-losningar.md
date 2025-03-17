# Java Loopar - Övningslösningar

Detta dokument innehåller lösningar till övningarna från "Java för JavaScript-utvecklare - Loopar".

## Lösning Övning 1: Grundläggande For-loop

```java
public class TalUtskrift {
    public static void main(String[] args) {
        // Skriv ut talen 1 till 10 med for-loop
        for (int i = 1; i <= 10; i++) {
            System.out.println("Tal: " + i);
        }
    }
}
```

**Viktiga koncept:**
- Vi initierar `i` till 1
- Vi fortsätter loopen så länge `i` är mindre än eller lika med 10
- Vi ökar `i` med 1 för varje iteration

## Lösning Övning 2: Summer tal

```java
public class TalSummering {
    public static void main(String[] args) {
        int summa = 0;
        
        // Beräkna summan av talen 1 till 100
        for (int i = 1; i <= 100; i++) {
            summa += i;
        }
        
        System.out.println("Summan av talen 1 till 100 är: " + summa);
    }
}
```

**Viktiga koncept:**
- Vi initierar en summavariabel till 0
- I varje iteration lägger vi till det aktuella talet till summan
- Detta är ett vanligt mönster för att ackumulera värden

**Notera:** För detta specifika problem finns faktiskt en matematisk formel: summan av talen 1 till n är n(n+1)/2, så vi kunde också ha skrivit:

```java
int n = 100;
int summa = n * (n + 1) / 2;
System.out.println("Summan av talen 1 till 100 är: " + summa);
```

Men det missar poängen med loopövningen!

## Lösning Övning 3: Fakultetsberäkning

```java
public class Fakultet {
    public static void main(String[] args) {
        int n = 5; // Testa med olika värden
        
        // Beräkna n!
        long resultat = 1; // Använd long för att hantera större fakulteter
        
        for (int i = 1; i <= n; i++) {
            resultat *= i;
        }
        
        System.out.println(n + "! = " + resultat);
    }
}
```

**Viktiga koncept:**
- Vi initierar resultatet till 1 (inte 0, eftersom vi multiplicerar)
- Vi använder datatypen `long` för att hantera större tal (men den överskrids fortfarande för n > 20)
- En `for`-loop är lämplig här eftersom vi vet exakt hur många iterationer vi behöver
- Att beräkna fakulteter är en vanlig användning för loopar

## Lösning Övning 4: Multiplikationstabell

```java
public class Multiplikationstabell {
    public static void main(String[] args) {
        int storlek = 10;
        
        // Skriv ut rubrik
        System.out.println("Multiplikationstabell 1-" + storlek + ":");
        
        // Skriv ut övre raden med kolumnnummer
        System.out.print("   |");
        for (int i = 1; i <= storlek; i++) {
            System.out.printf("%4d", i);
        }
        System.out.println();
    }
}

/**
 * Viktiga koncept:
 * - Vi visar två lösningar: en med array och en utan
 * - Array-lösningen sparar alla värden, vilket är användbart om vi behöver alla värden senare
 * - Lösningen utan array använder bara tre variabler och är mer minneseffektiv
 * - Vi hanterar specialfallen för de första två talen i båda lösningarna
 */

## Lösning Övning 10: Lottery Number Generator

```java
import java.util.Random;
import java.util.Arrays;

public class LotteryGenerator {
    public static void main(String[] args) {
        int[] lottoNumbers = new int[7];
        Random random = new Random();
        
        // Generera 7 unika tal
        int count = 0;
        while (count < lottoNumbers.length) {
            // Generera ett slumpmässigt tal mellan 1 och 35
            int number = random.nextInt(35) + 1;
            
            // Kontrollera om talet redan finns i arrayen
            boolean exists = false;
            for (int i = 0; i < count; i++) {
                if (lottoNumbers[i] == number) {
                    exists = true;
                    break;
                }
            }
            
            // Om talet inte finns, lägg till det i arrayen
            if (!exists) {
                lottoNumbers[count] = number;
                count++;
            }
        }
        
        // Sortera talen i stigande ordning
        Arrays.sort(lottoNumbers);
        
        // Skriv ut lottotalen
        System.out.print("Dagens lottonummer: ");
        for (int i = 0; i < lottoNumbers.length; i++) {
            System.out.print(lottoNumbers[i]);
            if (i < lottoNumbers.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println();
        
        // Alternativ utskrift med for-each
        System.out.print("Samma nummer med for-each: ");
        boolean first = true;
        for (int number : lottoNumbers) {
            if (!first) {
                System.out.print(", ");
            } else {
                first = false;
            }
            System.out.print(number);
        }
        System.out.println();
    }
}
```

**Viktiga koncept:**
- Vi använder en `while`-loop för att fylla vår array med unika tal
- Vi kontrollerar om ett tal redan finns innan vi lägger till det
- Vi använder `Arrays.sort()` för att sortera talen (importerad från `java.util.Arrays`)
- Vi visar två sätt att skriva ut arrayen: med traditionell for-loop och med for-each
- För for-each-loopen visar vi ett trick för att hantera kommatecken utan att lägga till ett extra i slutet
        
        // Skriv ut horisontell avgränsare
        System.out.print("---+");
        for (int i = 1; i <= storlek; i++) {
            System.out.print("----");
        }
        System.out.println();
        
        // Skriv ut multiplikationstabellen med nestade loopar
        for (int rad = 1; rad <= storlek; rad++) {
            // Skriv ut radnummer
            System.out.printf("%2d |", rad);
            
            // Skriv ut produkterna på raden
            for (int kolumn = 1; kolumn <= storlek; kolumn++) {
                System.out.printf("%4d", rad * kolumn);
            }
            
            // Ny rad efter varje tabellrad
            System.out.println();
        }
    }
}
```

**Viktiga koncept:**
- Vi använder nestade loopar: en yttre loop för raderna och en inre loop för kolumnerna
- Vi använder `printf` för att formatera utskriften med jämn utfyllnad
- Detta är ett bra exempel på hur nestade loopar kan användas för att generera tabeller

## Lösning Övning 5: Primtalstest

```java
public class Primtalstest {
    public static void main(String[] args) {
        int tal = 17; // Testa med olika värden
        
        boolean ärPrimtal = true;
        
        // 0 och 1 är inte primtal
        if (tal <= 1) {
            ärPrimtal = false;
        } else {
            // Vi behöver bara kontrollera upp till roten av talet
            for (int i = 2; i <= Math.sqrt(tal); i++) {
                if (tal % i == 0) {
                    ärPrimtal = false;
                    break; // Vi kan avsluta loopen så fort vi hittar en delare
                }
            }
        }
        
        if (ärPrimtal) {
            System.out.println(tal + " är ett primtal.");
        } else {
            System.out.println(tal + " är inte ett primtal.");
        }
    }
}
```

**Viktiga koncept:**
- Vi använder en flaggvariabel `ärPrimtal` som initieras till `true`
- Vi hanterar specialfallen 0 och 1 (som inte är primtal) med en if-sats
- Vi testar bara möjliga delare upp till roten av talet, vilket är en matematisk optimering
- Vi använder `break` för att avsluta loopen så fort vi hittar en delare, vilket är mer effektivt

## Lösning Övning 6: Array-summering

```java
public class ArraySummering {
    public static void main(String[] args) {
        int[] siffror = {5, 10, 15, 20, 25};
        
        int summa = 0;
        
        // Version 1: med traditionell for-loop och index
        for (int i = 0; i < siffror.length; i++) {
            summa += siffror[i];
        }
        
        System.out.println("Summa (med traditionell for-loop): " + summa);
        
        // Version 2: med for-each loop (mer koncis)
        summa = 0; // Återställ summan
        for (int tal : siffror) {
            summa += tal;
        }
        
        System.out.println("Summa (med for-each loop): " + summa);
    }
}
```

**Viktiga koncept:**
- Vi visar både indexbaserad for-loop och for-each loop för att illustrera skillnaden
- For-each loopen är mer koncis och läsbar när vi bara behöver läsa värdena utan att ändra dem i arrayen
- För enkla operationer som summering är for-each loopen ofta att föredra
- Notera att om vi hade velat ändra värdena i arrayen (t.ex. dubblera varje värde) skulle vi behövt använda den traditionella for-loopen med index

## Lösning Övning 7: Palindromtest

```java
public class Palindromtest {
    public static void main(String[] args) {
        String originalText = "A man, a plan, a canal, Panama!";
        
        // Steg 1: Konvertera till gemener och ta bort alla tecken som inte är bokstäver eller siffror
        String rengjordText = originalText.toLowerCase().replaceAll("[^a-z0-9]", "");
        
        // Steg 2: Kontrollera om rengjordText är ett palindrom
        boolean ärPalindrom = true;
        int längd = rengjordText.length();
        
        for (int i = 0; i < längd / 2; i++) {
            if (rengjordText.charAt(i) != rengjordText.charAt(längd - 1 - i)) {
                ärPalindrom = false;
                break;
            }
        }
        
        // Alternativ lösning med StringBuilder
        String omvändText = new StringBuilder(rengjordText).reverse().toString();
        boolean ärPalindromAlternativ = rengjordText.equals(omvändText);
        
        // Skriv ut resultaten
        System.out.println("Original text: " + originalText);
        System.out.println("Rengjord text: " + rengjordText);
        System.out.println("Är palindrom (manuell kontroll): " + ärPalindrom);
        System.out.println("Är palindrom (med StringBuilder): " + ärPalindromAlternativ);
    }
}
```

**Viktiga koncept:**
- Vi visar två olika metoder för att kontrollera om en sträng är ett palindrom
- Metod 1: Jämför tecken från början och slutet och möts i mitten
- Metod 2: Använder StringBuilder för att vända på strängen och jämför
- Vi använder regex `replaceAll("[^a-z0-9]", "")` för att ta bort alla tecken som inte är bokstäver eller siffror
- Båda metoderna är giltiga, men den första är mer effektiv eftersom den kan avsluta tidigt om den hittar en skillnad

## Lösning Övning 8: Mönstergenerering

```java
public class Mönstergenerering {
    public static void main(String[] args) {
        int höjd = 5; // Testa med olika värden
        
        // Lösning 1: Enkel triangel
        System.out.println("Mönster 1:");
        for (int i = 1; i <= höjd; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Lösning 2: Alternativ med StringBuilder
        System.out.println("\nMönster 2:");
        for (int i = 1; i <= höjd; i++) {
            StringBuilder rad = new StringBuilder();
            for (int j = 1; j <= i; j++) {
                rad.append("*");
            }
            System.out.println(rad.toString());
        }
        
        // Bonus: Omvänd triangel
        System.out.println("\nBonus: Omvänd triangel");
        for (int i = höjd; i >= 1; i--) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Bonus: Centrerad triangel (pyramid)
        System.out.println("\nBonus: Centrerad triangel (pyramid)");
        for (int i = 1; i <= höjd; i++) {
            // Skriv ut mellanslag för att centrera
            for (int j = 1; j <= höjd - i; j++) {
                System.out.print(" ");
            }
            
            // Skriv ut stjärnor
            for (int k = 1; k <= 2 * i - 1; k++) {
                System.out.print("*");
            }
            
            System.out.println();
        }
    }
}
```

**Viktiga koncept:**
- Nestade loopar används för att skapa 2D-mönster
- För varje rad (yttre loop) skriver vi ut ett varierande antal stjärnor (inre loop)
- Vi inkluderade även några bonusmönster för att visa variationer
- Den centrerade triangeln är mer komplex och kräver tre komponenter: mellanslag, stjärnor och radbrytning

## Lösning Övning 9: Fibonacci-sekvens

```java
public class Fibonacci {
    public static void main(String[] args) {
        int n = 10; // Antal termer att visa
        
        // Lösning med en loop
        long[] fib = new long[n];
        
        // Hantera specialfallen för de första två talen
        if (n >= 1) {
            fib[0] = 0;
        }
        
        if (n >= 2) {
            fib[1] = 1;
        }
        
        // Beräkna resten av sekvensen
        for (int i = 2; i < n; i++) {
            fib[i] = fib[i-1] + fib[i-2];
        }
        
        // Skriv ut sekvensen
        System.out.print("Fibonacci-sekvens med " + n + " termer: ");
        for (int i = 0; i < n; i++) {
            System.out.print(fib[i]);
            if (i < n - 1) {
                System.out.print(", ");
            }
        }
        System.out.println();
        
        // Alternativ lösning utan array (mer minneseffektiv)
        System.out.print("Alternativ lösning: ");
        long prev = 0, curr = 1, next;
        
        System.out.print(prev);
        
        if (n > 1) {
            System.out.print(", " + curr);
            
            for (int i = 2; i < n; i++) {
                next = prev + curr;
                System.out.print(", " + next);
                prev = curr;
                curr = next;
            }
        }
        System.out.println();