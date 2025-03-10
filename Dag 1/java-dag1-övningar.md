# Java Dag 1 - Grundläggande övningar

Dessa övningar fokuserar på de allra första grunderna i Java: variabler, utskrift, operatorer och string-manipulering. Allt hålls inom main-metoden för att hålla det enkelt i början.

## Att komma igång
För varje övning:
1. Skapa ett nytt Projekt i IntelliJ och checka i 'Add sample code'
2. Utgå från startmallen som visas
3. Skriv din kod enligt uppgiftbeskrivningen
4. Spara och kör programmet för att se ditt resultat

## Del 1: Variabler och utskrift

### Övning 1.1: Ditt första Java-program

**Vad du lär dig:** Att skriva ut text i konsolen

**Startmall:**
```java
public class HejVarlden {
    public static void main(String[] args) {
        // Skriv din kod här
    }
}
```

**Din uppgift:**
1. Skriv kod för att skriva ut "Hej världen!" i konsolen
2. Lägg till kod för att skriva ut ditt namn på en ny rad
3. Skriv ut din favoritfärg på ytterligare en rad

### Övning 1.2: Produktvariabler

**Vad du lär dig:** Att definiera variabler av olika typer

**Startmall:**
```java
public class ProduktVariabler {
    public static void main(String[] args) {
        // Definiera dina variabler här
        
        // Skriv ut variablerna här
    }
}
```

**Din uppgift:**
1. Definiera variabeln `String produktNamn` med namnet på en produkt
2. Definiera variabeln `int pris` med ett heltalspris
3. Definiera variabeln `boolean finnsILager` som anger om produkten finns i lager
4. Definiera variabeln `double vikt` med produktens vikt i kg
5. Skriv ut all produktinformation på separata rader med beskrivande text

### Övning 1.3: Produktbeskrivning

**Vad du lär dig:** Att arbeta med olika datatyper

**Startmall:**
```java
public class Produktinfo {
    public static void main(String[] args) {
        // Definiera variabler för en produkt
        
        // Skriv ut en formaterad produktbeskrivning
    }
}
```

**Din uppgift:**
1. Skapa variabler för produktnamn, pris, storlek (som en char), färg, vikt och lagerstatus
2. Skriv ut en prydlig produktbeskrivning med rubrik och all information
3. Testa att ändra värdena och se hur utskriften ändras

## Del 2: Operatorer

### Övning 2.1: Enkla beräkningar

**Vad du lär dig:** Att använda matematiska operatorer

**Startmall:**
```java
public class PrisBerakning {
    public static void main(String[] args) {
        int pris = 100;
        int antal = 3;
        
        // Beräkna totalpriser och skriv ut resultaten
    }
}
```

**Din uppgift:**
1. Beräkna och skriv ut det totala priset (pris × antal)
2. Beräkna och skriv ut vad det kostar att köpa 2, 3 och 4 produkter
3. Beräkna och skriv ut vad genomsnittspriset blir om du köper 3 produkter

### Övning 2.2: Moms och rabatt

**Vad du lär dig:** Mer om matematiska operatorer och typkonvertering

**Startmall:**
```java
public class MomsBerakning {
    public static void main(String[] args) {
        int prisUtanMoms = 100;
        
        // Beräkna pris med moms och rabatt
        // Skriv ut resultaten
    }
}
```

**Din uppgift:**
1. Beräkna momsen (25% av priset utan moms)
2. Beräkna totalpriset med moms
3. Beräkna en rabatt på 10% av totalpriset
4. Beräkna slutpriset efter rabatt
5. Skriv ut alla dessa värden med beskrivande text

### Övning 2.3: Lagerhantering

**Vad du lär dig:** Att använda inkrement- och dekrementoperatorer

**Startmall:**
```java
public class Lagerhantering {
    public static void main(String[] args) {
        int lagerAntal = 10;
        
        System.out.println("Ursprungligt lagerantal: " + lagerAntal);
        
        // Ändra lagersaldo och skriv ut resultaten
    }
}
```

**Din uppgift:**
1. Öka lagervärdet med 1 genom att använda inkrement-operatorn (`++`)
2. Skriv ut det nya lagervärdet
3. Minska lagervärdet med 1 genom att använda dekrement-operatorn (`--`)
4. Skriv ut det nya lagervärdet
5. Lägg till 5 enheter till lagret med hjälp av `+=` operatorn
6. Skriv ut det nya lagervärdet
7. Ta bort 3 enheter från lagret med hjälp av `-=` operatorn
8. Skriv ut det slutliga lagervärdet

