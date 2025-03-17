# Java Villkorssatser - Övningslösningar

Detta dokument innehåller lösningar till övningarna från "Java för JavaScript-utvecklare - Villkorssatser".

## Lösning Övning 1: Ålderskontroll

```java
public class ÅldersKontroll {
    public static void main(String[] args) {
        int ålder = 25; // Testa med olika värden
        
        if (ålder < 13) {
            System.out.println("Du är ett barn");
        } else if (ålder >= 13 && ålder <= 19) {
            System.out.println("Du är en tonåring");
        } else if (ålder >= 20 && ålder <= 64) {
            System.out.println("Du är en vuxen");
        } else {
            System.out.println("Du är en pensionär");
        }
    }
}
```

**Viktiga koncept:**
- Vi använder `if`, `else if` och `else` för att kontrollera olika åldersintervall
- Villkoren kontrolleras i ordning, så vi behöver bara kolla övre gränsen i varje intervall (förutom det första)
- Vi kunde också ha skrivit `else if (ålder <= 19)` i det andra villkoret, eftersom vi redan vet att ålder >= 13 från det första villkoret

## Lösning Övning 2: BetygsKalkylator

```java
public class BetygsKalkylator {
    public static void main(String[] args) {
        int poäng = 85; // Testa med olika värden
        
        if (poäng >= 90 && poäng <= 100) {
            System.out.println("Betyg: A");
        } else if (poäng >= 80 && poäng <= 89) {
            System.out.println("Betyg: B");
        } else if (poäng >= 70 && poäng <= 79) {
            System.out.println("Betyg: C");
        } else if (poäng >= 60 && poäng <= 69) {
            System.out.println("Betyg: D");
        } else if (poäng >= 0 && poäng <= 59) {
            System.out.println("Betyg: F");
        } else {
            System.out.println("Ogiltig poäng. Ange ett värde mellan 0 och 100.");
        }
    }
}
```

**Alternativ lösning med förenklad logik:**

```java
public class BetygsKalkylator {
    public static void main(String[] args) {
        int poäng = 85; // Testa med olika värden
        
        if (poäng < 0 || poäng > 100) {
            System.out.println("Ogiltig poäng. Ange ett värde mellan 0 och 100.");
        } else if (poäng >= 90) {
            System.out.println("Betyg: A");
        } else if (poäng >= 80) {
            System.out.println("Betyg: B");
        } else if (poäng >= 70) {
            System.out.println("Betyg: C");
        } else if (poäng >= 60) {
            System.out.println("Betyg: D");
        } else {
            System.out.println("Betyg: F");
        }
    }
}
```

**Viktiga koncept:**
- I den alternativa lösningen kontrollerar vi först om poängen är giltig
- I den första lösningen kontrollerar vi både under- och övergränsen i varje intervall
- I den andra lösningen utnyttjar vi att villkoren kontrolleras i ordning, så vi behöver bara kontrollera den undre gränsen i varje intervall

## Lösning Övning 3: Miniräknare

```java
public class Miniräknare {
    public static void main(String[] args) {
        double tal1 = 10.5;
        double tal2 = 5.2;
        char operator = '+'; // Testa med olika operatorer: '+', '-', '*', '/'
        
        System.out.println("Implementering med if-satser:");
        
        if (operator == '+') {
            System.out.println(tal1 + " + " + tal2 + " = " + (tal1 + tal2));
        } else if (operator == '-') {
            System.out.println(tal1 + " - " + tal2 + " = " + (tal1 - tal2));
        } else if (operator == '*') {
            System.out.println(tal1 + " * " + tal2 + " = " + (tal1 * tal2));
        } else if (operator == '/') {
            if (tal2 != 0) {
                System.out.println(tal1 + " / " + tal2 + " = " + (tal1 / tal2));
            } else {
                System.out.println("Kan inte dividera med noll!");
            }
        } else {
            System.out.println("Ogiltig operator. Använd +, -, * eller /");
        }
        
        System.out.println("\nImplementering med switch:");
        
        switch (operator) {
            case '+':
                System.out.println(tal1 + " + " + tal2 + " = " + (tal1 + tal2));
                break;
            case '-':
                System.out.println(tal1 + " - " + tal2 + " = " + (tal1 - tal2));
                break;
            case '*':
                System.out.println(tal1 + " * " + tal2 + " = " + (tal1 * tal2));
                break;
            case '/':
                if (tal2 != 0) {
                    System.out.println(tal1 + " / " + tal2 + " = " + (tal1 / tal2));
                } else {
                    System.out.println("Kan inte dividera med noll!");
                }
                break;
            default:
                System.out.println("Ogiltig operator. Använd +, -, * eller /");
                break;
        }
    }
}
```

