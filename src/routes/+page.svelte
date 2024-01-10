<script>
    import Home from "./home/home.svelte";
    import Header from "./header/header.svelte";
</script>
<main>
    <Header/>
    <Home/>
</main>
<style>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

    *{
        font-family: 'Montserrat', Arial;
        color: white;
    }
    main{
    background-color: #0D1117;
    width: 100%;
    overflow-x: hidden;
    }
</style>