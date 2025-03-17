# Java Metoder Del 2 - Övningslösningar

Detta dokument innehåller lösningar till övningarna från "Java för JavaScript-utvecklare - Metoder Del 2".

## Lösning Övning 1: Method Overloading med Miniräknare

```java
public class Miniräknare {
    public static void main(String[] args) {
        // Testa olika versioner av beräkna-metoden
        System.out.println("10 + 5 = " + beräkna(10, 5, '+'));
        System.out.println("10 - 5 = " + beräkna(10, 5, '-'));
        System.out.println("10 * 5 = " + beräkna(10, 5, '*'));
        System.out.println("10 / 5 = " + beräkna(10, 5, '/'));
        
        System.out.println("10.5 + 5.2 = " + beräkna(10.5, 5.2, '+'));
        
        System.out.println("10 + 5 (automatisk addition) = " + beräkna(10, 5));
        
        int[] talArray = {1, 2, 3, 4, 5};
        System.out.println("Summan av {1, 2, 3, 4, 5} = " + beräkna(talArray));
    }
    
    // Version 1: två integers och en operator
    public static int beräkna(int tal1, int tal2, char operator) {
        switch (operator) {
            case '+':
                return tal1 + tal2;
            case '-':
                return tal1 - tal2;
            case '*':
                return tal1 * tal2;
            case '/':
                if (tal2 != 0) {
                    return tal1 / tal2;
                } else {
                    System.out.println("Fel: Division med noll");
                    return 0;
                }
            default:
                System.out.println("Ogiltig operator: " + operator);
                return 0;
        }
    }
    
    // Version 2: två doubles och en operator
    public static double beräkna(double tal1, double tal2, char operator) {
        switch (operator) {
            case '+':
                return tal1 + tal2;
            case '-':
                return tal1 - tal2;
            case '*':
                return tal1 * tal2;
            case '/':
                if (tal2 != 0) {
                    return tal1 / tal2;
                } else {
                    System.out.println("Fel: Division med noll");
                    return 0;
                }
            default:
                System.out.println("Ogiltig operator: " + operator);
                return 0;
        }
    }
    
    // Version 3: två integers, automatisk addition
    public static int beräkna(int tal1, int tal2) {
        return tal1 + tal2;
    }
    
    // Version 4: array av integers, summera alla värden
    public static int beräkna(int[] tal) {
        int summa = 0;
        for (int värde : tal) {
            summa += värde;
        }
        return summa;
    }
}
```

**Viktiga koncept:**
- Vi har fyra olika versioner av metoden `beräkna`, var och en med en unik parameterlista
- Java väljer rätt metod beroende på antal och typ av parametrar som skickas in
- Vi kan hantera olika datatyper (int, double, array) med samma metodnamn
- Switch-satser används för att hantera olika operatorer

## Lösning Övning 2: Method Overloading med Formatering

```java
import java.text.NumberFormat;
import java.util.Locale;

public class Formaterare {
    public static void main(String[] args) {
        // Testa olika versioner av formatera-metoden
        int summa = 1234567;
        System.out.println("Formaterad summa: " + formatera(summa));
        
        String namn = "John Doe";
        System.out.println("Formaterat namn: " + formatera(namn));
        
        String telefon = "0701234567";
        System.out.println("Formaterat telefonnummer: " + formatera(telefon));
    }
    
    // Version 1: Formatera heltalssumma med tusentalsavgränsare
    public static String formatera(int summa) {
        // Använd NumberFormat för att formatera tal med tusentalsavgränsare
        NumberFormat formatter = NumberFormat.getNumberInstance(new Locale("sv", "SE"));
        return formatter.format(summa);
        
        // Alternativ implementation utan att använda NumberFormat:
        // StringBuilder sb = new StringBuilder();
        // String talSträng = Integer.toString(summa);
        // int längd = talSträng.length();
        // 
        // for (int i = 0; i < längd; i++) {
        //     sb.append(talSträng.charAt(i));
        //     // Lägg till tusentalsavgränsare om:
        //     // - Vi inte är på sista siffran
        //     // - Antalet återstående siffror är delbart med 3
        //     if ((längd - i - 1) % 3 == 0 && i < längd - 1) {
        //         sb.append(" ");
        //     }
        // }
        // return sb.toString();
    }
    
    // Version 2: Formatera namn från "Förnamn Efternamn" till "Efternamn, Förnamn"
    public static String formatera(String namn) {
        // Anta att namnet är i formatet "Förnamn Efternamn"
        int mellanrumsIndex = namn.lastIndexOf(' ');
        if (mellanrumsIndex != -1) {
            String förnamn = namn.substring(0, mellanrumsIndex);
            String efternamn = namn.substring(mellanrumsIndex + 1);
            return efternamn + ", " + förnamn;
        } else {
            // Om det inte finns något mellanrum, returnera namnet som det är
            return namn;
        }
    }
    
    // Version 3: Formatera telefonnummer
    public static String formatera(String telefonnummer) {
        // Rensa bort icke-numeriska tecken
        String rensat = telefonnummer.replaceAll("[^0-9]", "");
        
        // Om det är ett svenskt mobilnummer (10 siffror) formatera som 070-123 45 67
        if (rensat.length() == 10) {
            return rensat.substring(0, 3) + "-" + 
                   rensat.substring(3, 6) + " " + 
                   rensat.substring(6, 8) + " " + 
                   rensat.substring(8);
        }
        // Om det är ett svenskt fast nummer (9 siffror) formatera som 08-123 456 78
        else if (rensat.length() == 9) {
            return rensat.substring(0, 2) + "-" + 
                   rensat.substring(2, 5) + " " + 
                   rensat.substring(5, 7) + " " + 
                   rensat.substring(7);
        }
        // Annars, gör ett enkelt format med bindestreck efter var tredje siffra
        else {
            StringBuilder formaterat = new StringBuilder();
            for (int i = 0; i < rensat.length(); i++) {
                formaterat.append(rensat.charAt(i));
                if ((i + 1) % 3 == 0 && i < rensat.length() - 1) {
                    formaterat.append("-");
                }
            }
            return formaterat.toString();
        }
    }
}
```

