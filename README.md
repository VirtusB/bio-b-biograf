# Biograf Bio B webapplikation

[TOC]



## Indledning

B Bio skal have et nyt website til at administrere forestillinger og til at håndtere salg af billetter til deres kunder. De ter vigtigt for B Bio at få deres kunder registreret i deres eget system. Kunden bliver derved ikke fristet af film, der vises i andre biografer. Og det gør det nemmere for kunden, at bestille billetter til flere forestillinger. Udover at kunden selv kan vedligeholde egne data, skal Bio B også have mulighed for at vedligeholde kunder i kundebasen

## Krav

Der er følgende overordnede krav til websitet/løsningen.

- Bio B skal kunne oprette, redigere og nedlægge følgende: Kommende film, aktuelle film, sale samt oprette forestillinger hvor film og sal indgår. Dette arbejde udføres af en Bio B medarbejder, der skal være logget ind. Det skal være muligt at differentiere adgangen, så oprettelse af forestillinger kræver særlig fuldmagt
- Kunder skal kunne oprette dem selv som bruger, logge ind, redigere deres data, se tilgængelige forestillinger, bestille billetter, få listet historik, optjene rabatter, og selv kunne administrere deres bestillinger



## Systembesrkivelse

- Verdensbillede
  - ![](billeder/Screen%201.png)
  - Hardware
    - CPU: 2 x Intel Xeon E5-2670
    - CPU køler: 2 x Noctua NH-U12DXi4
    - RAM: Hynix 128GB 16x8GB PC3–12800R
    - Bundkort: ASRock E2C602–4L/D16
    - SSD: Samsung EVO 500GB
    - PSU: Corsair RM1000X
    - Kabinet: Fractal Design Define XL R2
  - Software
    - Microsoft SQL Server
    - ASP.Net Core 2.1
    - Entity Framework Core

## Programmets funktion

- Grundigere beskrivelse
  - Moderne web applikation til Bio B biografen. Admin portal som giver Bio B personale mulighed for, at oprette, redigere og slette forestillinger, sale samt film. Der er 2 typer portal brugere, kun-se-brugere og adgang-til-alt brugere, så Bio B selv kan vælge hvilke medarbejdere der skal kunne oprette, redigere og slette. Desuden skal personalet have mulighed for, at validere en billet, tjekke betaling og status via admin portalen, samt refundering og ændring af status. Kunder skal have deres egen portal, hvor de kan se deres tidligere bestillinger, ændre på en igangværende bestilling og se hvilket rabattrin de er på. Kunder går ét rabattrin op, for hver 10 gennemførte bestillinger. Kunder skal kunne slette deres konto og ændre på deres kontaktinformation. Bio B personale skal også kunne ændre i kundens informationer, f.eks. i tilfælde hvor kunden foretrækker ikke at gøre det selv.

- UML diagram
  - ![](billeder/1540896309722.png)



## Programmets begrænsinger

- Programmet skal ikke kunne:
  - Siden skal ikke være optimeret til mobiler eller tablets

## Programmets fremtid

- Forventet levetid: 5 år
- Udvidelsesmuligheder i senere versioner
  - App til Android og iOS
  - Responsiv webside
  - Eget anmeldelses- og ratingsystem
  - Videoafspiller på siden til trailers

## Brugerprofil

- Hvem skal bruge systemet?
  - Bio B personale
  - Besøgende brugere på Bio B siden, mulige kunder
- Der kræves ingen erfaring, for at kunne benytte siden eller admin portalen

## Krav til udviklingsforløbet

- Krav fra udvikler og kunden
  - Møde hver 14. dag
- Hvilke vejledninger, designmetoder og standarder skal anvendes?
  - Objekt orienteret
  - UML diagram af klasserne
  - E/R diagram af databasen
  - Asynkrone metoder
  - Repository pattern
- Programmeringssprog
  - C#
  - SQL
  - HTML/CSS
  - JavaScript
- Review
  - ?
- Hvilken dokumentation, skal der udarbejdes
  - Brugermanual til admin portalen
- Hvordan skal ændringer i kravspecifikationen håndteres
  - Ændringer vil så vidt muligt blive implementeret efter ønske

## Omfang af kundeleverence

- Hvor meget af det samlede system skal leveres til kunden
  - URL til websiden, URL til admin portalen, adgangskoder til admin portalen
