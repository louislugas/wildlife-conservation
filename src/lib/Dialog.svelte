<script>
export let id = 1
</script>
    <div class="bird-header">
        <div class="inner-header">
            <div class="left">
                <div class="bird-image">
                    <div>Bird image here</div>
                </div>
            </div>
            <div class="right">
                <h2>
                {
                    id == 1
                    ? "Ashy Tailorbird"
                    : id == 2
                    ? "Yellow Vented Bulbul"
                    : id == 3
                    ? "Common Grey Magpie"
                    : id == 4
                    ? "Green Leafbird"
                    : id == 5
                    ? "Straw Headed Bulbul"
                    : id == 6
                    ? "Bali Myna"
                    : id == 7
                    ? "Javan Pied Starling"
                    : ""
                }
            </h2>
            <h3>Indonesian Name</h3>
            <h3><em>Latin Name</em></h3>
            </div>
        
        </div>
    </div>
<section>
    <div class="audio">
        <audio controls>
            <source src="horse.mp3" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
    </div>
    <div class="midpiece">
        <div class="iucn">
            <p>IUCN Status</p>
            <p>Lorem ipsum</p>
        </div>
        <div class="cites">
            <p>Cites</p>
            <p>Lorem ipsum</p>
        </div>
        <div class="protect">
            <p>Indonesian Protection Status</p>
            <p>Lorem ipsum</p>
        </div>
    </div>
    
    
    <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Minus tenetur
        cumque adipisci numquam in quidem quis veniam sequi placeat quos facere a
        enim nulla quaerat perspiciatis totam, et tempora cum.
    </p>
    <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Minus tenetur
        cumque adipisci numquam in quidem quis veniam sequi placeat quos facere a
        enim nulla quaerat perspiciatis totam, et tempora cum.
    </p>
</section>

<style>
    section {
        margin:1.5rem;
    }
    p {
        font-family: "Quicksand", sans-serif;
    }
    .inner-header {
        margin:1rem;
        width:100%;
        display: flex;
    }
    .bird-header {
        display: flex;
        margin-bottom: 1rem;
        background-image: linear-gradient(green, transparent);
    }
    .audio {
        display: flex;
        justify-content: center;
        position: absolute;
        top:29%;
        left:0%;
        width:100%;
    }
    audio {
        width:90%;
        max-width:250px;
    }
    .midpiece {
        margin-top:3rem;
        display: flex;
        justify-content: space-evenly;
        text-align: center;
    }
    .midpiece > div {
        width:30%;
    }
    .midpiece > div > p:first-child {
        font-weight: 600;
        height:30px;
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
        background-color:coral;
        border-radius: 50%;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        color:black;
        font-family: sans-serif;
    }
    .bird-image > div {
        width:70%;
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
            top:22%;
        }
        p {
            font-size: 0.9rem;
        }
    }
</style>