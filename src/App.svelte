<script>
    import Header from './components/Header.svelte';
    import Home from './components/Home.svelte';
    import City from './components/City.svelte';
    import Footer from './components/Footer.svelte';

    import {search, data} from './stores';

    let searchVal = null;

    search.subscribe(v => {
        searchVal = v;

        if (searchVal) {
            fetch(`${process.env.API_URL}?q=${$search}&appid=${process.env.API_KEY}&units=metric`)
                    .then(res => res.json())
                    .then(json => {
                        data.set(json);
                        {
                            console.log($data)
                        }
                    })
        }
    })
</script>

{#if !$data }
    <Home/>
{:else }
    <Header/>
    <City/>
{/if}

<Footer/>

<style lang="scss" global>
    @import "assets/styles/global.scss";

    .sw-app {
        position: relative;
        display: grid;
        grid-template-areas: "header" "content" "footer";
        grid-template-rows: 80px auto 55px;
        min-height: 100vh;
        background: linear-gradient(120deg, $c-gradient-primary 10%, $c-gradient-secondary 60%, $c-gradient-tertiary 100%);
    }
</style>