**Viktiga koncept:**
- Vi visar implementering med både if-satser och switch för att jämföra
- I båda fallen hanterar vi division med noll som ett specialfall
- För switch-satsen måste vi använda `break` efter varje case

## Lösning Övning 4: VeckoplaneringsApp

```java
public class VeckoPlaneringApp {
    public static void main(String[] args) {
        int dag = 5; // 1 = Måndag, 7 = Söndag
        
        switch (dag) {
            case 1:
                System.out.println("Måndag: Skola/Jobb");
                break;
            case 2:
                System.out.println("Tisdag: Gym");
                break;
            case 3:
                System.out.println("Onsdag: Studiecirkel");
                break;
            case 4:
                System.out.println("Torsdag: Ledig kväll");
                break;
            case 5:
                System.out.println("Fredag: Socialt umgänge");
                break;
            case 6:
            case 7:
                System.out.println("Helg: Vila och återhämtning");
                break;
            default:
                System.out.println("Ogiltig dag. Ange ett värde mellan 1 och 7.");
                break;
        }
    }
}
```

**Viktiga koncept:**
- Vi använder fall-through för helgen (lördag och söndag)
- Vi har en default case för att hantera ogiltiga värden

## Lösning Övning 5: BMI-Kalkylator

```java
public class BMIKalkylator {
    public static void main(String[] args) {
        double vikt = 70.0; // kg
        double längd = 1.75; // m
        
        // Beräkna BMI
        double bmi = vikt / (längd * längd);
        
        System.out.println("Din vikt: " + vikt + " kg");
        System.out.println("Din längd: " + längd + " m");
        System.out.println("Ditt BMI: " + bmi);
        
        // Tolka BMI
        if (bmi < 18.5) {
            System.out.println("Tolkning: Undervikt");
        } else if (bmi >= 18.5 && bmi < 25) {
            System.out.println("Tolkning: Normalvikt");
        } else if (bmi >= 25 && bmi < 30) {
            System.out.println("Tolkning: Övervikt");
        } else {
            System.out.println("Tolkning: Fetma");
        }
    }
}
```

**Viktiga koncept:**
- Vi beräknar BMI enligt formeln: vikt (kg) / (längd (m) * längd (m))
- Vi använder if-else-satser för att tolka BMI-värdet enligt givna intervall

## Lösning Övning 6: Skottår

```java
public class Skottår {
    public static void main(String[] args) {
        int år = 2024; // Testa med olika årtal
        
        // Ett år är skottår om det är delbart med 4
        // Men inte om det är delbart med 100, såvida det inte också är delbart med 400
        
        boolean ärSkottår = false;
        
        if ((år % 4 == 0 && år % 100 != 0) || (år % 400 == 0)) {
            ärSkottår = true;
        }
        
        if (ärSkottår) {
            System.out.println(år + " är ett skottår.");
        } else {
            System.out.println(år + " är inte ett skottår.");
        }
    }
}
```

**Alternativ lösning:**

