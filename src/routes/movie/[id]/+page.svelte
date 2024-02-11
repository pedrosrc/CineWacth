<script>
    import { page } from "$app/stores";
    import { onMount } from "svelte";
    import api from "../../../services/api";
    import IoIosHeartEmpty from "svelte-icons/io/IoIosHeartEmpty.svelte";
    import MdPlayCircleOutline from "svelte-icons/md/MdPlayCircleOutline.svelte";
    // @ts-ignore
    import StarRating from "@ernane/svelte-star-rating";

    let movieId = $page.params;
    let movie;
    let scoreMovie;

    onMount(async () => {
        const response = await api.get(`movie/${movieId.id}`, {
            params: {
                api_key: import.meta.env.VITE_APIKEY,
                language: "pt-BR",
            },
        });
        movie = await response.data;
        scoreMovie = Number(movie.vote_average.toFixed(0))
        console.log(scoreMovie)
    });
    
    let config = {}

    $: config = {
        readOnly: true,
        countStars: 5,
        range: {
            min: 0,
            max: 5,
            step: 0.001,
        },
        score: (scoreMovie - 0.1 )/2,
        showScore: true,
        scoreFormat: function () {
            return `(${this.score.toFixed(1)}/${this.countStars})`;
        },
        name: "score",
        starConfig: {
            size: 20,
            fillColor: "#F9ED4F",
            strokeColor: "#BB8511",
            unfilledColor: "#FFF",
            strokeUnfilledColor: "#000",
        },
    };
</script>

<section class="container_movie">
    {#if movie}
        <div class="backdrop">
            <img
                src={`https://image.tmdb.org/t/p/original/${movie.backdrop_path}`}
                alt=""
            />
            <div class="overlay"></div>
        </div>

        <div class="container_info">
            <div class="poster">
                <img
                    src={`https://image.tmdb.org/t/p/original/${movie.poster_path}`}
                    alt=""
                />
            </div>
            <div class="section_info">
                <h1>{movie.title}</h1>
                <span class="rating"><StarRating {config}/></span>
                <p>{movie.overview}</p>
                <div class="buttons">
                    <button><svg><IoIosHeartEmpty /></svg> Salvar</button>
                    <button><svg><MdPlayCircleOutline /></svg>Trailer</button>
                </div>
            </div>
        </div>
    {:else}
        <div>Caregando...</div>
    {/if}
</section>

<style>
    .container_movie {
        position: relative;
        margin: 0;
    }
    .container_info {
        display: flex;
        width: 1200px;
        margin: auto;
        margin-top: 14em;
        margin-left: 16em;
        position: absolute;
        z-index: 2;
    }
    .backdrop {
        width: 100%;
        height: 500px;
        position: absolute;
        z-index: 1;
    }
    .backdrop img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: top;
    }
    .overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
            to bottom,
            rgba(13, 17, 23, 0) 0%,
            rgba(13, 17, 23, 1) 100%
        );
        pointer-events: none;
    }
    .poster img {
        width: 300px;
        border-radius: 15px;
    }
    .section_info {
        margin-left: 3em;
    }
    .section_info h1 {
        font-size: 2em;
    }
    .section_info p {
        width: 30em;
        font-size: 1.2em;
    }
    .rating{
        justify-content: left;
    }
    .buttons {
        display: flex;
    }
    .buttons button {
        display: flex;
        justify-content: center;
        align-items: center;
        border: none;
        width: 120px;
        height: 40px;
        margin-right: 10px;
        border-radius: 5px;
        background-color: blueviolet;
        color: #fff;
    }
    .buttons button svg {
        width: 20px;
        margin: 0;
        padding: 0;
    }
</style>
