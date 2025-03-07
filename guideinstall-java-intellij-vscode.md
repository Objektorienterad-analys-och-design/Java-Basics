# Installationsguide för Java-utvecklingsmiljö

För att kunna programmera i Java behöver du två huvudkomponenter:

1. **JDK (Java Development Kit)** - Detta är själva Java-plattformen
2. **En IDE (Integrated Development Environment)** - Detta är verktyget du kommer att skriva kod i

## Installera JDK

Innan du kan börja programmera i Java måste du installera JDK (Java Development Kit). Här är stegen:

### För Windows

1. Besök Oracle's nedladdningssida för JDK: https://www.oracle.com/java/technologies/downloads/
2. Alternativt kan du använda OpenJDK: https://adoptium.net/
3. Välj Windows-versionen (x64 Installer)
4. Ladda ner installationsfilen och kör den
5. Följ installationsguiden med standardinställningarna
6. Verifiera installationen genom att öppna kommandotolken (cmd) och skriva:
   ```
   java -version
   ```

### För macOS

1. Besök Oracle's nedladdningssida för JDK: https://www.oracle.com/java/technologies/downloads/
2. Alternativt kan du använda OpenJDK: https://adoptium.net/
3. Välj macOS-versionen
4. Ladda ner .dmg-filen och öppna den
5. Kör installationspaketet och följ anvisningarna
6. Verifiera installationen genom att öppna Terminal och skriva:
   ```
   java -version
   ```

### För Linux

1. För Ubuntu/Debian:
   ```
   sudo apt update
   sudo apt install openjdk-17-jdk
   ```

2. För Fedora/Red Hat:
   ```
   sudo dnf install java-17-openjdk-devel
   ```

3. Verifiera installationen:
   ```
   java -version
   ```

## Installera en IDE

Du har flera alternativ när det gäller vilken IDE du vill använda för Java-utveckling. De tre främsta alternativen är:

### IntelliJ IDEA (Rekommenderas)

IntelliJ IDEA anses av många vara den bästa Java-IDE:n med kraftfulla funktioner och intelligenta kodfunktioner.

1. Gå till JetBrains webbplats: https://www.jetbrains.com/idea/download/
2. Ladda ner "Community Edition" (gratis)
3. Kör installationsfilen
4. Följ installationsguiden med standardinställningarna
5. Starta IntelliJ IDEA och välj "New Project" för att skapa ditt första Java-projekt
6. Välj "Java" från projekttyperna och se till att JDK är korrekt konfigurerad
7. Ge projektet ett namn och klicka på "Create"

#### Skapa ditt första Java-program i IntelliJ

1. Högerklicka på din projektmapp i Project Explorer
2. Välj New > Java Class
3. Ge klassen ett namn (t.ex. "HejVarlden")
4. I klassen, skriv in main-metoden:
   ```java
   public static void main(String[] args) {
       System.out.println("Hej, världen!");
   }
   ```
5. Kör programmet genom att högerklicka i editorn och välja "Run"

### Eclipse

Eclipse är en annan populär och kraftfull IDE för Java.

1. Gå till Eclipse nedladdningssida: https://www.eclipse.org/downloads/
2. Ladda ner "Eclipse IDE for Java Developers"
3. Kör installationsfilen och följ instruktionerna
4. När du startar Eclipse kommer du att bli ombedd att välja en arbetsyta (workspace)
5. Skapa ett nytt Java-projekt genom att gå till File > New > Java Project
6. Ge projektet ett namn och klicka på "Finish"

### Visual Studio Code med Java-tillägg

VS Code är ett lättare alternativ som blir alltmer populärt för Java-utveckling.

1. Ladda ner och installera VS Code: https://code.visualstudio.com/
2. Öppna VS Code
3. Gå till Extensions (Ctrl+Shift+X)
4. Sök efter och installera följande tillägg:
   - "Extension Pack for Java" (från Microsoft)
   - "Java Extension Pack" (från Microsoft)
5. När tilläggen är installerade, öppna en mapp (File > Open Folder) där du vill lagra dina Java-filer
6. Skapa en ny fil med filändelsen .java (t.ex. HejVarlden.java)
7. Skriv din kod i filen och spara den
8. Kör programmet genom att klicka på "Run" över main-metoden eller genom att använda "Run Java" i högerklicksmenyn

#### Konfigurera VS Code för Java

För att få en bättre upplevelse med Java i VS Code:

1. Gå till Inställningar (File > Preferences > Settings)
2. Sök efter "java.home" och ställ in sökvägen till din JDK-installation
3. Konfigurera "java.jdt.ls.vmargs" om du behöver anpassa minnestilldelning
4. För felsökning, installera även "Debugger for Java"-tillägget

## Felsökning vid installation

### Vanliga problem med JDK

1. **"java" är inte igenkänt som ett internt kommando**: Detta betyder att Java inte är korrekt konfigurerat i din PATH-miljövariabel.
   - Windows: Uppdatera din PATH-miljövariabel att inkludera `C:\Program Files\Java\jdk-X.X.X\bin` 
   - Mac/Linux: Lägg till export PATH=$PATH:/path/to/jdk/bin i din .bash_profile eller .zshrc fil

2. **Fel JDK-version**: Om din IDE använder fel JDK-version:
   - IntelliJ: File > Project Structure > Project > Project SDK
   - Eclipse: Window > Preferences > Java > Installed JREs
   - VS Code: Uppdatera java.home i inställningarna

### Vanliga problem med IDE

1. **IntelliJ visar inte Run-alternativet**: Kontrollera att din klass har en korrekt main-metod
2. **Eclipse visar "Build path"-fel**: Högerklicka på projektet, välj Build Path > Configure Build Path och kontrollera JRE System Library
3. **VS Code visar inte Java-alternativ**: Kontrollera att Java-tilläggen är korrekt installerade och aktiverade

## Git-integration

För versionshantering rekommenderar vi att du använder Git tillsammans med din IDE:

- **IntelliJ IDEA**: Har inbyggd Git-integration. Gå till VCS > Enable Version Control Integration
- **Eclipse**: Använd EGit-tillägget som följer med de flesta Eclipse-installationer
- **VS Code**: Har inbyggd Git-integration som standard

## Slutsats

Med JDK och en IDE installerade är du redo att börja din Java-programmerings-resa! Experimentera med den utvecklingsmiljö som passar dig bäst - alla tre alternativen har sina styrkor.

För nybörjare kan IntelliJ IDEA Community Edition vara det bästa valet tack vare dess användarvänlighet och kraftfulla kodfunktioner, men Eclipse och VS Code är också utmärkta alternativ.

Lycka till med din Java-programmering!