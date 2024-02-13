<script>
    import Header from "./Header.svelte";
    import { Toaster } from 'svelte-french-toast';
    import './style.css'

</script>

<div class="app">
    <Header/>
    <main>
        <Toaster/>
        <slot/>
    </main>
</div>