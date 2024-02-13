<script>
  import { onMount } from "svelte";
  import FaGrimace from "svelte-icons/fa/FaGrimace.svelte";
  import FaTrash from "svelte-icons/fa/FaTrash.svelte";
  import toast from "svelte-french-toast";

  let movies;

  onMount(async () => {
    const myList = localStorage.getItem("@cinewacth");
    // @ts-ignore
    movies = await JSON.parse(myList);
  });

  function handleRemove(id) {
    let filterMovie = movies.filter((item) => {
      return item.id !== id;
    });
    movies = filterMovie;
    localStorage.setItem("@cinewacth", JSON.stringify(filterMovie));
    toast.error("O filme foi retirado da sua lista!");
  }
</script>

<section class="container_list">
  <h2>Sua Lista</h2>
  {#if movies}
    <div class="movies">
      {#each movies as movie}
        <div class="movie">
          <a href={`/movie/${movie.id}`}>
            <img
              src={`https://image.tmdb.org/t/p/original/${movie.poster_path}`}
              alt={movie.title}
            />
            <div class="options">
              <span>{movie.title}</span>
              <button on:click={() => handleRemove(movie.id)}
                ><a href="/list"><FaTrash /></a></button
              >
            </div>
          </a>
        </div>
      {/each}
    </div>
  {:else}
    <div class="error">
      <i><FaGrimace /></i>
      <h3>Ops, parece que você não salvou nenhum filme!</h3>
      <p>Clique <a href="/">aqui</a> visualizar os filmes disponiveís</p>
    </div>
  {/if}
</section>

<style>
  .container_list {
    display: flex;
    flex-direction: column;
  }
  h2 {
    font-size: 2em;
    text-align: start;
    margin-left: 5em;
    font-weight: lighter;
    font-style: italic;
    background-image: linear-gradient(80deg, blueviolet, #0d1117);
    background-repeat: no-repeat;
    background-size: 20% 3px;
    background-position: left bottom;
  }
  .movies {
    width: 100%;
    display: flex;
    text-align: start;
    margin-left: 9em;
    flex-wrap: wrap;
    flex-direction: row;
  }
  .error {
    display: flex;
    align-items: center;
    flex-direction: column;
    margin: 0 auto;
    margin-top: 8em;
    justify-content: center;
    text-align: center;
  }
  .error i {
    width: 40px;
  }
  .error a {
    color: blueviolet;
  }
  .options {
    display: flex;
    width: 250px;
    justify-content: space-between;
  }
  .options button {
    display: flex;
    width: 30px;
    color: transparent;
    background-color: transparent;
    border: none;
    text-decoration: none;
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
    border-radius: 8px;
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
      margin-left: 0;
    }
    .movie {
      width: 160px;
      margin-top: 10px;
    }
    .movie a img {
      width: 150px;
      border-radius: 10px;
    }
    .options {
      width: 150px;
    }
    .options button{
      width: 35px;
    }
    .movie a {
      width: 150px;
      height: 250px;
      margin: 5px;
      font-size: 0.8em;
    }
  }
</style>
