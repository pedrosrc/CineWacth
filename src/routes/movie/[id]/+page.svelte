<script>
    import { page } from "$app/stores";
    import { onMount } from "svelte";
    import api from "../../../services/api";
    import StarRating from "@ernane/svelte-star-rating";
    import IoIosHeartEmpty from 'svelte-icons/io/IoIosHeartEmpty.svelte'
    import MdPlayCircleOutline from 'svelte-icons/md/MdPlayCircleOutline.svelte'

    let movieId = $page.params;
    let movie;

    onMount(async () => {
        const response = await api.get(`movie/${movieId.id}`, {
            params: {
                api_key: import.meta.env.VITE_KEYAPI,
                language: "pt-BR",
            },
        });
        movie = await response.data;
    });
</script>

<section class="container_movie">
    {#if movie}
        <div class="container_info">
            <div class="poster">
                <img
                    src={`https://image.tmdb.org/t/p/original/${movie.poster_path}`}
                    alt=""
                />
            </div>
            <div class="section_info">
                <h1>{movie.title}</h1>
                <span>Nota: {movie.vote_average.toFixed(1)}</span>
                <p>{movie.overview}</p>
                <div class="buttons">
                    <button><svg><IoIosHeartEmpty/></svg> Salvar</button>
                    <button><svg><MdPlayCircleOutline/></svg>Trailer</button>
                </div>
            </div>
        </div>
        <div class="container_location">
            <h2>Aonde assistir?</h2>
        </div>
    {:else}
        <div>Caregando...</div>
    {/if}
</section>

<style>
    .container_movie {
        position: relative;
    }
    .container_info {
        display: flex;
        width: 1000px;
        margin: auto;
        margin-top: 2em;
    }
    .container_location {
        display: flex;
        font-style: italic;
        flex-direction: column;
        width: 1000px;
        margin: auto;
        margin-top: 2em;
    }
    .poster img {
        width: 300px;
        border-radius: 15px;
    }
    .section_info {
        margin-left: 10px;
    }
    .section_info p{
        width: 30em;
        font-size: 1.2em;
    }
    .buttons{
        display: flex;
    }
    .buttons button{
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
    .buttons button svg{
        width: 20px;
        margin: 0;
        padding: 0;
    }
</style>
