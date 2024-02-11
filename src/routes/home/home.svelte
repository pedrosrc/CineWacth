<script>
    import { onMount } from "svelte";
    import api from "../../services/api";

    let movies = [];

    onMount(async () => {
        const response = await api.get("movie/now_playing", {
            params: {
                api_key: import.meta.env.VITE_APIKEY,
                language: "pt-BR",
                page: 1,
            },
        });
        movies = await response.data.results.slice(0, 10);
    });
</script>

<svelte:head>
    <title>CineWacth | Home</title>
    <meta name="Home" content="Svelte demo app" />
</svelte:head>

<section class="container_home">
    <h2>Filmes em Cartazes</h2>
    <div class="movies">
        {#each movies as movie}
            <div class="movie">
                <a href={`/movie/${movie.id}`}>
                    <img
                        src={`https://image.tmdb.org/t/p/original/${movie.poster_path}`}
                        alt={movie.title}
                    />
                    <span>{movie.title}</span>
                </a>
            </div>
        {/each}
    </div>
</section>

<style>
    h2 {
        font-size: 2em;
        text-align: start;
        margin-left: 5em;
        font-weight: lighter;
        font-style: italic;
        background-image: linear-gradient(80deg, blueviolet, #0d1117);
        background-repeat: no-repeat;
        background-size: 30% 3px;
        background-position: left bottom;
    }
    .movies {
        width: 100%;
        display: flex;
        margin: 0 auto;
        justify-content: center;
        flex-wrap: wrap;
        flex-direction: row;
    }
    .movie {
        display: flex;
        width: 300px;
        margin: 10px;
        flex-direction: column;
        transition: .3s;
    }
    .movie:hover{
        transform: translate(-3px,-5px);
        color: purple;
    }
    .movie a img {
        width: 250px;
    }
    .movie a{
        color: #fff;
        text-decoration: none;
        margin-top: 0.2em;
        width: 200px;
    }
    
    
</style>
