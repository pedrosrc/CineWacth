<script>
	import { onMount } from 'svelte';
    import api from '../../services/api';

    let movies = [];

    onMount( async() => {
        const response = await api.get('movie/now_playing', {
            params:{
                api_key: "e497db75384a8e566e73381e11b886e4",
                language: 'pt-BR',
                page: 1
            }
        });
        movies = await response.data.results.slice(0,10);
    })


</script>

<section>
    <h2>Filmes em Cartazes</h2>
    <div class="movies">
        {#each movies as movie}
            <div class="movie">
                <img src={`https://image.tmdb.org/t/p/original/${movie.poster_path}`} alt={movie.title}>
                <span>{movie.title}</span>
            </div>
        {/each}
    </div>
</section>


<style>
	h2 {
		font-size: 2em;
        text-align: left;
        font-weight: bolder;
        font-style: italic;
	}
    .movies{
        display: flex;
        margin: 0 auto;
        justify-content: center;
        flex-wrap: wrap;
        flex-direction: row;
    }
    .movie{
        display: flex;
        width: 350px;
        margin: 5px;
        flex-direction: column;
    }
    .movie > img{
        width: 200px;
    }
</style>
