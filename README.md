# Workshop: Git Flow

I denna lilla workshop kommer ni att få "steg-för-steg"-instruktioner för att träna på att arbeta enligt Git Flow, ett måste för alla kommande projekt i er utbildning. Jag rekommenderar att ni använder er av Git Bash-terminalen för en trevligare överblick när ni arbetar.

## Steg 1 - Skapa repo

Börja med att välja ut en person i gruppen som skapar ert repo, privat eller public spelar mindre roll. Börja med att göra alla till collaborators så att ni alla har push- och pull-rättigheter till repot.

## Steg 2 - Skapa dev-branchen

"dev"-branchen funkar alldeles utmärkt att skapa online på Github, så öppna branchvyn och skapa en ny branch vid namn "dev". Source skall vara "main". Alla i gruppen kan nu klona hem ert repo lokalt till era datorer, och även skapa er egna lokala "dev"-branch genom att stå i "main" och köra ```git branch dev```. Hoppa sedan över till er lokala "dev"-branch genom att köra kommandot ```git checkout dev```.

## Steg 3 - Skapa branch protection rules

För att uppa säkerheten i vårt projekt, och förhindra att vi har frifräsare i gruppen som kör sitt eget race och skriver över andras arbeten så bör vi skapa så kallade Branch Protection Rules. Ta er till ert repos inställningar, och klicka på *Rules* -> *Rulesets* i vänstermenyn. Klicka sedan på den gröna knappen och välj *New branch ruleset*. 
1. Döp er regel till "Main protection rule", och under alternativet *Enforcement status* bockar ni i *Active*.
2. Scrolla ner till *Target branches*, klicka på *Add target* och välj alternativet *Include by pattern*. Ange "main" i fältet.
3. Scrolla vidare till *Branch rules* där ni bockar i *Require a pull request before merging*, samt ändra värdet i *required apprvals* till 1 mindre än antalet personer i gruppen (ex är ni 4 i gruppen så sätter ni värdet 3). Rör ingenting annat.
4. Scrolla längst ner och klicka på *Create*.

Nu har ni skapat en regel som skyddar er main från olyckliga mergningar. Nu kommer alla i gruppen (förutom den som skapar pull requesten) vara tvugna att godkänna innan en branch kan mergas till er "main".
Skapa nu ytterligare en regel som ni döper till "Branch protection". Ni följer stegen ovan bortsett från att ni nu i steg 2 efter att ha klickat på *Add target* väljer *Include all branches*.
Denna regel kommer säkerställa att alla pull requests till alla brancher förutom "main" (som kräver fler) kräver 1 review från en lagkamrat innan ni kan merga.

## Steg 4 - Ändra default-branch (Valfritt)

Detta steg är mest för att säkerställa att ni inte råkar skapa onödiga pull requests till "main", vilket om ni har skapat er "Main protection rule" inte längre är lika akut. Det kan dock vara skönt att slippa byta till "dev" varje gång man skapr en pull request.
Ta er till inställningarna och *General*. Ganska högt upp på sidan hittar ni *Default branch* där ni om ni så önskar kan byta er default branch till "dev".

## Steg 5 

Ni har fått en lista på olika tasks. Dessa hitta ni [här](./tasks.md)