**Viktiga koncept:**
- Alla tre metoder har samma namn `formatera` men olika parametertyper
- Vi använder flera tekniker för strängmanipulation
- Vi visar två olika approacher för att formatera tal (med och utan NumberFormat)
- För telefonformatering hanterar vi olika typer av telefonnummer

## Lösning Övning 3: Enkel Rekursion

```java
public class RekursionsÖvningar {
    public static void main(String[] args) {
        int n = 5;
        System.out.println("Summan av 1 till " + n + " är: " + summa(n));
        
        // Testa med några fler värden
        System.out.println("Summan av 1 till 1 är: " + summa(1));
        System.out.println("Summan av 1 till 10 är: " + summa(10));
    }
    
    // Rekursiv metod för att beräkna summan av 1 till n
    public static int summa(int n) {
        // Basfall: om n är 1, är summan 1
        if (n <= 1) {
            return n;
        }
        // Rekursivt fall: summan av 1 till n är n + summan av 1 till (n-1)
        else {
            return n + summa(n - 1);
        }
    }
}
```

**Viktiga koncept:**
- Metoden `summa` anropar sig själv med ett mindre värde (n-1)
- Basfallet (n <= 1) förhindrar oändlig rekursion
- För n = 5 beräknas: 5 + summa(4) = 5 + (4 + summa(3)) = 5 + 4 + (3 + summa(2)) = 5 + 4 + 3 + (2 + summa(1)) = 5 + 4 + 3 + 2 + 1 = 15

## Lösning Övning 4: Rekursiv Palindromkontroll

```java
public class Palindrom {
    public static void main(String[] args) {
        String[] testSträngar = {"anna", "palindrom", "level", "java", "radar"};
        
        for (String s : testSträngar) {
            System.out.println(s + " är palindrom: " + ärPalindrom(s));
        }
    }
    
    // Rekursiv metod för att kontrollera om en sträng är ett palindrom
    public static boolean ärPalindrom(String sträng) {
        // Basfall 1: En tom sträng eller en sträng med ett tecken är ett palindrom
        if (sträng.length() <= 1) {
            return true;
        }
        
        // Kontrollera om det första och sista tecknet är samma
        char första = sträng.charAt(0);
        char sista = sträng.charAt(sträng.length() - 1);
        
        if (första != sista) {
            return false;  // Om tecknen inte matchar, är det inte ett palindrom
        }
        
        // Rekursivt fall: kontrollera om resten av strängen (utan första och sista tecknet) är ett palindrom
        String resten = sträng.substring(1, sträng.length() - 1);
        return ärPalindrom(resten);
    }
}
```

**Alternativ lösning med hjälpmetod:**

```java
public class Palindrom {
    public static void main(String[] args) {
        String[] testSträngar = {"anna", "palindrom", "level", "java", "radar"};
        
        for (String s : testSträngar) {
            System.out.println(s + " är palindrom: " + ärPalindrom(s));
        }
    }
    
    // Publik metod som användaren anropar
    public static boolean ärPalindrom(String sträng) {
        // Konvertera till små bokstäver och ta bort icke-alfabetiska tecken
        String rensad = sträng.toLowerCase().replaceAll("[^a-zåäö0-9]", "");
        return ärPalindromRekursiv(rensad, 0, rensad.length() - 1);
    }
    
    // Privat hjälpmetod som implementerar rekursionen
    private static boolean ärPalindromRekursiv(String sträng, int start, int slut) {
        // Basfall: Om vi har kontrollerat alla tecken eller kommit till mitten
        if (start >= slut) {
            return true;
        }
        
        // Om tecknen på de jämförda positionerna inte matchar
        if (sträng.charAt(start) != sträng.charAt(slut)) {
            return false;
        }
        
        // Rekursivt fall: kontrollera nästa par av tecken
        return ärPalindromRekursiv(sträng, start + 1, slut - 1);
    }
}
```

**Viktiga koncept:**
- Den första lösningen skapar nya strängar i varje rekursivt anrop med `substring`
- Den alternativa lösningen är mer effektiv eftersom den inte skapar nya strängar - den håller bara reda på indexen
- Båda lösningarna jämför de yttersta tecknen och arbetar sig inåt
- Basfallet är när det finns 0 eller 1 tecken kvar att kontrollera

## Lösning Övning 5: Binärsökning (Rekursiv)

```java
public class BinärSökning {
    public static void main(String[] args) {
        int[] sortedArray = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
        
        // Testa med några olika söktal
        int[] sökTal = {23, 5, 91, 10}; // 10 finns inte i arrayen
        
        for (int tal : sökTal) {
            int index = binärSök(sortedArray, tal, 0, sortedArray.length - 1);
            
            if (index != -1) {
                System.out.println(tal + " finns på index " + index);
            } else {
                System.out.println(tal + " finns inte i arrayen");
            }
        }
    }
    
    // Rekursiv binärsökningsmetod
    public static int binärSök(int[] array, int sökTal, int lågIndex, int