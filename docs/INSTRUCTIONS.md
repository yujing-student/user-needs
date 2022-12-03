
# Back to Static - Static Site Generation

Ontwikkel een statisch gegenereerde website voor een opdrachtgever

## Context

Deze leertaak hoort bij sprint 17 Back to Static. Dit is een leertaak die je individueel of in een team uitvoert.

In het college _S17W1-01-Sprintplanning Back-to-Static_ wordt de opdracht uitgelegd. In de Workshop _S17W1-03-Static-Site-Generation_ krijg je uitleg over hoe je statische web pagina's kan genereren met SvelteKit.

Bij deze leertaak hoort de deeltaak:
- [Creative coding](https://github.com/fdnd-task/back-to-static-creative-coding)

## Doel van deze opdracht

Je leert wat Static Site generation is, wat de voor- en nadelen zijn en hoe je dit kan toepassen. 

## Werkwijze

Deze opdracht gaat over de DLC fases **Bouwen** en **Integreren** 

### Bouwen
De website die je gebouwd heb maakt tot nu toe gebruik van server side rendering. Elke keer dat een bezoeker van de website een pagina bezoekt wordt er een request naar de server gedaan en rendert de server de betreffende pagina voordat de response naar de browser wordt teruggestuurd. Aangezien de server de data uit een API moet ophalen (via het headless cms), kan het even duren voordat de pagina gerenderd is. Om de website efficiënter te maken ga je de website van te voren renderen zodat er na een request van een bezoeker alleen maar statische HTML, CSS en JavaScript hoeft worden teruggestuurd.

#### Aanpak
1. Meet van de homepage van de huidige server side gerenderde webiste de _response tijd_ en het aantal _kilobytes_ dat in de response wordt meegestuurd. Doe deze test op jou localhost en kijk hiervoor in de _Dev Tools > Network Tab_ met een _Throttle_ van bijvoorbeeld _Slow 3G_.
2. maak een branch aan, bijvoorbeeld _static-site_.
3. Zoek uit hoe je in het door jou gebruikte framework de website statisch gegenereerd kan worden. En pas je code aan volgens de instructies. 
4. Maak op je localhost een build van de website en documenteer in je wiki de _response tijd_ en het aantal _kilobytes_ dat in nu de response wordt meegestuurd voor de homepage.

### Integreren
Nu de website statisch gegeneerd wordt, ga je de website publiceren naar het internet en ga je ervoor zorgen dat bij een verandering van de content of de code de website opnieuw gebuild wordt (continuous deployment).

#### Aanpak
1. Publiceer je website met bijvoorbeeld Netlify of Vercel. Nu je statische pagina's publiceertd kan je ook met een GitHub action automatisch de site laten builden bij een update van de code.
2. Zoek uit hoe je na een aanpassing van de content in het headless cms een nieuwe build kan maken 

## Criteria

Focus sprint # - De focus van deze sprint ligt op het statisch genereren van een website.

Voor deze leertaak gelden de gedragscriteria voor sprint 17 Back to Static: 
* Methodisch handelen: Combineert onderbouwd principes, conventies en best-practices op het gebied van frontend, interface design en vormgeving.
* Methodisch handelen: Weegt belangen van de eindgebruiker en de eisen en wensen van een opdrachtgever af bij het realiseren van een oplossing voor een opdrachtgever.
* Probleemoplossend vermogen: Analyseert een vraag, signaleert knelpunten en kiest onderbouwd een oplossingsrichting.
* Lerend vermogen: Maakt aangeboden en zelf gevonden materie eigen, gebruikt dit bij leertaken, deelt ervaring binnen de squad en leert van anderen.
* Lerend vermogen: Kent eigen capaciteiten en beperkingen, waardeert het vermogen van anderen en maakt dit bespreekbaar

Deze opdracht is done als:
- [ ] jou code build naar een statische website 
- [ ] je code automatische gebuild wordt naar de live site bij een push naar GitHub (continuous deployment)
- [ ] de website online te bekijken is via GitHub pages of een ander platform (Netlify, Vercel, etc)
- [ ] documenteer het verschil in respons tijd en het het evrschil in kilo


