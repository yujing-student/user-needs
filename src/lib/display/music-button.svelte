<script>


import { onMount } from "svelte";

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

<div class="box">
    <section>

<!--        <h3>speel kerstmuziek</h3>-->
        <audio src="/jingle-bells.mp3" crossorigin="anonymous">
        </audio>

        <!--            <audio controls="" autoplay="" name="media"><source src="/jingle-bells.mp3" type="audio/mpeg"></audio>-->


        <button data-playing="false" class="play-btn" role="switch">
            <span>speel kerstmuziek</span>
        </button>
    </section>

</div>
<style>
    .box {
        display: flex;
        flex-direction: column;
        align-items: center;

        /*background-color: #f5f5f5;*/
    }
    .play-btn{
        background-color: var(--blue);
        color: var(--white);
        font-size: 2rem;
        box-shadow: 6px 5px 0px 3px;
        border-radius: 9px;
    }
</style>