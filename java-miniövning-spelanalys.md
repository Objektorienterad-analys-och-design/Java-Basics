# Java Miniövning - Spelstatistik

## Introduktion

I denna övning ska du skapa ett program som analyserar resultaten från en spelsäsong för ett lag. Programmet kommer att låta användaren mata in matchresultat och sedan utföra olika typer av analys på dessa data.

## Uppgiftsbeskrivning

Du ska skapa ett program som:

1. Låter användaren mata in resultat för ett antal matcher (vinst, förlust eller oavgjort)
2. Beräknar och visar statistik för säsongen (poäng, antal vinster/förluster/oavgjorda, etc.)
3. Kategoriserar och analyserar lagets prestationer

## Detaljerade instruktioner

### Förberedelser

1. Skapa en ny Java-klass med namnet `SpelStatistik`
2. Importera `java.util.Scanner` för att hantera användarinput

### Steg 1: Insamling av matchresultat

**Uppgift:** Samla in resultat för lagets matcher under säsongen.

**Detaljerade instruktioner:**

1. Fråga användaren hur många matcher laget har spelat under säsongen
2. Skapa en array med rätt storlek för att lagra resultaten
3. För varje match, fråga användaren om resultatet:
   - 'V' för vinst
   - 'O' för oavgjort
   - 'F' för förlust
4. Lagra resultaten i arrayen

**Tips för implementation:**
- Du behöver en loop för att samla in data för varje match
- Tänk på att validera användarens input (att de bara skriver V, O eller F)

### Steg 2: Beräkna statistik

**Uppgift:** Beräkna och visa statistik baserat på matchresultaten.

**Detaljerade instruktioner:**

1. Räkna antal vinster, oavgjorda och förluster
2. Beräkna totalpoäng för säsongen (3 poäng för vinst, 1 poäng för oavgjort, 0 poäng för förlust)
3. Beräkna vinstprocent (antal vinster / totalt antal matcher)
4. Hitta den längsta sviten av vinster i följd
5. Visa all statistik på ett överskådligt sätt

**Tips för implementation:**
- Du behöver gå igenom arrayen med resultat
- För att räkna olika resultat kan du använda villkorssatser
- För att hitta längsta vinstsviten behöver du hålla reda på både aktuell svit och längsta svit

### Steg 3: Kategorisera och analysera prestationer

**Uppgift:** Kategorisera lagets prestation baserat på resultaten och ge en analys.

**Detaljerade instruktioner:**

1. Baserat på totalpoäng, kategorisera lagets säsong som:
   - Utmärkt: 80% eller mer av maximala poäng
   - Bra: 60-79% av maximala poäng
   - Medel: 40-59% av maximala poäng
   - Dålig: Under 40% av maximala poäng
2. Analysera om laget var bättre på att:
   - Vinna matcher (om vinstprocenten är över 50%)
   - Undvika förluster (om procenten förluster är under 30%)
3. Visa kategoriseringen och analysen

**Tips för implementation:**
- Maximala poäng är antalet matcher * 3
- Du behöver beräkna procentandel av maximala poäng
- Använd villkorssatser för att kategorisera prestation
- Du kan använda både if-else och/eller switch för olika delar av analysen

## Steg-för-steg-planering

Här är en mer detaljerad nedbrytning av hur du kan tänka när du närmar dig problemet:

### Steg 1: Insamling av matchresultat
1. Skapa en Scanner för användarinput
2. Fråga hur många matcher laget har spelat
3. Skapa en array för resultaten med rätt storlek (kan vara en char-array eller String-array)
4. Skapa en loop som går från match 1 till sista matchen
5. I varje iteration, be om resultatet för den aktuella matchen (V, O eller F)
6. Validera input (om användaren skriver något annat än V, O eller F, be dem försöka igen)
7. Spara resultatet i arrayen

### Steg 2: Beräkna statistik
1. Skapa variabler för antal vinster, oavgjorda, förluster, och totalpoäng
2. Loopa genom resultat-arrayen
3. För varje resultat:
   - Om det är 'V': öka vinster och lägg till 3 poäng
   - Om det är 'O': öka oavgjorda och lägg till 1 poäng
   - Om det är 'F': öka förluster
