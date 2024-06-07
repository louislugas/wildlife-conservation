<script>
    import Scroll from "./Scroll.svelte"
    export let progress
</script>
<div>
    <h1 style:opacity={progress < 0.04 ? 1 : 0 }>
        Uncaged Conservation
    </h1>
    <h3 style:opacity={progress < 0.08 ? 1 : 0 }>
        An inclusive audio-visual exploration<br>of wildlife marketplaces
    </h3>
</div>
<Scroll />

<style>
    div {
        transform:translateY(-30%);
        width:88%;
        max-width: 800px;
    }
    h1 {
        font-family: "Calistoga", serif;
        font-size: 6rem;
        margin:0;
        margin-bottom: 1rem;
        font-weight: 400;
        line-height:5.5rem;
        text-align: center;
        transition:opacity 500ms ease-in-out;
    }
    h3 {
        font-family: "Quicksand", sans-serif;
        font-size: 2rem;
        font-weight: 400;
        margin:0;
        text-align: center;
        transition:opacity 500ms ease-in-out;
    }

    @media only screen and (max-width: 500px) {
        div {
            transform:translateY(-50%);
        }
        h1 {
            font-size: 3.5rem;
            line-height: 3rem;
        }
        h3 {
            font-size:1rem
        }
    }
</style>