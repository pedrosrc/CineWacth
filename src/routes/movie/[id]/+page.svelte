<script>
    import { page } from "$app/stores";
    import { onMount } from "svelte";
    import api from "../../../services/api";

    let movieId = $page.params;
    let movie;
    let imagemUrl= '';

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

<section>
    {#if movie}
        <div class="container_background">
        </div>
        <div class="container_info">
            <div class="poster">
                <img src="" alt="" />
            </div>
            <div class="section_">
                <h1>{movie.title}</h1>
                <span>Nota</span>
                <p>
                    Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                    Beatae veniam qui laboriosam totam dolore inventore tempore
                    minus magnam, exercitationem ab perspiciatis provident earum
                    voluptas, eius mollitia facilis illum sed est?
                </p>
                <div>
                    <button>Salvar</button>
                    <button>Trailer</button>
                </div>
            </div>
        </div>
    {:else}
        <div>Caregando...</div>
    {/if}
</section>

<style>
    .container_background {
        height: 100vh; /* Ajuste conforme necessário */
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-image: url({imagemUrl});
    }
</style>