## Del 3: String-manipulering

### Övning 3.1: Grundläggande string-operationer

**Vad du lär dig:** Att manipulera text med string-metoder

**Startmall:**
```java
public class TextManipulering {
    public static void main(String[] args) {
        String produktBeskrivning = "Elegant kaffemugg i porslin, tillverkad i Sverige";
        
        // Undersök och manipulera strängen
        // Skriv ut resultaten
    }
}
```

**Din uppgift:**
1. Skriv ut originalbeskrivningen
2. Beräkna och skriv ut antal tecken i beskrivningen
3. Konvertera beskrivningen till stora bokstäver och skriv ut resultatet
4. Konvertera beskrivningen till små bokstäver och skriv ut resultatet
5. Använd `substring` för att extrahera och skriva ut de första 10 tecknen
6. Använd `substring` för att extrahera och skriva ut de sista 10 tecknen
7. Använd `replace` för att ersätta alla 'e' med 'x' och skriv ut resultatet

### Övning 3.2: Sökning i text

**Vad du lär dig:** Att söka efter text i en sträng

**Startmall:**
```java
public class TextSökning {
    public static void main(String[] args) {
        String beskrivning = "Handgjord keramikmugg med unikt mönster, perfekt för både kaffe och te.";
        
        // Sök efter specifika ord i beskrivningen
        // Skriv ut resultaten
    }
}
```

**Din uppgift:**
1. Använd `contains` för att kontrollera om beskrivningen innehåller ordet "kaffe"
2. Använd `contains` för att kontrollera om beskrivningen innehåller ordet "glas"
3. Använd `indexOf` för att hitta positionen för ordet "mugg"
4. Kontrollera om beskrivningen börjar med "Hand" med hjälp av `startsWith`
5. Kontrollera om beskrivningen slutar med "." med hjälp av `endsWith`
6. Skriv ut alla resultat med beskrivande text

### Övning 3.3: CSV-data

**Vad du lär dig:** Att dela upp och kombinera text

**Startmall:**
```java
public class CSVData {
    public static void main(String[] args) {
        String produktData = "Kaffemugg,Röd,89.50,Porslin,42";
        
        // Dela upp CSV-data och skriv ut som strukturerad information
    }
}
```

**Din uppgift:**
1. Använd `split` för att dela upp strängen vid varje kommatecken
2. Lagra delarna i en array av strängar
3. Skriv ut varje del med en beskrivande text:
   - "Produktnamn: [del 1]"
   - "Färg: [del 2]"
   - "Pris: [del 3] kr"
   - "Material: [del 4]"
   - "Artikelnummer: [del 5]"
4. Kombinera delarna till en prydlig produktbeskrivning med hjälp av konkatenering

## Del 4: Kombinerade övningar

### Övning 4.1: Kundvagn

**Vad du lär dig:** Att kombinera variabler och operatorer

**Startmall:**
```java
public class Kundvagn {
    public static void main(String[] args) {
        // Produktinformation
        String produkt1 = "T-shirt";
        int antalProdukt1 = 2;
        double prisProdukt1 = 149.50;
        
        String produkt2 = "Jeans";
        int antalProdukt2 = 1;
        double prisProdukt2 = 499.90;
        
        // Beräkna delsummor och totalsumma
        // Skriv ut en kundvagnsöversikt
    }
}
```

**Din uppgift:**
1. Beräkna delsumma för varje produkt (antal × pris)
2. Beräkna totalsumma för hela kundvagnen
3. Skriv ut en prydlig kundvagnsöversikt med produkter, antal, styckpris och delsummor
4. Lägg till en fraktkostnad på 39 kr om totalsumman är under 500 kr, annars 0 kr
5. Skriv ut den slutliga summan inklusive frakt

### Övning 4.2: Produktkod-parser

**Vad du lär dig:** Att kombinera string-operationer med logik

**Startmall:**
```java
public class ProduktkodParser {
    public static void main(String[] args) {
        String produktkod = "SWE-TR-L-123456";
        
        // Analysera produktkoden och extrahera information
        // Skriv ut den analyserade informationen
    }
}
```

