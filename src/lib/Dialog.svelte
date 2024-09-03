<script>
import {bird} from '$lib/bird'
export let select = 1
export let lang
export let lselect = 0

$: if(lang == "en") {
        lselect = 0
    } else {
        lselect = 1
    }

import ashytailorbird from '$lib/images/pp_ashy_tailorbird.jpg'
import yellowventedbulbul from '$lib/images/pp_yellow_vented_bulbul.jpg'
import commongreenmagpie from '$lib/images/pp_common_green_magpie.jpg'
import greatergreenleafbird from '$lib/images/pp_greater_green_leafbird.jpg'
import strawheadedbulbul from '$lib/images/pp_straw_headed_bulbul.jpg'
import balimyna from '$lib/images/pp_bali_myna.jpg'
import javanpiedstarling from '$lib/images/pp_javan_pied_starling.jpg'

let imgArr = [
    ashytailorbird, 
    yellowventedbulbul, 
    commongreenmagpie, 
    greatergreenleafbird,
    strawheadedbulbul,
    balimyna,
    javanpiedstarling
    ]

</script>
    <div class="bird-header" style:background-image="linear-gradient({bird[select-1].color}, transparent)">
        <div class="inner-header">
            <div class="left">
                <div class="bird-image"
                    style:border-color="{
                    bird[select-1].color == "green" ? "lightgreen" : 
                    bird[select-1].color == "orange" ? "gold" : 
                    "coral" 
                    }"
                >
                    <img src={imgArr[select-1]} alt="{bird[select-1].name.english} - {bird[select-1].name.indonesian}">
                </div>
            </div>
            <div class="right">
                <h2>{lang == "en" ? bird[select-1].name.english : bird[select-1].name.indonesian}</h2>
                <h3>{lang == "en" ? bird[select-1].name.indonesian : bird[select-1].name.english}</h3>
                <h3><em>{bird[select-1].name.latin}</em></h3>
            </div>
        
        </div>
    </div>
<section>
    <!-- <div class="audio">
        <audio controls>
            <source src="" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
    </div> -->
    <div class="midpiece">
        <div class="iucn">
            <p>IUCN Status</p>
            <p>{bird[select-1].iucn[lselect]}</p>
        </div>
        <div class="cites">
            <p>CITES Status</p>
            <p>{bird[select-1].cites[lselect]}</p>
        </div>
        <div class="protect">
            <p>Indonesian Protection Status</p>
            <p>{bird[select-1].indoprotect[lselect]}</p>
        </div>
    </div>
    <div class="desc">
        {#each bird[select-1].desc[lselect] as p}
            <p>{@html p}</p>
        {/each}
    </div>
</section>

<style>
    section {
        margin:1.5rem;
    }
    p {
        font-family: "Quicksand", sans-serif;
        line-height: 1.8rem;
    }
    .inner-header {
        margin:1rem;
        width:100%;
        display: flex;
    }
    .bird-header {
        display: flex;
        margin-bottom: 1rem;
    }
    .audio {
        display: flex;
        justify-content: center;
        position: absolute;
        top:23%;
        left:0%;
        width:100%;
    }
    audio {
        width:90%;
        max-width:250px;
    }
    .midpiece {
        margin-top:1rem;
        display: flex;
        justify-content: space-evenly;
        text-align: center;
    }
    .midpiece > div {
        width:30%;
    }
    .midpiece > div > p {
        line-height: 1rem;
    }
    .midpiece > div > p:first-child {
        font-weight: 600;
        height:35px;
    }
    .left {
        width:20%;
        margin-right: 1rem;
    }
    .right > h2 {
        font-family: "Calistoga", serif;
        font-weight: 400;
        margin-bottom: 0.5rem;
    }
    .right > h3 {
        font-family: 'Quicksand', serif;
        font-weight: 400;
        margin: 0;
        font-size: 1rem;
    }
    .bird-image {
        width:100%;
        aspect-ratio: 1;
        /* background-color:coral; */
        border-radius: 50%;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        color:black;
        font-family: sans-serif;
        overflow: hidden;
        border-width: 3px;
        border-style: solid;
    }
    .bird-image > img {
        width:100%;
        aspect-ratio: 1;
    }
    .desc {
        height:30vh;
        overflow-y: auto;
    }
    .desc::-webkit-scrollbar {
        width: 0.5rem;
        
    }    
    .desc::-webkit-scrollbar-thumb {
        background-color: darkgrey;
        border-radius: 0.5rem;
    }

    :global(strong) {
        color:rgb(255, 233, 145);
    }

    :global(a) {
        color:gold;
        font-weight:600;
    }

    :global(a:visited) {
        color:gold;
    }

    @media only screen and (max-width:500px) {
        .right > h2 {
            font-size:1.1rem;
            margin-top:0.5rem;
        }
        .right > h3 {
            font-size: 0.9rem;
        }
        .left {
            width:40%;
            margin-right: 1rem;
        }
        .midpiece {
            font-size: 0.9rem;
        }
        .audio {
            top:26%;
        }
        p {
            font-size: 0.9rem;
        }
    }
</style>