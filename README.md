> _Fork_ deze leertaak en ga aan de slag. 
Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. 
De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# Titel
<!-- Geef je project een titel en schrijf in één zin wat het is -->
Scroll driven animations spike 1

View transitions api spike 2 livelink:https://user-needs-bhvnj6iuq-yu-jing-projects-0dab48b4.vercel.app/members

christmas web audio Spike 3 livelink :https://user-needs-nmi3vl7i3-yu-jing-projects-0dab48b4.vercel.app/members 

## Inhoudsopgave

  * [Beschrijving](#beschrijving)
  * [Kenmerken](#kenmerken)

[//]: # (  * [Installatie]&#40;#installatie&#41;)

[//]: # (  * [Gebruik]&#40;#gebruik&#41;)

[//]: # (  * [Bronnen]&#40;#bronnen&#41;)

[//]: # (  * [Licentie]&#40;#licentie&#41;)

## Beschrijving
<!-- In de Beschrijving staat hoe je project er uit ziet, hoe het werkt en wat je er mee kan. -->
<!-- Voeg een mooie poster visual toe 📸 -->
<!-- Voeg een link toe naar Github Pages 🌐-->

## Kenmerken
<!-- Bij Kenmerken staat welke technieken zijn gebruikt en hoe. Wat is de HTML structuur? Wat zijn de belangrijkste dingen in CSS? Wat is er met Javascript gedaan en hoe? Misschien heb je een framwork of library gebruikt? -->

### spike 1
Mijn eerste spike is een scroll driven animation voor de cards met als thema contrasting colour dreaming <br>
in mijn eerdere versies had ik dat ik de cards een andere kleur wilde geven alleen bleek uit de usertest dat dit toch niet zo handig is zie hier de link naar wat ik eerrst had bij `designkeuzes`:  https://github.com/lisagjh/voorhoede/pull/43
In de pull request kan je zien hoe ik getest heb en waar ik naar gekeken heb om dit te realiseren


<h2>Volledige animatie als video</h2>

https://github.com/user-attachments/assets/c6ceb98f-1850-4cf3-883e-7ea636200b48

<h2>Code van de animatie</h2>

ook heb ik mij gehouden aan de code conventies afspraken https://github.com/fdnd-agency/voorhoede/issues/100

````svelte 
 {#each data.members as member}

        <article class="card">
            <picture>
                <source srcset="https://fdnd-agency.directus.app/assets/{member.photo}?format=avif" type="image/avif">
                <source srcset="https://fdnd-agency.directus.app/assets/{member.photo}?format=webp" type="image/webp">
                <img src="https://fdnd-agency.directus.app/assets/{member.photo}" loading="lazy" alt="{member.title}">
            </picture>

            <ul class="card-label-filters">
                <li class="label-filters">
                    service design
                </li>
                <li class="label-filters">label</li>
            </ul>

            <h2 aria-label="{member.title}">{member.title}</h2>
            <p>{member.address}</p>

            <ul class="card-label">
                <li>{parseInt(member.colleagues)}  werknemers</li>
                <li class="card-hiring">hiring</li>

            </ul>

            <Link href="/" clazz="detail-link"><span slot="link-text">Details</span>
                <svg width="16" height="16" slot="svg-icon-right" viewBox="0 0 24 24" fill="none">
                    <path d="M6 12H18M18 12L13 7M18 12L13 17" stroke-width="2" stroke-linecap="round"
                          stroke-linejoin="round"/>
                </svg>
            </Link>

        </article>
    {/each}
````

````css

body{
  background: rgb(129, 228, 168);
  background: linear-gradient(83deg, rgb(240 184 184) 0%, rgb(194, 250, 243) 47%, rgb(255 174 249) 100%);
}


  @keyframes slide-in-up {


        0% {

            transform: translateY(10em);
    background-color: white;
        }
        25% {
            transform: translateY(5em);
    background-color: white;
        }
        50% {
        background-color: white;
        }

    }


    @keyframes gradient-animation {
        0% {
            background-position: 0% 50%;   background-color: white;
        }
        100% {
            background-position: 100% 50%;
        }
    }
````

met prefers reduced motion word aangegeven dat mensen die geen voorkeur hebben deze animatie te zien krijgen en mensen die wel voorkeuren hebben krijgen de animatie niet te zien
````css
  @media (prefers-reduced-motion: no-preference) {
        img {
            animation: reveal 1s linear both;
            /* Rember to declare the timeline after the shorthand */
            animation-timeline: view();
        }
    }


@media (prefers-reduced-motion: no-preference) {
        .card {
            animation: slide-in-up both, white-background-cards 2s infinite;
            animation-timeline: view();
        }
    }
````

### spike 2
Mijn 2de animatie heb ik met view transitions gemaakt waarin  ik een rotate gebruikt heb en `document.startviewTransitions` zodat als je op de knop `maak mij recht` klikt dat er een smooth overgang is
de kaartjes draaien als je naar beneden scrolt en stoppen met draaien als je niet scrollt 


<h2>video van de animaite</h2>


video :https://github.com/user-attachments/assets/98195a00-5fd8-442e-97dc-022bae9984ad


<h2>Code van de animatie</h2>
```javascript

 const buttons = document.querySelectorAll('.button');
        for (let i = 0; i < buttons.length; i++) {
            buttons[i].addEventListener('click', () => {
                const clickedCard = buttons[i].closest('.card');
                document.startViewTransition(() =>
                    clickedCard.classList.toggle('active')
            )
            });
        }
```
als de viewtransition niet ondersteund word dan krijgt de gebruiker deze code te zien

````javascript
  else
        {
            const buttons = document.querySelectorAll('.button');
            for (let i = 0; i < buttons.length; i++) {
                buttons[i].addEventListener('click', () => {
                    const clickedCard = buttons[i].closest('.card');
                        clickedCard.classList.toggle('active')
                });
            }
        }
````

daarna bedacht ik me dat het wel leuk is om het andersom te maken dus dat alas je scrollt de cards draaien en als je klikt dat de cards dan recht worden

````css
  @keyframes Rotate {


        0% {
            /*background-color: red;*/
            transform: translateY(10em);
            filter: blur(25px);
            transition: filter 0.3s ease-in-out;
            rotate: 405deg;
        }
        25% {
            transform: translateY(5em);
            filter: blur(15px);
            transition: filter 0.3s ease-in-out;
        }
        50% {
            filter: blur(0px);
            transition: filter 0.3s ease-in-out;
        }

        100%{
            filter: blur(10px);
            transition: filter 0.3s ease-in-out;
        }

    }
````

ook heb ik rekening gehouden met mensen die niet van dat rotate houden aan de hand van deze code waarin ik aangeef dat mensen die reduce aan hebbens taan geen animatie te zien krijgen

````css 
   @media (prefers-reduced-motion: reduce) {
        .card {
            animation: none;
        }
        :global(.card.active) {
            animation: none; /* Remove the animation */
        }
    }
````

[//]: # (## Installatie)

[//]: # ()
[//]: # (de code staat op een andere branch en daar kan je het vinden :https://github.com/lisagjh/voorhoede/tree/spike/contrasting-digital-dreamscape-Yu-Jing )




[//]: # ()
[//]: # (## Gebruik)

## Bronnen

## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