```java
public class Skottår {
    public static void main(String[] args) {
        int år = 2024; // Testa med olika årtal
        
        boolean ärSkottår = false;
        
        if (år % 4 == 0) {
            if (år % 100 == 0) {
                if (år % 400 == 0) {
                    ärSkottår = true;
                } else {
                    ärSkottår = false;
                }
            } else {
                ärSkottår = true;
            }
        } else {
            ärSkottår = false;
        }
        
        System.out.println(år + (ärSkottår ? " är" : " är inte") + " ett skottår.");
    }
}
```

**Viktiga koncept:**
- I den första lösningen använder vi ett sammansatt boolskt uttryck med OCH och ELLER
- I den alternativa lösningen använder vi nestade if-satser
- Den första lösningen är kortare och ofta lättare att förstå
- I sista utskriften använder vi en ternär operator för att välja rätt text

## Lösning Övning 7: Förbättrad Miniräknare med Scanner

```java
import java.util.Scanner;

public class FörbättradMiniräknare {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enkel miniräknare");
        System.out.println("------------------");
        
        // Läs in första talet
        System.out.print("Ange första talet: ");
        double tal1 = scanner.nextDouble();
        
        // Läs in operatör
        System.out.print("Ange operatör (+, -, *, /): ");
        char operator = scanner.next().charAt(0);
        
        // Läs in andra talet
        System.out.print("Ange andra talet: ");
        double tal2 = scanner.nextDouble();
        
        // Utför beräkning
        switch (operator) {
            case '+':
                System.out.println("Resultat: " + tal1 + " + " + tal2 + " = " + (tal1 + tal2));
                break;
            case '-':
                System.out.println("Resultat: " + tal1 + " - " + tal2 + " = " + (tal1 - tal2));
                break;
            case '*':
                System.out.println("Resultat: " + tal1 + " * " + tal2 + " = " + (tal1 * tal2));
                break;
            case '/':
                if (tal2 != 0) {
                    System.out.println("Resultat: " + tal1 + " / " + tal2 + " = " + (tal1 / tal2));
                } else {
                    System.out.println("Fel: Kan inte dividera med noll!");
                }
                break;
            default:
                System.out.println("Fel: Ogiltig operator. Använd +, -, * eller /");
                break;
        }
        
        scanner.close();
    }
}
```

**Viktiga koncept:**
- Vi använder Scanner för att läsa in användarinput
- För att läsa en char använder vi `scanner.next().charAt(0)` eftersom Scanner inte har en direkt metod för chars
- Vi hanterar specialfallet division med noll
- Vi stänger Scanner när vi inte behöver den längre

## Lösning Övning 8: KärleksKalkylator

```java
public class KärleksKalkylator {
    public static void main(String[] args) {
        String namn1 = "Alice";
        String namn2 = "Bob";
        
        // Konvertera till gemener för att ignorera skiftläge
        String name1Lower = namn1.toLowerCase();
        String name2Lower = namn2.toLowerCase();
        
        // Räkna gemensamma bokstäver
        int gemensamma = 0;
        for (int i = 0; i < name1Lower.length(); i++) {
            char c = name1Lower.charAt(i);
            if (name2Lower.indexOf(c) != -1) {
                gemensamma++;
            }
        }
        
        // Beräkna kärleksprocent baserat på längd och gemensamma bokstäver
        int totalLängd = namn1.length() + namn2.length();
        int kärleksprocent = (gemensamma * 100) / totalLängd;
        
        // Begränsa procenttalet till 100
        if (kärleksprocent > 100) {
            kärleksprocent = 100;
        }
        
        // Skriv ut resultat med ternära operatorer
        System.out.println(namn1 + " + " + namn2 + " = " + kärleksprocent + "% kärlek");
        
        String meddelande = (kärleksprocent >= 80) ? "Perfekt match!" :
                           (kärleksprocent >= 60) ? "Mycket bra match!" :
                           (kärleksprocent >= 40) ? "Ganska bra match." :
                           (kärleksprocent >= 20) ? "Kanske bara vänner." :
                           "Inte en bra match.";
        
        System.out.println(meddelande);
    }
}