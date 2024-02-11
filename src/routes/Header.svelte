<script>
    // @ts-nocheck

    import MdCollectionsBookmark from "svelte-icons/md/MdCollectionsBookmark.svelte";
    import MdInfo from "svelte-icons/md/MdInfo.svelte";
    import FaHome from "svelte-icons/fa/FaHome.svelte";
</script>

<header>
    <div>
        <a href="/">
            <h1>Cine<i>Wacth</i></h1>
        </a>
    </div>
    <nav>
        <li><a href="/about"><MdInfo /></a></li>
        <li>
            <a href="/list"><MdCollectionsBookmark /></a>
        </li>
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
        background-color: #010409;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    }
    a {
        text-decoration: none;
        color: transparent;
    }
    a > h1{
        color: white;
    }
    header li {
        list-style: none;
        width: 30px;
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
    nav > li {
        margin-right: 50px;
    }
    @media screen and (max-width: 720px) {

        header li {
            list-style: none;
            width: 20px;
            display: none;
        }
    }
</style>
