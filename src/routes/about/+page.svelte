<script>
    import IoLogoGithub from 'svelte-icons/io/IoLogoGithub.svelte'
    import IoLogoLinkedin from 'svelte-icons/io/IoLogoLinkedin.svelte'
</script>

<section class="container_about">
    <div class="section_about">
        <h2>Sobre</h2>
        <p>CineWacth se trata de um projeto pessoal, criado por <a href="https://github.com/pedrosrc" target="_blamnk">Pedro Leonardo</a>, onde o intuinto é demonstrar meus conhecimentos. Nesse projeto está sendo consumido uma API da <a href="https://developers.themoviedb.org/3" target="_blank">TheMovieDB</a>, onde podemos ver os filmes em cartazes no cinema no Brasil e ver detalhes e favorita-los. Modifiquei, reconstrui e aprimorei partes desse projeto, espero que gostem e me acompanhem nas redes socias:</p>
        <ul>
            <li>
                <a href="https://github.com/pedrosrc" target="_blank"> <IoLogoGithub/></a>
            </li>
            <li>
                <a href="https://www.linkedin.com/in/pedroleodev" target="_blank"><IoLogoLinkedin/></a>
            </li>
        </ul>
    </div>
</section>

<style>
.container_about{
    display: flex;
    justify-content:center;
}
.section_about{
    width: 1000px;
    margin-top: 5em;
    text-align: center;
}
.section_about p {
    font-size: 1.3em;
}
.section_about a{
    text-decoration: none;
}
.section_about p > a{
    color: blueviolet;
}
.section_about ul {
    display: flex;
    justify-content: center;
    align-items: center;  
}
.section_about li{
    margin: 5px;
    list-style: none;
    width: 40px;
}
@media(max-width: 720px){
    .section_about{
    width: 350px;
    background-color: blueviolet;
    padding: 10px;
    border-radius: 15px
    
}
.section_about p {
    font-size: 1.1em;
    text-align: justify;
}
.section_about p > a{
    color: #000;
    font-weight: bold;
}
}

</style>