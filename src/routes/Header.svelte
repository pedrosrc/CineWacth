<script>
    // @ts-nocheck

    import MdCollectionsBookmark from "svelte-icons/md/MdCollectionsBookmark.svelte";
    import MdInfo from "svelte-icons/md/MdInfo.svelte";

    let isOpen = false;

    function toggleMenu() {
        isOpen = !isOpen;
    }
</script>

<header>
    <div>
        <a href="/">
            <h1>Cine<i>Wacth</i></h1>
        </a>
    </div>
    <button on:click={toggleMenu} class="toggleButton">☰</button>
    <nav class="desk-nav">
        <li><a href="/about"><MdInfo /></a></li>
        <li>
            <a href="/list"><MdCollectionsBookmark /></a>
        </li>
    </nav>
    <nav class:open={isOpen} class="mobile-nav">
        <ul>
            <li><a href="/about"> <i><MdInfo /></i> Informações</a></li>
            <li>
                <a href="/list">
                    <i><MdCollectionsBookmark /></i> Minha lista</a
                >
            </li>
        </ul>
    </nav>
</header>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Audiowide&display=swap");

    :global(.svelte-fluid-header--button) {
        color: grey;
    }
    :global(.svelte-fluid-header--button:hover) {
        color: grey;
    }
    header {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-wrap: wrap;
        background-color: #010409;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    }
    a {
        display: flex;
        align-items: center;
        width: 100%;
        text-decoration: none;
        color: transparent;
        color: #fff;
        gap: 5px;
    }
    a > h1 {
        color: white;
    }
    header li {
        list-style: none;
        width: 30px;
        margin-right: 50px;
    }
    header h1 {
        font-family: "Audiowide", Arial, Helvetica, sans-serif;
        font-weight: normal;
    }
    header h1 i {
        font-style: normal;
        color: blueviolet;
    }
    nav {
        display: flex;
    }
    .mobile-nav {
        display: none;
    }
    .mobile-nav.open {
        display: flex;
    }

    .toggleButton {
        display: none;
        background: none;
        border: none;
        color: white;
        font-size: 1.5rem;
        cursor: pointer;
    }
    @media screen and (max-width: 720px) {
        header{
            padding: 0.8rem;
        }
        header li {
            margin: 0 5px;
            padding: 10px;
            width: 100%;
        }
        header li:hover{
            background-color: blueviolet;
            border-radius: 5px;
        }
        header li i {
            width: 20px;
        }

        .toggleButton {
            display: block;
            margin: 0 15px;
        }
        .desk-nav {
            display: none;
        }
        .mobile-nav {
            background-color: #010409;
        }
        .mobile-nav ul {
            display: flex;
            align-items: center;
            flex-direction: column;
            text-align: center;
            padding: 0;
        }
    }
</style>
