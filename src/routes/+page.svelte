<script>
    import Scroller from "@sveltejs/svelte-scroller";

    import * as d3 from "d3";

    import { Canvas } from "@threlte/core";
    import Scene from "$lib/Scene.svelte";
    import Title from "$lib/Title.svelte";
    import Dialog from "$lib/Dialog.svelte";

    let id, dialog, select;

    let count;
    let index;
    let offset;
    let progress;
    let top = 0;
    let threshold = 0.8;
    let bottom = 0.9;

    let zoom = 0;
    let open = false;

    let scaleProgress = d3
        .scaleLinear()
        .domain([0.3, 1])
        .range([0, 1])
        .clamp(true);

    $: if (index < 3) {
        zoom = 0;
    } else {
        zoom = scaleProgress(progress) * 90;
    }
    $: if (open) {
        dialog.showModal();
    }

    function close() {
        open = false;
        dialog.close();
    }
</script>   

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
    <Dialog bind:select/>
</dialog>

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

        <section
        class="intro background-section"
        style:opacity={progress < 0.15 ? 1 : 0}
        style:display={progress < 0.2 ? "flex" : "none"}
        style:top="{progress * -500}px"
        style:flex-direction="column"
        >
            <Title bind:progress />
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
        {#each Array(10) as _, i}
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

<div style:width="88%" style:margin="0 auto" style:max-width="650px" style:margin-bottom="8rem">
    <p style:color="white">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolore ducimus maxime libero eveniet et ab sequi fugit! Tenetur autem qui, quasi, at perspiciatis sapiente amet est id earum maxime exercitationem.</p>

    <p style:color="white">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Repellat esse dignissimos ullam eum molestiae, tempora itaque iure sit obcaecati tempore rem deleniti ut nihil optio voluptatibus eligendi. Illum repellat dignissimos corporis ab excepturi non minus animi eligendi reiciendis itaque ipsa, quasi aperiam tempora, fuga ratione porro libero maiores sit quibusdam!</p>

    <p style:color="white">Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus vero laborum quod accusantium officia incidunt!</p>

    <p style:color="white">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Reprehenderit optio nostrum mollitia eius, alias ducimus sit animi repellat quod incidunt voluptatum nisi amet accusamus minus eos non necessitatibus? Consectetur, impedit? Aperiam perferendis tempore neque quasi quod voluptas vero ducimus voluptate mollitia eius officiis, eos architecto odit ea qui perspiciatis ratione, eaque exercitationem rerum sunt similique alias quibusdam! Voluptatum, atque reprehenderit.</p>

</div>


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
    p {
        color:white;
        font-family: sans-serif;
        line-height: 1.5rem;
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
        font-family: sans-serif;
        background: linear-gradient(black 75%, transparent 110%);
        height: 120vh;
        transition: opacity 500ms ease-in-out;
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
        height: 80vh;
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
</style>
