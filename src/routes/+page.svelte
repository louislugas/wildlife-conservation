<script>
  import Scroller from "@sveltejs/svelte-scroller";

  import { Canvas } from "@threlte/core";
  import Scene from "$lib/Scene.svelte";

  let id, dialog

  let count;
  let index;
  let offset;
  let progress;
  let top = 0;
  let threshold = 0.8;
  let bottom = 0.9;

  let zoom = 0;
  let open = false

  $: zoom = progress * 50;
  $: if (open) {
	  dialog.showModal()
  }

  function close() {
    open = false
	  dialog.close()
  }
</script>

<dialog bind:this={dialog}>
	<h1>
    {
      id == 1 ? "Ashy Tailorbird" :
      id == 2 ? "Yellow Vented Bulbul" :
      id == 3 ? "Common Grey Magpie" :
      id == 4 ? "Green Leafbird" :
      id == 5 ? "Straw Headed Bulbul" :
      id == 6 ? "Bali Myna" :
      id == 7 ? "Javan Pied Starling" : ""
    }
  </h1>
	<button on:click={close}>Close</button>
	<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Minus tenetur cumque adipisci numquam in quidem quis veniam sequi placeat quos facere a enim nulla quaerat perspiciatis totam, et tempora cum.</p>
	<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Minus tenetur cumque adipisci numquam in quidem quis veniam sequi placeat quos facere a enim nulla quaerat perspiciatis totam, et tempora cum.</p>
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
  <div slot="background">
	<section
		style:position="absolute"
		style:display="flex"
		style:justify-content="center"
		style:align-items="center"
		style:width="100vw"
		style:height="100vh"
		style:padding="0"
	>
		<img src="./images/background-export.png" alt="background">
		<!-- <img src="./images/checker-01.png" alt="background"> -->
	</section>
    <section class="three-section">
      <Canvas>
        <Scene bind:zoom bind:id bind:open/>
      </Canvas>
    </section>
  </div>

  <div slot="foreground">
    {#each Array(7) as _, i}
      <section>
        {index + 1}
        <br>
        {progress}
        <br>
        {progress / 7}
        <br>
        {offset}
      </section>
    {/each}
  </div>
</Scroller>

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
    width:100%;
    height:100%;
    object-fit: cover;
  }
  :global(body) {
    margin: 0;
    overflow-x: hidden;
	background-color: black;
  }
  .three-section {
    width: 100vw;
    height: 100vh;
    position: absolute;
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
	z-index:999;
	max-width: 600px;
	width:80%;
  }
  dialog::backdrop {
	background-color: rgba(0,0,0,0.5);
  }
</style>
