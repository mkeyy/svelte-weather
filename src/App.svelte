<script>
    import Home from './components/Home.svelte';
    import City from './components/City.svelte';

    import {search, data} from './stores';

    let searchVal = null;

    search.subscribe(v => {
        searchVal = v;

        if (searchVal) {
            fetch(`${process.env.API_URL}?q=${$search}&appid=${process.env.API_KEY}&units=metric`)
                    .then(res => res.json())
                    .then(json => {
                        data.set(json);
                        {console.log($data)}
                    })
        }
    })
</script>

{#if !$data }
    <Home/>
{:else }
    <City/>
{/if}

<style lang="scss" global>
    @import "assets/styles/global.scss";

    .sw-app {
        min-height: 100vh;
        background: linear-gradient(120deg, $c-gradient-primary 10%, $c-gradient-secondary 60%, $c-gradient-tertiary 100%);;
    }
</style>