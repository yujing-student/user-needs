> _Fork_ deze leertaak en ga aan de slag. 
Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. 
De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# Titel
<!-- Geef je project een titel en schrijf in één zin wat het is -->
Scroll driven animations spike 1

## Inhoudsopgave

  * [Beschrijving](#beschrijving)
  * [Kenmerken](#kenmerken)
  * [Installatie](#installatie)
  * [Gebruik](#gebruik)
  * [Bronnen](#bronnen)
  * [Licentie](#licentie)

## Beschrijving
<!-- In de Beschrijving staat hoe je project er uit ziet, hoe het werkt en wat je er mee kan. -->
<!-- Voeg een mooie poster visual toe 📸 -->
<!-- Voeg een link toe naar Github Pages 🌐-->

## Kenmerken
<!-- Bij Kenmerken staat welke technieken zijn gebruikt en hoe. Wat is de HTML structuur? Wat zijn de belangrijkste dingen in CSS? Wat is er met Javascript gedaan en hoe? Misschien heb je een framwork of library gebruikt? -->
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


## Installatie

de code staat op een andere branch en daar kan je het vinden :https://github.com/lisagjh/voorhoede/tree/spike/contrasting-digital-dreamscape-Yu-Jing 





## Gebruik

## Bronnen

## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
