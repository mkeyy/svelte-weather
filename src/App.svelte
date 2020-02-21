<script>
    import Header from './components/Header.svelte';
    import Home from './components/Home.svelte';
    import City from './components/City.svelte';
    import Error from './components/Error.svelte';
    import Footer from './components/Footer.svelte';

    import {search, data} from './stores';

    let loading = false;

    search.subscribe(() => {
        if ($search) {
            loading = true;
            fetch(`${process.env.API_URL}?q=${$search}&appid=${process.env.API_KEY}&units=metric`)
                    .then(res => res.json())
                    .then(json => {
                        data.set(json);
                        loading = false;
                    })
        }
    })
</script>

{#if !$search && !$data }
    <Home/>
{:else if $data && $data.cod === 200}
    <Header/>
    <City/>
{:else}
    <Error/>
{/if}

<Footer/>

<style lang="scss" global>
    @import "assets/styles/global.scss";

    .sw-app {
        position: relative;
        display: grid;
        grid-template-areas: "header" "content" "footer";
        grid-template-rows: auto 1fr auto;
        min-height: 100vh;
        background: linear-gradient(120deg, $c-gradient-primary 10%, $c-gradient-secondary 60%, $c-gradient-tertiary 100%);
    }
</style>