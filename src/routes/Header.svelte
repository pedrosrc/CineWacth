<script>
    import MdCollectionsBookmark from 'svelte-icons/md/MdCollectionsBookmark.svelte'
    import MdInfo from 'svelte-icons/md/MdInfo.svelte'
    import FaHome from 'svelte-icons/fa/FaHome.svelte'
</script>

<header>
    <div><a href="/"><li><FaHome/></li></a></div>
    <div><h1>CineWacth</h1></div>
    <nav>
        <li><MdInfo/></li>
        <li><MdCollectionsBookmark/></li>
    </nav>
</header>

<style>
    header{
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #010409;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    }
    header li{
        list-style: none;
        width: 30px;
    }
    header nav{
        display: flex;
    }
    nav > li{
        margin-right: 50px;
    }
</style>