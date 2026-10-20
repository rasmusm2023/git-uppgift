# Frågor

## Fråga 1: Versionshantering vs vanliga filer

### **För Godkänt (G):** Vad är versionshantering och vad är den stora skillnaden mellan att spara en fil via editorns vanliga sparaknapp och att spara ändringar i Git?

- Versionshantering är ett system som håller koll på alla ändringar i koden över tid. Den stora skillnaden är att versionshantering sparar historiken, så att man kan gå tillbaka till olika ögonblick i historiken. Till skillnad från vanlig spara-knapp i editorn som bara sparar den nyaste versionen av koden.

### **För Väl Godkänt (VG):** Förklara vad som menas med att Git sparar en tidslinje av frysta ögonblicksbilder (commits). Vad bevisar det faktum att du när som helst kan klicka på din allra första commit på GitHub och fortfarande se alla tre TODO kvar i koden, trots att filen på din dator ser helt annorlunda ut idag?

- Varje commit sparar hur hela projektet ser ut just då, som ett foto. En commit kan inte ändras i efterhand. Varje ny commit pekar bakåt på den förra, så tillsammans bildar de en tidslinje.

Att första commiten fortfarande visar alla tre TODO bevisar att gamla commits aldrig skrivs över. Mina ändringar blev nya commits ovanpå de gamla. Filen på datorn är bara den senaste versionen, medan historiken finns kvar oförändrad. Därför kan jag alltid gå tillbaka och se varje tidigare version.

## Fråga 2: Arbetsytan, Staging och Commits

### **För Godkänt (G):** Beskriv vad kommandona git status, git add och git commit gör i det dagliga arbetsflödet och när du kör dem.

- **git status** visar läget just nu: vilka filer som är ändrade, vilka som är nya, vilka som är redo att committas. Körs typiskt ofta innan git add och git commit för att dubbelkolla ändringarna som gjorts.

**git add** väljer ut vilka filer som ska ingå i nästa commit. Man säger att man "stagar". Körs när en ändring är färdig. Man stagar och committar ofta, i små steg, i stället för att vänta tills en stor feature är klar.

**git commit** sparar de utvalda filerna/ändringarna som en ny ögonblicksbild i historiken, med ett meddelande som beskriver tydligt men kortfattat vad som gjorts. Det körs efter git add, när en del av arbetet är klart.

Arbetsflödet: ändra kod → git status → git add → git commit → upprepa.

### **För Väl Godkänt (VG):** Förklara relationen mellan arbetsytan (arket på skrivbordet), staging (kuvertet) och commit (arkivlådan). Förklara också varför Git protesterar med no changes added to commit om man har ändrat filen i editorn och försöker köra git commit direkt utan git add.

- Arbetsytan är filerna som jag redigerar i editorn. Här kan jag ändra fritt, men inget är sparat i git ännu.
  Staging är där jag lägger de ändringar som ska skickas iväg. Med git add flyttar jag en ändring från skrivbordet ner i kuvertet.
  Commit är där kuvertet förseglas och arkiveras. Med git commit blir innehållet i kuvertet en fryst ögonblicksbild i historiken.

git commit tar bara det som ligger i staging (kuvertet). Ändringar som gjorts i editorn ligger fortfarande på skrivbordet. Om jag kör git commit utan git add är kuvertet fortfarande tomt, och då finns det inget att arkivera. Git protesterar alltså inte för att filen är oförändrad. Problemet är att jag aldrig har lagt ändringen i kuvertet.
Lösningen är att köra git add först och sedan git commit.

## Fråga 3: Lådan hemma vs Montern på GitHub

### **För Godkänt (G):** Vad är skillnaden mellan mappen på din dator och repot på GitHub, och vad gör kommandot git push?

- Mitt lokala repo (mappen på datorn) är där jag arbetar: ändrar filer, gör commits osv. Commits jag gör hamnar bara här till att börja med.
  Repot på github (remote repo) är en kopia av projektet och dess historik som ligger på internet. Den fungerar som backup och andra kan se den och samarbeta via den.

git push skickar mina nya commits från datorn upp till github, så att repot där blir uppdaterat. Jag kör det efter git commit, när jag vill att mitt arbete ska synas och vara sparat på github.

### **För Väl Godkänt (VG):** Förklara konceptet med de två rummen / minnesytorna (lådan hemma på datorn vs glasmontern på GitHub). Förklara varför git push svarar Everything up-to-date om du har ändrat i koden men glömt att staga och committa innan du kör push.

- De två rummen: Lådan hemma är det lokala repot på datorn. Där hamnar mina commits, och bara jag ser dem. Glasmontern är GitHub, där andra kan se koden. Den uppdateras bara när jag kör git push, som skickar över de commits som saknas där.

git push skickar bara commits, inte ändringar som inte är committade. Om jag inte har kört git add och git commit har ändringen aldrig kommit in i lådan. Lådan och montern innehåller då samma commits, så det finns inget att skicka.
Lösningen är att köra git add, git commit och sedan git push.