- Hvor meget af dokumentationen skal leveres til kunden
  - Brugermanualen, medmindre yderligere bliver efterspugt

## Forudsætninger

- Udstyr som kunden skal stille til rådighed under udviklingen
  - Intet. Udviklerne har eget udstyr.
- Personer som kunden skal stille til rådighed
  - En  gruppe på 5 mennesker, til at teste brugervenligheden af siden

## Definitioner

- Formatet på væsentlige data, som kunden ønsker
  - PDF

## Funktionelle krav

- Use Cases

  - Kunde - køb af billet

    | ID and Name       | 1 - Køb af billet                                            |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Besøgende på Bio B siden                                     | Secondary actor | X          |
    | Description       | Brugeren skal købe en billet                                 |                 |            |
    | Trigger           | Brugeren klikker på en film på siden                         |                 |            |
    | Preconditions     | 1. Brugeren er logget ind<br>2. Brugeren skal kunne betale online <br>3. Brugeren skal have råd til billetten |                 |            |
    | Postconditions    | 1. Brugeren skal benytte sig af billetten                    |                 |            |
    | Normal flow       | 1. Brugeren klikker "Bestil" <br>2. Brugeren bliver sendt til betalingsgateway <br>3. Brugeren udfyder oplysninger og klikker "Betal" <br>4. Betalingen bliver accepteret <br>5. Reservationen får en "Paid" status i databasen <br>6. Brugeren får vist billetten og kan klikke "Print" |                 |            |
    | Alternative flow  | 1. Brugeren er ikke logget ind<br>2. Brugeren klikker på en film og klikker "Bestil"<br>3. Brugeren bliver sendt til log-ind siden |                 |            |
    | Exceptions        | 1. Hvis brugeren ikke har råd<br>2. Hvis der ikke er flere pladser |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal ikke lade en bruger købe en billet, hvis brugeren ikke er logget ind |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

  - Kunde - oprettelse af konto

    | ID and Name       | 2 - Oprettelse af konto                                      |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Besøgende på Bio B siden                                     | Secondary actor | X          |
    | Description       | Brugeren skal oprette en konto på Bio B websiden             |                 |            |
    | Trigger           | Brugeren klikker på "Opret konto", eller skal købe en billet |                 |            |
    | Preconditions     | 1. Brugeren har en e-mail                                    |                 |            |
    | Postconditions    | 1. Brugeren skal bruge kontooplysningerne til at logge ind   |                 |            |
    | Normal flow       | 1. Brugeren klikker "Opret konto" <br/>2. Brugeren bliver sendt til "Opret konto" siden<br>3. Brugeren udfyder alle oplysningerne og klikker "Opret" <br>4. Brugerens oplysninger bliver gemt i databasen<br>5. Brugeren får at vide, at kontoen er oprettet<br>6. Brugeren kan nu logge ind |                 |            |
    | Alternative flow  | 1. Brugeren er ikke logget ind<br />2. Brugeren klikker på en film og klikker "Bestil"<br>3. Brugeren bliver sendt til log-ind siden |                 |            |
    | Exceptions        | 1. Hvis brugeren ikke udfylder alle felterne <br>2. Hvis brugeren udfylder et felt med ugyldige oplysninger |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal ikke lade en bruger oprette en konto, hvis brugeren ikke er over 18 år, eller ikke har udfyldt alle felterne korrekt |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

  - Kunde - sletning af konto

    | ID and Name       | 3 - Sletning af konto                                        |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Bruger med konto på Bio B siden                              | Secondary actor | X          |
    | Description       | Brugeren skal slette sin konto på Bio B websiden             |                 |            |
    | Trigger           | Brugeren klikker på "Slet konto" på "Min konto" siden        |                 |            |
    | Preconditions     | 1. Brugeren har en konto<br />2. Brugeren er logget ind      |                 |            |
    | Postconditions    |                                                              |                 |            |
    | Normal flow       | 1. Brugeren klikker "Min konto"  <br>2. Brugeren "Slet konto" <br>3. Brugeren bliver spurgt, om han/hun er sikker  <br>4. Brugeren klikker "Ja" <br>5. Brugerens bedes indtaste sin email i popup vindue <br>6. Brugeren kan nu klikke på "Slet" knappen <br>7. Brugeren klikker på "Slet" og kontoen fjernes fra databasen |                 |            |
    | Alternative flow  | 1. Brugeren klikker "Min konto"  <br/>2. Brugeren "Slet konto" <br>3. Brugeren bliver spurgt, om han/hun er sikker<br>4. Brugeren klikker "Nej" <br>5. Brugerens konto bliver ikke slettet |                 |            |
    | Exceptions        | 1. Hvis brugeren ikke udfylder e-mailen korrekt              |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid spørge, om brugeren er sikker på at ville slette sin konto |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

  - Personale - Ændring af rolle for bruger

    | ID and Name       | 4 - Ændring af rolle for bruger                              |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Personale på Bio B siden                                     | Secondary actor | X          |
    | Description       | Den ansatte skal ændre rolle for en bruger                   |                 |            |
    | Trigger           | Den ansatte klikker "Rediger brugere"                        |                 |            |
    | Preconditions     | 1. Den ansatte har en konto <br>2. Den ansatte er logget ind<br>3. Den ansatte er super-admin |                 |            |
    | Postconditions    |                                                              |                 |            |
    | Normal flow       | 1. Den ansatte klikker "Administrer brugere"   <br>2. Den ansatte vælger en specifik bruger <br>3. Den ansatte klikker "Rediger bruger"   <br>4. Den ansatte vælger rolle for brugeren i dropdown  <br>5. Den ansatte klikker "Gem"  <br>6. Brugerens rolle er gemt i databasen  <br> |                 |            |
    | Alternative flow  |                                                              |                 |            |
    | Exceptions        | 1. Hvis den ansatte ikke er super-admin                      |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid sørge for, at den ansatte har tilstrækkelige rettigheder |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

  - Personale - oprettelse af film

    | ID and Name       | 5 - Oprettelse af film                                       |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Personale på Bio B siden                                     | Secondary actor | X          |
    | Description       | Den ansatte skal oprette en film                             |                 |            |
    | Trigger           | Den ansatte klikker "Opret film"                             |                 |            |
    | Preconditions     | 1. Den ansatte har en konto  <br>2. Den ansatte er logget ind <br>3. Den ansatte er super-admin<br />4. Filmen skal ikke allerede eksistere |                 |            |
    | Postconditions    |                                                              |                 |            |
    | Normal flow       | 1. Den ansatte klikker "Administrer film"    <br>2. Den ansatte klikker "Opret film" <br>3. Den ansatte udfylder alle felterne <br>4. Den ansatte klikker "Gem film"   <br>5. Filmen bliver gemt i databasen |                 |            |
    | Alternative flow  |                                                              |                 |            |
    | Exceptions        | 1. Hvis den ansatte ikke er super-admin<br />2. Hvis filmen allerede eksisterer<br>3. Hvis alle felter ikke er udfyldt |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid sørge for, at den ansatte har tilstrækkelige rettigheder, og at filem ikke allerede findes |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |



  - Personale - oprettelse af show

    | ID and Name       | 6 - Oprettelse af show                                       |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Personale på Bio B siden                                     | Secondary actor | X          |
    | Description       | Den ansatte skal oprette et show                             |                 |            |
    | Trigger           | Den ansatte klikker "Opret show"                             |                 |            |
    | Preconditions     | 1. Den ansatte har en konto  <br>2. Den ansatte er logget ind <br>3. Den ansatte er super-admin<br />4. Showet skal ikke eksistere i salen i samme tidsramme<br>5. Der skal vælges en film til showet |                 |            |
    | Postconditions    |                                                              |                 |            |
    | Normal flow       | 1. Den ansatte klikker "Administrer shows"    <br>2. Den ansatte klikker "Opret show" <br>3. Den ansatte udfylder alle felterne <br>4. Den ansatte klikker "Gem show"   <br>5. Showet bliver gemt i databasen |                 |            |
    | Alternative flow  |                                                              |                 |            |
    | Exceptions        | 1. Hvis den ansatte ikke er super-admin<br />2. Hvis showet overlapper med et andet show i samme sal<br />3. Hvis alle felter ikke er udfyldt |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid sørge for, at den ansatte har tilstrækkelige rettigheder, og at showet ikke allerede findes |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

  - Personale - validering af billtetter

    | ID and Name       | 7 - validering af billtetter                                 |                 |            |
    | ----------------- | ------------------------------------------------------------ | --------------- | ---------- |
    | Created by        | Virtus                                                       | Date Created    | 30.10.2018 |
    | Primary actor     | Personale på Bio B siden                                     | Secondary actor | X          |
    | Description       | Den ansatte skal validere en billet                          |                 |            |
    | Trigger           | Den ansatte klikker "Valider billet"                         |                 |            |
    | Preconditions     | 1. Den ansatte har en konto  <br>2. Den ansatte er logget ind <br>3. Den ansatte har rollen "Personale" eller over<br />4. Der er en kunde med en billet |                 |            |
    | Postconditions    |                                                              |                 |            |
    | Normal flow       | 1. Den ansatte klikker "Valider billet"    <br>2. Den ansatte indtaster billet nummeret <br>3. Den ansatte klikker "Valider" <br>4. Den ansatte får svaret om billetten er gyldig   <br>5. Billetten er gyldig |                 |            |
    | Alternative flow  | Ved trin 5 er billetten ikke gyldig                          |                 |            |
    | Exceptions        | 1. Hvis den ansatte ikke har rollen "Personale"<br />2. Hvis billetten ikke er gyldig |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid sørge for, at den ansatte har tilstrækkelige rettigheder, og at tjekke om billetten er gyldig |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |

