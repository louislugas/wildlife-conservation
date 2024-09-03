<script>
    import Scroller from "@sveltejs/svelte-scroller";

    import * as d3 from "d3";

    import { Canvas } from "@threlte/core";
    import Scene from "$lib/Scene.svelte";
    import Title from "$lib/Title.svelte";
    import End from "$lib/End.svelte";
    import Dialog from "$lib/Dialog.svelte";
    import Scroll from "$lib/Scroll.svelte";
    import {onMount} from "svelte"

    import Fa from "svelte-fa"
    import { faVolumeMute, faVolumeUp } from "@fortawesome/free-solid-svg-icons";

    import bgMarketAudio from "$lib/audio/bg_audio_marketplace.mp3"
    

    let interact = false
    let playedOnce = false
    let id, dialog, select;

    let lang = "en"

    let count;
    let index = 0;
    let offset = 0.75;
    let progress = 0;
    let top = 0;
    let threshold = 0.8;
    let bottom = 0.9;

    let audio = false
    let bgAudio


    let zoom = 0;
    let open = false;

    let scaleProgress = d3
        .scaleLinear()
        .domain([0.2, 1])
        .range([0, 1])
        .clamp(true);

    $: if (index < 1) {
        zoom = 0;
    } else {
        zoom = scaleProgress(progress) * 90;
    }
    $: if (open) {
        dialog.showModal();
    }

    $: if (index > 1 && progress < 1 && interact) {
        if (!playedOnce) {
            playedOnce = true
            audio = true
        }
    } else {
        audio = false
    }

    $: if (progress > 1) {
        audio = false
    }

    $: if (bgAudio) {
        bgAudio.volume = 0.5
        if (audio) {
            bgAudio.play()
        } else if (!audio) {
            bgAudio.pause()
        }
    }

    function close() {
        open = false;
        dialog.close();
    }
</script>   

<svelte:body on:click={() => {interact = true}}></svelte:body>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=Calistoga&family=Quicksand:wght@300..700&display=swap"
        rel="stylesheet"
    />
</svelte:head>

<dialog bind:this={dialog}>
    <button on:click={close}>×</button>
    <Dialog bind:select bind:lang/>
</dialog>

<Title bind:lang/>




