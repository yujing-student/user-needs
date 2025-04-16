> _Fork_ deze leertaak en ga aan de slag. 
Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. 
De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# Creative spikes
<!-- Geef je project een titel en schrijf in één zin wat het is -->
Scroll driven animations spike 1 livelink: https://user-needs-six.vercel.app/members

View transitions api spike 2 livelink:https://user-needs-bhvnj6iuq-yu-jing-projects-0dab48b4.vercel.app/members

christmas web audio Spike 3 livelink :https://user-needs-nmi3vl7i3-yu-jing-projects-0dab48b4.vercel.app/members 

testspike livelink:https://user-needs-j1qjlhd6j-yu-jing-projects-0dab48b4.vercel.app/members

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

Scroll driven animations spike 1 livelink https://user-needs-six.vercel.app/members

View transitions api spike 2 livelink:https://user-needs-bhvnj6iuq-yu-jing-projects-0dab48b4.vercel.app/members

christmas web audio testspike  livelink :https://user-needs-nmi3vl7i3-yu-jing-projects-0dab48b4.vercel.app/members 

christmas web audio Spike waar de cards bewegen 4  livelink:https://user-needs-j1qjlhd6j-yu-jing-projects-0dab48b4.vercel.app/members

## Kenmerken
<!-- Bij Kenmerken staat welke technieken zijn gebruikt en hoe. Wat is de HTML structuur? Wat zijn de belangrijkste dingen in CSS? Wat is er met Javascript gedaan en hoe? Misschien heb je een framwork of library gebruikt? -->