**Din uppgift:**
1. En produktkod har formatet "LAND-KATEGORI-STORLEK-NUMMER"
2. Dela upp produktkoden i dess komponenter med `substring` eller `split`
3. Översätt landskoden till land:
   - "SWE" = "Sverige"
   - "DNK" = "Danmark"
   - "NOR" = "Norge"
4. Översätt kategorikoden till kategori:
   - "TR" = "Tröjor"
   - "BX" = "Byxor"
   - "SK" = "Skor"
5. Översätt storlekskoden till rätt storlek:
   - "S" = "Small"
   - "M" = "Medium"
   - "L" = "Large"
6. Skriv ut all information i en strukturerad form

### Övning 4.3: Orderbekräftelse

**Vad du lär dig:** Att skapa formaterad utskrift

**Startmall:**
```java
public class Orderbekräftelse {
    public static void main(String[] args) {
        // Kundinformation
        String kundNamn = "Anna Andersson";
        String adress = "Storgatan 1, 123 45 Staden";
        
        // Produkter och priser
        // Skapa din orderbekräftelse här
    }
}
```

**Din uppgift:**
1. Definiera minst tre produkter med namn, antal och pris
2. Beräkna delsummor och totalsumma
3. Skapa en snygg orderbekräftelse med:
   - Rubrik
   - Kundinformation
   - Tabell med produkter, antal, pris och delsummor
   - Totalsumma
   - Fraktinformation
   - Förväntad leveranstid
   - Tackmeddelande
4. Använd System.out.println för att skapa mellanrum och formatering

## Utmaningsövningar (valfria)

### Utmaning 1: Priskonverterare

**Vad du lär dig:** Avancerad string-formatering och matematiska operationer

**Startmall:**
```java
public class Priskonverterare {
    public static void main(String[] args) {
        double pris = 1299.90;
        
        // Skapa olika format av priset
        // Skriv ut de olika formaten
    }
}
```

**Din uppgift:**
1. Beräkna priset utan moms (pris ÷ 1.25)
2. Skapa och skriv ut följande format av priset:
   - "1299.90 kr"
   - "1,299.90 kr" (med tusentalsavgränsare)
   - "1 299,90 kr" (svenskt format)
   - "1299.90 kr inkl moms (1039.92 kr exkl moms)"
3. Dra av 15% rabatt och skriv ut det nya priset i alla format ovan
4. Skapa en prydlig tabell som visar alla prisformaten

### Utmaning 2: SEO-optimerare

**Vad du lär dig:** Avancerad string-manipulering

**Startmall:**
```java
public class SEOoptimerare {
    public static void main(String[] args) {
        String produktRubrik = "Exklusiv Handgjord Kaffemugg i Svenskt Porslin - Blå";
        String beskrivning = "Denna vackra kaffemugg är handgjord av erfarna keramiker i Sverige. Perfekt för dig som uppskattar högkvalitativa produkter med lång livslängd. Tillverkad av finaste porslin.";
        
        // Skapa SEO-optimerade versioner av texterna
    }
}
```

**Din uppgift:**
1. Skapa en URL-vänlig version av produktrubriken där:
   - Alla mellanslag ersätts med bindestreck
   - Alla stora bokstäver blir små
   - Alla specialtecken (å,ä,ö) ersätts med motsvarande (a,a,o)
2. Skapa en kortversion av beskrivningen (max 50 tecken) som slutar med "..."
3. Räkna och skriv ut antal ord i ursprungliga beskrivningen
4. Ta ut de 5 viktigaste nyckelorden (ord med minst 5 bokstäver) från beskrivningen
5. Skapa en "meta description" på max 155 tecken baserad på beskrivningen

## Tips för inlärningen

1. **Experimentera:** Ändra variabelvärden och se hur utskriften förändras.
2. **Läs felmeddelanden:** När något går fel, läs felmeddelandet noggrant - det berättar ofta exakt vad som är fel.
3. **Var konsekvent:** Håll en konsekvent stil i din kod, särskilt med namngivning av variabler.
4. **Ta små steg:** Gör en liten del i taget, testa, sedan nästa del.
5. **Kommentera din kod:** Skriv kommentarer som förklarar vad olika delar av koden gör.