<Scroller
    {top}
    {threshold}
    {bottom}
    bind:count
    bind:index
    bind:offset
    bind:progress
    >
    <div slot="background" >
        <section class="background-section" style:opacity={progress > 1 ? 0 : 1}>
            <div class="vignette"></div>
            <img src="./images/background-export.png" alt="background" style:opacity={0.3}/>
            <!-- <img src="./images/checker-01.png" alt="background"> -->
        </section>

        <section class="ambiance background-section"
            style:opacity={progress < 1 ? 1 : 0}
            >
            <button class="volume" on:click={() => {audio = !audio}}>
            <Fa icon={audio ? faVolumeUp : faVolumeMute} color="#141414" scale="0.8"/>
            </button>
            <audio bind:this={bgAudio} loop src={bgMarketAudio}></audio>
        </section>

        <section class="cover background-section"
            style:opacity={index > 1 ? 0 : 1}
            >
        </section>
        <section class="background-section"
            style:opacity={progress > 1 ? 0 : 1}
            style:z-index={10}
            style:pointer-events="none"
            style:display="flex"
            style:align-items="flex-end"
        >
            <Scroll />
        </section>

        <section class="three-section background-section"
            style:opacity={progress > 1 ? 0 : 1}
            >
            <Canvas>
                <Scene bind:zoom bind:open bind:select/>
            </Canvas>
        </section>
    </div>

    <div slot="foreground">
        {#each Array(15) as _, i}
        <section>
            <!-- {index + 1}
            <br>
            {progress}
            <br>
            <p>ZOOM: {zoom}</p>
            <br>
            {offset} -->
        </section>
        {/each}
    </div>
</Scroller>

<End bind:lang/>




<style>
    * {
        -webkit-tap-highlight-color: transparent;
        -webkit-touch-callout: none;
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }
    
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    :global(body) {
        margin: 0;
        overflow-x: hidden;
        background-color: black;
    }
    .background-section {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100vw;
        height: 100vh;
        padding: 0;
        transition:opacity 500ms ease-in-out;
    }
    
    .intro {
        z-index: 10;
        /* font-family: sans-serif; */
        /* background: black; */
        width:100%;
        justify-content: center;
        /* transition: opacity 500ms ease-in-out; */
        /* position: absolute; */
        
       
    }
    .cover {
        background-image: linear-gradient(black 75%, transparent);
        width:100%;
        height:100vh;
        z-index: 10;
        pointer-events: none;
        /* border:1px solid red; */
    }
    .ambiance {   
        width:100%;
        height:100vh;
        z-index: 11;
        pointer-events: none;
        display: flex;
        justify-content: flex-end;
        align-items: flex-start;
        /* border:1px solid red; */
    }
    [slot="background"] {
        /* background-color: rgba(255, 62, 0, 0.05); */
        /* border-top: 2px solid #ff3e00;
        border-bottom: 2px solid #ff3e00; */
        font-size: 1.4em;
        overflow: hidden;
        width: 100vw;
        
    }

    [slot="foreground"] {
        pointer-events: none !important;
        width: 50px;
    }

    [slot="foreground"] section {
        pointer-events: none !important;
    }

    :global(svelte-scroller-foreground) {
        pointer-events: none;
    }
    :global(svelte-scroller-outer) {
        pointer-events: none;
    }
    :global(svelte-scroller-background) {
        pointer-events: auto;
    }
    section {
        height: 100vh;
        /* background-color: rgba(0, 0, 0, 0.5); */
        color: white;
        padding: 1em;
        margin: 0 0 2em 0;
    }
    dialog {
        z-index: 999;
        max-width: 600px;
        width: 80%;
        display:none;
        animation:vanish 1s;
        border-radius: 1rem;
        background-color: #131313;
        box-shadow: 1px 1px 10px 5px rgba(10,10,10,0.8);
        color:#f5f5f5;
        border:none;
        padding:0;
    }
    dialog[open] {
        display:block;
        animation:appear 1s;
    }
    dialog::backdrop {
        background-color: rgba(0, 0, 0, 0.6);
        backdrop-filter: blur(0px);
        animation:backdropvanish 500ms;
    }
    dialog[open]::backdrop {
        backdrop-filter: blur(2px);
        animation:backdropappear 500ms;
    }

    @keyframes appear {
        from {
            opacity: 0
        }
        to {
            opacity: 1
        }
    }
    @keyframes vanish {
        from {
            display:block;
            opacity: 1
        }
        to {
            opacity: 0;
            display:none;
        }
    }
    @keyframes backdropappear {
        from {
            opacity: 0;
            backdrop-filter: blur(0px);
        }
        to {
            opacity: 1;
            backdrop-filter: blur(2px);
        }
    }
    @keyframes backdropvanish {
        from {
            display:block;
            opacity: 1;
            backdrop-filter: blur(2px);
        }
        to {
            opacity: 0;
            display:none;
            backdrop-filter: blur(0px);
        }
    }
    .vignette {
        width: 100vw;
        height: 100vh;
        background-image: radial-gradient(transparent 30%,rgba(0,0,0,0.8) 80%);
        backdrop-filter: blur(2px);
        position: absolute;
    }
    button {
        position: absolute;
        right:1rem;
        background-color: transparent;
        border: none;
        color:#f5f5f5;
        cursor:pointer;
        font-size: 2rem;
    }
    .volume {
        position:relative;
        background-color:#f5f5f5;
        aspect-ratio: 1;
        border-radius:1rem;
        margin-top:1rem;
        margin-right:1rem;
        width:4rem;
        pointer-events: auto;
        cursor: pointer;
    }
</style>
