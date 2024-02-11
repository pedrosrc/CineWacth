<script>
  import { onMount } from "svelte";
  import FaGrimace from 'svelte-icons/fa/FaGrimace.svelte'

  let movies = [];

  onMount(async () => {
    const myList = localStorage.getItem("@cinewacth");
    // @ts-ignore
    movies = (await JSON.parse(myList)) || [];
  });
</script>

<section class="container_list">
  <h2>Sua Lista</h2>
  {#if movies.length>1}
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
  {:else}
    <div class="error">
      <i><FaGrimace/></i>
      <h3>Ops, parece que você não salvou nenhum filme!</h3>
      <p>Clique <a href="/">aqui</a> visualizar os filmes disponiveís</p>
    </div>
  {/if}
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
    margin:  auto;
    justify-content: center;
    flex-wrap: wrap;
    flex-direction: row;
    
  }
  .error{
    display: flex;
    align-items: center;
    flex-direction: column;
    margin: 0 auto;
    margin-top: 8em;
    justify-content: center;
    text-align: center;
  }
  .error i{
    width: 40px;
  }
  .error a{
    color: blueviolet;
  }
  .movie {
    display: flex;
    width: 300px;
    margin: 10px;
    flex-direction: column;
    transition: 0.3s;
  }
  .movie:hover {
    transform: translate(-3px, -5px);
    color: purple;
  }
  .movie a img {
    width: 250px;
  }
  .movie a {
    color: #fff;
    text-decoration: none;
    margin-top: 0.2em;
    width: 200px;
  }
  @media screen and (max-width: 720px) {
    h2 {
      font-size: 1.5em;
      text-align: start;
      margin-left: 1em;
    }
    .movies {
      align-items: center;
      justify-content: center;
    }
    .movie {
      width: 160px;
      margin-top: 10px;
    }
    .movie a img {
      width: 150px;
      border-radius: 10px;
    }
    .movie a {
      width: 150px;
      height: 250px;
      margin: 5px;
      font-size: 0.8em;
    }
  }
</style>
