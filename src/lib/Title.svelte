<script>
    import Scroll from "./Scroll.svelte"
    // export let progress, index
    import imgBaliMyna from '$lib/images/bali-myna.png'
    import imgStrawHeadedBulbul from '$lib/images/straw-headed-bulbul.png'
    import imgAshyTailorbird from '$lib/images/ashy-tailorbird.png'

    export let lang = "en"

    function changLang(l) {
        lang = l
    }
</script>
<section style:background-color="black">
    <div class="title">
        <h1>
            {#if lang == "en"}
            Uncaged Conservation
            {:else}
            Konservasi yang Tidak Terkurung
            {/if}
        </h1>
        <h3>
            {#if lang == "en"}
            An inclusive audio-visual exploration<br>of wildlife marketplaces
            {:else}
            Sebuah eksplorasi audio-visual inklusif<br>tentang perdagangan satwa liar
            {/if}
        </h3>
        <p style:margin-top="2rem" style:text-align="center">Choose language:</p>
        <div class="button-container">
            <button 
                on:click={() => changLang("en")}
                style:background-color={lang == "en" ? "#f5f5f5" : "grey"}>
                English</button>
            <button 
                on:click={() => changLang("id")}
                style:background-color={lang == "en" ? "grey" : "#f5f5f5"}>
                Indonesian</button>
        </div>
        <Scroll />
    </div>
    <div class="img">
        <img src={imgBaliMyna} alt="bird divider bali myna">
    </div>

    <div> 
        {#if lang == "en"}
        <h2>
            Welcome to Uncaged Conservation
        </h2>
        <p>Through this collaborative work of art and science, we want to challenge the misconceptions about the illegal wildlife trade and the people involved. Why do people cage birds and is the appropriate response to the problem of wildlife trade in turn to cage humans in the form of incarceration?</p>

        <p>Immerse yourself in the website and experience what it is like to be in a bird market in Indonesia. Use your mouse to scroll through the website to encounter various species of birds. You can click on the birds to read more information and see additional pictures and recordings. Because of how rare some of these birds are, some do not have corresponding recordings. But you can still hear the ambient sounds of the market on the main page.</p>
        {:else}
        <h2>
            Selamat Datang
        </h2>
        <p>Melalui karya kolaboratif seni dan sains ini, kami ingin menjelaskan kesalahpahaman tentang perdagangan satwa liar dan orang-orang yang terlibat di dalamnya. Mengapa masyarakat mengurung burung dan apakah memenjarakan pelaku adalah solusi yang tepat untuk mengatasi perdagangan satwa liar?</p>

        <p>Telusuri website ini dan rasakan bagaimana rasanya berada di pasar burung di Indonesia. Gunakan mouse Anda untuk menelusuri situs web, dan Anda akan menemukan berbagai spesies burung. Anda dapat mengklik burung untuk membaca informasi lebih lanjut dan melihat video tambahan dan rekaman. Karena betapa langkanya beberapa burung ini, kami tidak dapat menayangkan rekamannya. Namun Anda masih bisa mendengar suara-suara di sekitar pasar di halaman utama website ini.</p>
        {/if}
    </div>

    <div class="img">
        <img src={imgAshyTailorbird} alt="bird divider ashy tailorbird">
    </div>
    

    <div>
    {#if lang == "en"}
        <h2>
            Species Profiles
        </h2>
        <p>We have chosen a range of species that are popular in trade for various reasons. Walk through the marketplace and pick a species in the cage to familiarise yourself with. These birds are embedded items in the cages and will be accompanied by details such as species identification and an account of cultural and ecological significance. As you move through the website, the birds are colour-coded according to IUCN threat level with critically endangered species having a red background. Some of these categories need more explaining, such as the <a target='_blank' class='link-article' href='https://en.wikipedia.org/wiki/IUCN_Red_List'>IUCN</a> and <a target='_blank' class='link-article' href='https://cites.org/eng/disc/what.php'>CITES</a>. </p>
        {:else}
        <h2>
            Profil Spesies
        </h2>
        <p>Kami telah memilih sejumlah spesies yang populer dalam perdagangan karena berbagai alasan. Jelajahi pasar dan pilih spesies di dalam kandang untuk dikenali. Burung-burung ini dimasukkan ke dalam sangkar dan akan disertai dengan rincian seperti identifikasi spesies dan penjelasan tentang signifikansi budaya dan ekologi. Beberapa kategori ini memerlukan penjelasan lebih lanjut, seperti <a target='_blank' class='link-article' href='https://en.wikipedia.org/wiki/IUCN_Red_List'>IUCN</a> dan <a target='_blank' class='link-article' href='https://cites.org/eng/disc/what.php'>CITES</a>.</p>
        {/if}
    </div>

    
    <div class="img">
        <img src={imgStrawHeadedBulbul} alt="bird divider straw headed bulbul">
    </div>
    

    <div>
    {#if lang == "en"}
        <h2>
            IUCN
        </h2>
        <p>The IUCN Red List is the most well-known assessment of species populations worldwide. Made up of non-governmental bodies and scientists from various institutions, it is seen as a global gold standard for monitoring the threats facing wild species. Classifications are made based on data about population numbers and the threats in their habitats, species are then classified into least concern, vulnerable, near threatened, endangered, critically endangered, and extinct in the wild.</p>

        <h2>
            CITES
        </h2>
        <p>CITES (the Convention on International Trade in Endangered Species of Wild Fauna and Flora) is an international agreement between governments. It aims to ensure that international trade in specimens of wild animals and plants does not threaten the species' survival.</p>
        {:else}
        <h2>
            IUCN
        </h2>
        <p>Daftar Merah IUCN adalah pengelompokan populasi spesies yang paling terkenal di seluruh dunia. Terdiri dari badan-badan non-pemerintah dan ilmuwan dari berbagai institusi, penilaian ini dipandang sebagai standar emas global untuk memantau ancaman yang dihadapi spesies liar. Spesies diklasifikasikan menjadi paling tidak dihiraukan, rentan, hampir terancam, hampir punah, sangat terancam punah, dan kemudian punah, berdasarkan jumlah populasi dan ancaman di habitatnya.</p>

        <h2>
            CITES
        </h2>
        <p>CITES (Konvensi Perdagangan Internasional Spesies Fauna dan Flora Liar yang Terancam Punah) adalah perjanjian internasional antar pemerintah. Tujuannya adalah untuk memastikan bahwa perdagangan internasional spesimen hewan dan tumbuhan liar tidak mengancam kelangsungan spesies tersebut.</p>
        {/if}
    </div>
</section>
<!-- <section class="cover"></section> -->


<style>
    a {
        color:gold;
        font-weight:600;
    }
    a:visited {
        color:gold;
    }
    div {
        /* transform:translateY(-30%); */
        width:88%;
        max-width: 800px;
        /* position: absolute; */
        transition: opacity 500ms ease-in-out;
        /* opacity:0; */
        margin-bottom:4rem;
        margin-top:4rem;
        color:white;
    }
    .title {
        height:100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
    .button-container {
        display: flex;
        margin:0 auto;
        justify-content: center;
        gap:0.5rem;
        width:fit-content;
        padding:0.5rem;
        border-radius:1.5rem;
        background-color: grey;
    }
    section {
        width:100%;
        display: flex;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .cover {
        background-image: linear-gradient(black 75%, transparent);
        width:100%;
        height:100px;
        /* border:1px solid red; */
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
    h2 {
        font-family: "Calistoga", serif;
        font-size: 1.5rem;
        font-weight: 400;
    }
    p {
        font-family: "Quicksand", sans-serif;
        font-size: 1rem;
        transition: opacity 500ms ease-in-out;
    }
    button {
        width:100px;
        height:40px;
        border-radius:1rem;
        border:none;
        cursor: pointer;
        font-family:"Quicksand", sans-serif;
        transition:background 200ms ease-in-out;
    }
    .img {
        width:150px;
        background-image: radial-gradient(circle at center, rgba(255, 217, 0, 0.4) 5%, transparent 55%);
    }
    img {
        width:100%;
        height:100%;
        object-fit: contain;
    }
    strong {
        color:rgb(255, 233, 145);
    }

    @media only screen and (max-width: 500px) {
        div {
            /* transform:translateY(-50%); */
        }
        h1 {
            font-size: 3.5rem;
            line-height: 3rem;
        }
        h3 {
            font-size:1rem
        }
        p {
            font-size: 0.8rem;
        }
    }
</style>