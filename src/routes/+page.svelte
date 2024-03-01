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

  $: zoom = progress * 50;
  $: if (id) {
	dialog.showModal()
  }

  function close() {
	dialog.close()
	
  }
</script>

<dialog bind:this={dialog}>
	<h1>Lorem Ipsum {id}</h1>
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
		<img src="./images/background-test-resize.png" alt="background">
		<!-- <img src="./images/checker-01.png" alt="background"> -->
	</section>
    <section class="three-section">
      <Canvas>
        <Scene bind:zoom bind:id />
      </Canvas>
    </section>
  </div>

  <div slot="foreground">
    {#each Array(5) as _, i}
      <section>
        {index + 1}<br />{progress}<br />{(i * 1) / 5}<br />{(i * 1) / 5 +
          1 / 5}
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