4. Beräkna vinstprocent
5. Hitta längsta vinstsviten:
   - Skapa variabler för aktuell svit och längsta svit
   - När du hittar en vinst, öka aktuell svit
   - Om aktuell svit > längsta svit, uppdatera längsta svit
   - När du hittar något annat än vinst, återställ aktuell svit till 0
6. Visa all statistik

### Steg 3: Kategorisera och analysera
1. Beräkna maximala möjliga poäng (antal matcher * 3)
2. Beräkna procentandel av maximala poäng
3. Baserat på procentandel, kategorisera säsongen
4. Beräkna procent förluster
5. Analysera om laget var bättre på att vinna eller undvika förluster
6. Visa kategorisering och analys

## Organisering av koden

Det är en bra praxis att dela upp din kod i metoder. Här är förslag på metoder som du kan implementera:

1. `main` - Programmets huvudmetod som koordinerar allt
2. `samlaInResultat` - En metod som samlar in matchresultat och returnerar en array
3. `beräknaStatistik` - En metod som beräknar och visar statistik
4. `hittaLängstaVinstsviten` - En metod som hittar längsta sekvensen av vinster
5. `kategoriseraPrestation` - En metod som kategoriserar och analyserar lagets prestation

## Reflektionsfrågor

När du har implementerat programmet, tänk över följande:

1. **Val av loopar:** Vilken typ av loop valde du för datainsamlingen? Vilken typ av loop valde du för att analysera resultaten? Varför valde du just dessa looptyper?

2. **Val av villkorssatser:** Hur implementerade du logiken för att kategorisera lagets prestation? Använde du if-else, switch, eller en kombination? Varför valde du denna approach?

3. **Struktur och modularitet:** Hur delade du upp din kod i metoder? Vilka fördelar ser du med din valda struktur?

4. **Alternativa lösningar:** Finns det andra sätt du kunde ha löst samma problem? Till exempel, skulle en annan datastruktur än en array fungera bättre för att lagra och analysera matchresultaten?

5. **Felhantering:** Hur hanterar ditt program felaktig input från användaren? Vilka förbättringar skulle du kunna göra?

## Inlämning

Din inlämning ska innehålla:
1. Java-koden för ditt program
2. En kort reflektion (max 1 sida) där du besvarar reflektionsfrågorna

## Bedömningskriterier

Du kommer att bedömas på:
1. Korrekt implementation av alla tre delar
2. Struktur och läsbarhet i koden
3. Effektiv användning av loopar och villkorssatser
4. Kvaliteten på din reflektion

## Exempel på körning

Ditt program skulle kunna fungera ungefär så här:

```
Välkommen till spelstatistikprogrammet!
Hur många matcher har laget spelat denna säsong? 10

Match 1: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 2: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 3: Ange resultat (V för vinst, O för oavgjort, F för förlust): O
Match 4: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 5: Ange resultat (V för vinst, O för oavgjort, F för förlust): F
Match 6: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 7: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 8: Ange resultat (V för vinst, O för oavgjort, F för förlust): V
Match 9: Ange resultat (V för vinst, O för oavgjort, F för förlust): O
Match 10: Ange resultat (V för vinst, O för oavgjort, F för förlust): V

--- Säsongsstatistik ---
Antal matcher: 10
Vinster: 7
Oavgjorda: 2
Förluster: 1
Totalpoäng: 23 av 30 möjliga
Vinstprocent: 70.0%
Längsta vinstsvit: 3 matcher

--- Prestationsanalys ---
Säsongskategori: Bra (76.7% av maximala poäng)
Laget var bättre på att vinna matcher.
Endast 10.0% av matcherna slutade med förlust.
```

## Tips för svårigheter

Om du fastnar, här är några tips:

1. **Att validera användarinput**: 
   - Använd en loop som fortsätter tills användaren ger korrekt input
   - Kontrollera att input är antingen 'V', 'O' eller 'F' (var uppmärksam på stor/liten bokstav)

2. **Att hitta längsta vinstsviten**:
   - Ha två räknare: en för aktuell svit och en för längsta svit
   - När du hittar en vinst, öka aktuell svit
   - När aktuell svit blir större än längsta svit, uppdatera längsta svit
   - När du hittar något annat än vinst, återställ aktuell svit till 0

3. **Att beräkna procent**:
   - När du beräknar procent, använd flyttal (double) för att få korrekt resultat
   - Till exempel: `double vinstProcent = (double)antalVinster / antalMatcher * 100;`