## Bruger-grænseflade

- Krav til måden programmet betjenes på
  - Mus
  - Tastatur
  - Skærm
  - Internet
  - Computer
- Forskellige brugeres rettigheder til brug af forskellige funktioner
  - Personale
    - Validere billetter
    - Logge ind på admin portalen
  - Super-admin
    - Validere billetter
    - Oprette, slette og redigere film
    - Oprette, slette og redigere shows
    - Administrering af roller
  - Kunde
    - Logge ind
    - Ændre kontaktinformationer
    - Bestille billetter
    - Se ordre historik
    - Se optjent rabat

## Hardware-grænseflade

- Hvordan er delene i systemet hardwaremæssigt bygget sammen
  - ?
- På hvilken elektrisk form optræder informationerne
  - Via GUI interface på siden

## Kommunikations-grænseflade

- Overordnet kommunikationsprotokol
  - HTTP / HTTPS

## Software-grænseflade

- Operativsystemet som programmellet skal køre under
  - Windows
  - MacOS
  - Linux
- Benyttelse af prædefinerede softwaremoduler
  - Entity Framework
  - SQL Server Management Studio

## Krav til programmets ydelse

- Specifikke tidskrav til udførelse af bestemte funktioner
  - Asynkrone funktioner
  - Webside load tid under 1.5 sekund

