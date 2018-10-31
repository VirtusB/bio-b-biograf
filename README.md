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
  - ?
  - ?

## Programmets fremtid

- Forventet levetid: 5 år
- Udvidelsesmuligheder i senere versioner
  - ?

## Brugerprofil

- Hvem skal bruge systemet?
  - Bio B personale
  - Besøgende brugere på Bio B siden, mulige kunder
- Der kræves ingen erfaring, for at kunne benytte siden eller admin portalen

Krav til udviklingsforløbet

- Krav fra udvikler og kunden
  - Møde hver 14. dag
  - ?
- Hvilke vejledninger, designmetoder og standarder skal anvendes?
  - Objekt orienteret
  - UML diagram af klasserne
  - E/R diagram af databasen
  - Asynkrone metoder
  - Repository pattern
- Programmeringssprog
  - C#
  - SQL
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
  - ?
- Personer som kunden skal stille til rådighed
  - ?

## Definitioner

- Formatet på væsentlige data, som kunden ønsker
  - ?

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
    | Exceptions        | - Hvis brugeren ikke har råd<br>- Hvis der ikke er flere pladser |                 |            |
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
    | Preconditions     | 1. Brugeren har en e-mail <br>                               |                 |            |
    | Postconditions    | 1. Brugeren skal bruge kontooplysningerne til at logge ind   |                 |            |
    | Normal flow       | 1. Brugeren klikker "Opret konto" <br/>2. Brugeren bliver sendt til "Opret konto" siden
3. Brugeren udfyder alle oplysningerne og klikker "Opret" 
4. Brugerens oplysninger bliver gemt i databasen
5. Brugeren får at vide, at kontoen er oprettet
6. Brugeren kan nu logge ind |                 |            |
    | Alternative flow  | 1. Brugeren er ikke logget ind<br />2. Brugeren klikker på en film og klikker "Bestil"
3. Brugeren bliver sendt til log-ind siden |                 |            |
    | Exceptions        | - Hvis brugeren ikke udfylder alle felterne <br>- Hvis brugeren udfylder et felt med ugyldige oplysninger |                 |            |
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
    | Alternative flow  | 1. Brugeren klikker "Min konto"  <br/>2. Brugeren "Slet konto" 
3. Brugeren bliver spurgt, om han/hun er sikker  
4. Brugeren klikker "Nej" 
5. Brugerens konto bliver ikke slettet |                 |            |
    | Exceptions        | - Hvis brugeren ikke udfylder e-mailen korrekt               |                 |            |
    | Priority          | Høj                                                          |                 |            |
    | Frequence of use  |                                                              |                 |            |
    | Business rules    | Systemet skal altid spørge, om brugeren er sikker på at ville slette sin konto |                 |            |
    | Other information |                                                              |                 |            |
    | Assumptions       |                                                              |                 |            |