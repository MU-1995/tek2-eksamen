# Emne 1: CI/CD, GitHub Actions (Workflows)
Eksempler på spørgsmål:
## 1. Hvilke tjek laver man oftest i sin CI-pipeline?
- tjekker om koden overhovedet kompilere
- tjekker om Unit tests fejler
- Statisk kodeanalyse
## 2. Hvad er forskellen på jobs: og steps: i GitHub Actions?
jobs: er de overordnede opgaver. De kører som udgangspunkt parallelt og på hver sin runner (virtuelle maskine).

steps: er de individuelle trin inden for et job. De kører sekventielt - ét ad gangen , i rækkefølge.
## 3. Hvilken betydning har nøgleordene uses: og run:?
uses: henter et program som en anden har skrevet. actions/checkout@v4 er lavet af GitHub og gør ét specifikt job: henter din kode ned på maskinen.

run: en kommando du skriver selv - ligesom i terminalen.
## 4. Hvad er konkrete eksempler på hvor run: er nyttig?

## 5. Hvordan virker caching i GibHub Actions; hvad er en cache key?
Det fortæller GitHub at den skal gemme alle de JAR-filer Maven downloader i en cache, så næste gang workflow'et kører behøver den ikke downloade dem igen fra internettet.

Cache key er den nøgle GitHub bruger til at identificere cachen — den baseres automatisk på indholdet af din pom.xml. Logikken er:

- Samme pom.xml -> brug den gemte cache
- Ændret pom.xml(ny dependency tilføjet) -> byg cachen om
## 6. Hvad er formålet med hash-pinning af ens byggetrin?
uses: actions/checkout@v4 -- @v4 er et flydende tag. Det kan flyttes til nye eller skadelig commits

uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2 -- en commit-SHA. Kan ikke flyttes. Koden er den samme. Det er mindre læsbart, så #v4.2.2 viser versionen.
## 7. Hvilke af Maven's build lifecycle-trin giver mening at køre i CI?
Validate, compile, test, package, integration-test, verify

mvn -B verify kommandoen kører alt til og med verify. 
## 8. Hvordan aktiverer man et GibHub Actions workflow manuelt?
- Tilføj workflow_dispatch: under on: i din workflow-fil
- Gå til Actions-fanen på GitHub
- Vælg dit workflow i venstre side
- Klik "Run workflow"
## 9. Hvordan bygges og uploades Docker images i GibHub Actions?

## Eksempler på demonstration:
1. Forklar en GitHub Actions-fil til at teste Java-kode med Maven
- maven.yml
2. Tilføj caching af 3rd-party Maven dependencies
- tilføj cache: maven under actions/setup i maven.yml
3. Tilføj workflow_dispatch: til et projekt og kør CI manuelt
- tilføj workflow_dispatch: under triggers (on) i maven.yml
4. Udfør hash-pinning af en enkelt 3rd-party action
    1. find nyeste version -- https://github.com/actions/checkout/releases
   2. find SHA -- brug git ls-remote https://github.com/actions/checkout "refs/tags/v7.0.1*" i bash
   3. indsæt SHA ved actions/checkout@ i maven.yml