## Kvalitetsfaktorer

- Hastighed af siden
  - Siden skal loade indenfor 1.5 sekund
  - Brugeren skal have mindst have en forbindelse på 12 mbit
  - Brugeren skal have en computer der ikke er over 5 år gammel
  - SQL Server holdes opdateret og serveren skal have en gigabit forbindelse
  - Vigtighed: 5

## Pålidelighed

- Nøjagtighed
  - Siden skal have en oppetid på mindst 99%
  - Siden skal være 100% nøjagtighed i billetvalidering
- Håndtering af fejlbetjening
  - Fikses af udviklerne mod betaling

## Vedligeholdelsesvenlighed

- Hvor lang tid tager det at finde en fejl
  - Mindre problemer: 6 timer
  - Mellem problemer: 24 timer
  - Større problemer: op til 7 dage
  - Tider vil variere alt efter beskrivelse af problemet
- Hvor nemt er det at lave en mindre tilpasning til et ændret behov
  - Afhængig af forespørgelsen, men generelt nemt

## Udvidelsesvenlighed

- Hvor nemt er det at lave en egentlig udvidelse af produktet
  - Afhængig af udvidelse

## Brugervenlighed

- Hvor lang tid tager det for en ny bruger at lære at betjene produktet
  - Personale: under 1 dag, hvis brugermanualen benyttes
  - Bruger: med gennemsnitlige it-egenskaber, under 5 minutter

## Effektivitet

- Hvilke dele af produktet skal prioriteres høj effektivitet
  - Bestilling af billetter
  - Validering af billetter

## E/R diagram

![](billeder/erdiagram.png)

## Kanban

![](billeder/kanban.png)