## spike 1
Mijn eerste spike is een scroll driven animation voor de cards met als thema contrasting colour dreaming <br>
in mijn eerdere versies had ik dat ik de cards een andere kleur wilde geven alleen bleek uit de usertest dat dit toch niet zo handig is zie hier de link naar wat ik eerrst had bij `designkeuzes`:  https://github.com/lisagjh/voorhoede/pull/43
In de [pull request]([https://github.com/lisagjh/voorhoede/pull/43](https://github.com/lisagjh/voorhoede/pull/43)) kan je zien hoe ik getest heb en waar ik naar gekeken heb om dit te realiseren

livelink: https://user-needs-six.vercel.app/members

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

## spike 2
Mijn 2de animatie heb ik met view transitions gemaakt waarin  ik een rotate gebruikt heb en `document.startviewTransitions` zodat als je op de knop `maak mij recht` klikt dat er een smooth overgang is
de kaartjes draaien als je naar beneden scrolt en stoppen met draaien als je niet scrollt 

livelink: livelink:https://user-needs-bhvnj6iuq-yu-jing-projects-0dab48b4.vercel.app/members

<h2>video van de animaite</h2>


video :


https://github-production-user-asset-6210df.s3.amazonaws.com/100352887/395249980-98195a00-5fd8-442e-97dc-022bae9984ad.mp4?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241218%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241218T163912Z&X-Amz-Expires=300&X-Amz-Signature=c0f747c2c35de27c015bff1129a964b1817bfc0e966863e22c612f156390948e&X-Amz-SignedHeaders=host

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

### spike 3

<h2>Volledige animatie als video</h2>

https://github.com/user-attachments/assets/6ee466c4-0def-4760-943e-90764b51e558


<h2>Code van de animatie</h2>

web api 
````javascript

onMount(async () => {
    // Cross browser

    // link inspiration :https://codepen.io/baumannzone/pen/OJyBaPK
    const AudioContext = window.AudioContext || window.webkitAudioContext;
    let audioCtx;

    // load some sound
    const audioElement = document.querySelector("audio");
    let track;

    const playButton = document.querySelector(".play-btn");

    // play pause audio
    playButton.addEventListener(
        "click",
        (ev) => {
            if (!audioCtx) {
                init();
            }

            // check if context is in suspended state (autoplay policy)
            if (audioCtx.state === "suspended") {
                audioCtx.resume();
            }

            if (ev.currentTarget.dataset.playing === "false") {
                audioElement.play();
                ev.currentTarget.dataset.playing = "true";
            } else if (ev.currentTarget.dataset.playing === "true") {
                audioElement.pause();
                ev.currentTarget.dataset.playing = "false";
            }
        },
        false
    );

    // if track ends
    audioElement.addEventListener(
        "ended",
        () => {
            playButton.dataset.playing = "false";
            playButton.setAttribute("aria-checked", "false");
        },
        false
    );

    function init() {
        audioCtx = new AudioContext();
        track = audioCtx.createMediaElementSource(audioElement);

        // Volume
        // https://developer.mozilla.org/en-US/docs/Web/API/GainNode
        const gainNode = audioCtx.createGain();
        // Connect
        track.connect(gainNode).connect(audioCtx.destination);
    }
});
</script>
````
html code
````html
<div class="box">
    <section>

        <audio src="/jingle-bells.mp3" crossorigin="anonymous">
        </audio>
        <button data-playing="false" class="play-btn" role="switch">
            <span>speel kerstmuziek</span>
        </button>
    </section>

</div>
````

css code voor het stylen van de button

````css
.box {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 2rem;

        /*background-color: #f5f5f5;*/
    }

    button {
        display: inline-block;
        -webkit-box-sizing:border-box;
        -moz-box-sizing:border-box;
        box-sizing:border-box;
        min-width:100px;
        padding: 22px 33px;
        font-family: 'Lobster', cursive;
        font-size: 26px;
        line-height: 26px;
        text-decoration: none;
        color: #FFF;
        text-shadow: 0 1px 2px rgba(0,0,0,0.75);
        background: #5e0d0c;
        outline: none;
        border-radius: 15px;
        border: 1px solid #4c0300;
        box-shadow:
                inset 1px 1px 0px rgba(255,255,255,0.25), /* highlight */
                inset 0 0 6px #a23227, /* inner glow */
                inset 0 80px 80px -40px #ac3223, /* gradient */
                1px 1px 3px rgba(0,0,0,0.75); /* shadow */

        position: relative;
        overflow: visible; /* IE9 & 10 */
        -webkit-transition: 500ms linear;
        -moz-transition: 500ms linear;
        -o-transition: 500ms linear;
        transition: 500ms linear;
    }

    button::before {
        content: '';
        display: block;
        position: absolute;
        top: -7px;
        left: -3px;
        right: 0;
        height: 23px;
        background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACsAAAAXCAYAAACS5bYWAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAABFpJREFUeNrUV0tIo1cUvpkYjQ4xxSA6DxuNqG0dtaUKOgs3s6i0dFd3pSsXdjeIixakiGA34sZuXCkoONLFwJTK4GMYLYXg29gatTpiXurkbd7vv9/5ub+IxuhA7eiFQ5Kbc8/57ne/e87/ywRBYLdl3GG3aNwqsLJ0k0tLS+fmcnNzWUVFBVMoFGx2djarvLxcm5OTw+bm5iytra2xc4ExNjY27iqVyvvwK6CpeDzuCYVC1urq6qDA9UcfPp+PHR4esmAwKK6tr68/l5/8rgQ2Ozub1dbWyiYmJooaGxt/VqvV38jlchX9l0qlwoFA4DWS/RKLxRxFRUVf5+XlPcaaT2AP0sVPJBL2SCRiAPBpu93+vKamZo/Ae71eZjabWV1dXVqw7CKwp43ksrCw8Bhg7MJ/PLDZ5PHx8cz29vYT5JGD/bSYLgTrcDgYdk6siSc6NjZWDaAe4ZoHQL+cmZnRpZPnhWDpD8kw7uKo9ML/NMCsd2tr61vkzboMrEyv138M7TyLRqMWMBsX3sMgaZhMpp+AR5EJrCocDpuEGzKg4x8khs+CVWxubvZfR9JkMik4nU7BarUKLpeLmLsKuwIqTLynp4fqmIzASrqQT09Pf1VVVfX0KsWZ6uHBwQHTaDSsoKAgo6/H4xHLEcrVyRwuEisrKzs5XrrIVAVwiUVDKRRrL+YI32ewdVhMApuHWvcj6vids6J2u90MF4yBHUZNgKoEBaRBQalJqFSqtJfUYrGIlQX+ydXVVTN+u0tKSjQNDQ1axJVl2iTypebn55d7e3v/kqoDgZU1NTU9LCws/Py0M+2ekuGincxJ3yF+18jIyHJLS0slQJUWFxczrBeBE0vE5tHRkbixlZWVfSR8gTX/0P5gH7S1tX3Z3t7+BW8qAvwSfr8/jA0EIRM/qoFtampqbW9vTw+XA+ojUruVd3Z2tvb19T2TQFEim81GgVJoCvvj4+NLOJZgaWmpemdn5y3a6BbcnJDAw8HBwac6ne6eqCW5XDwB3qVSqM9/DAwMUNy/eVLabT7sI25qwgujThCBhWE+mAt2yNc4SQKSZrOQQE1HS22VJkmPAGTr7+//fX19fRk+Zgq0trbGeFAKEAQT98BSqKOj47vm5uaa/Px8JeIk4GcaHh6eWlxcfAU/A8xG67BxAX3fwdcbYUpSDJ06Z49Ak8ZC3OL8f3YiA4PBYKdLQ2AJ9OTk5GpXV9cQiCVh79M94QtlPLDUE/1gPNrd3f0W33W4cBoco48zQuy/IZYAMnGqlSc4c66L9JruQUaSARXeT8HGKzxAqFBekni6+h46+pMzGiJGMgTOJh1yU/KNEGDvZWvfBawkA9ppwGg0mrRa7SOI2g+gxOgbJIpdFpj72PnxSnPX8vqRxTURgBQWKisrH+GThOm+CtAzoK/9/Uiqq/6hoaHfdnd3jaOjo7/yY7yxbwqkWy3sQzpS2C6YirwvUJk0y7hurfyGRrnduPGvAAMASmo8wzeVwfsAAAAASUVORK5CYII=) no-repeat 0 0,
        url(data:image/png;base64,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) no-repeat 50% 0,
        url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACEAAAAXCAYAAACFxybfAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAodJREFUeNrsVb1rWlEUv2pN/GqspKRSKFYXWzEloIWif0Fn6dJChQ7OQil0qd3EzcEpg0OgdHDr4CQODk7VRlLMEIVqApX4We0zflR9/Z1Ui4T34ksaaAYP/Hzc673n/M6550PG8zz73yKjn0wm83fDYDAwo9HINBrNnwOQg4MDs0ql2lQqlfdAWont7ng8Pjw+Ps44nc4G1pI9EXWaSOzt7TGO42aH5Pv7+08ajUZ0MBiUeXEZd7vdL5VK5fX29rZ+5tQiEmdxKrlcjsEYczgcynK5/BKKv/IXFNz/XiqVXkHdjUuRIA9SqdRD8or/R8Ez9fr9fqHVakUR4c2z0REjIQuHw2ZcrPBXLCA0RHTezEdHjIQqkUhEr9I4HOILhQLf6/VoOUFEvDMiQiToDx1Cdz+bzZ6bUFarlel0OkkVUK/XWbvdPoVer5fh3ntsfwJ+CJ2XA4p0Op1bpBgJyxDehQQ6nQ5DZXHBYDBZq9V+EhFUndnr9drEqoc2bwJbwGPgtohuVSwWe2Gz2TZMJpNgRKi6qtUqg2EWj8dTgUDgo0KhWPN4PC70EvXOzs67fD6/S6kiRIKeZA1YJ2MiJNbdbvfTUCjkV6vVK2hcDF8GI2w0GrGTkxM2HA5PDxaLxSOfz/cWEfk81X0XIMMFgJJ/srBjCgk8IdcfuVyuZ36//7nFYtkQyAMumUzuRiKRD0jMFLa+AZOpYwqgB/ziBVqmVBKUO7eAB/R0WG/Z7XaTVqtdbTabHJL6EK2djBaBPHA0NSqpbUsiMUeEBgpF4Q5AbZrmSJ/yEWgBTaBNHl9kdkgmMUeG7qwAq9PqovceTA3zlxlgsuswyuXsGsiSxJLEkoSY/BZgAEjRodi+uBruAAAAAElFTkSuQmCC) no-repeat 100% 0;

    }
    button:hover {
        background: #a61715;
        text-shadow: 0 1px 2px rgba(0,0,0,0.75), 0 0 40px #FFF;
        box-shadow:
                inset 1px 1px 0px rgba(255,255,255,0.25), /* highlight */
                inset 0 0 6px #da3b2c, /* inner glow */
                inset 0 80px 80px -40px #dd4330, /* gradient */
                1px 1px 3px rgba(0,0,0,0.75); /* shadow */

    }
    button:focus {
        outline: none; /*FF*/
    }
    button:active {
        box-shadow:
                inset 1px 1px 0px rgba(255,255,255,0.25), /* highlight */
                inset 0 0 6px #da3b2c, /* inner glow */
                inset 0 80px 80px -40px #dd4330, /* gradient */
                0px 1px 0px rgba(255,255,255,0.25); /* shadow */

        -webkit-transition: 50ms linear;
        -moz-transition: 50ms linear;
        -o-transition: 50ms linear;
        transition: 50ms linear;
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
