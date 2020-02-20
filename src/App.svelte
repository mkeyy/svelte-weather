<script>
    import Home from './components/Home.svelte';
    import City from './components/City.svelte';

    import {search} from './stores';

    let searchVal = null;
    let city = null;

    search.subscribe(v => {
        searchVal = v;

        if (searchVal) {
            fetch(`${process.env.API_URL}?q=${$search}&appid=${process.env.API_KEY}&units=metric`)
                    .then(res => res.json())
                    .then(data => {
                        city = data;
                        {console.log(city)}
                    })
        }
    })
</script>

{#if !$search }
    <Home/>
{:else }
    <City {city}/>
{/if}

<style lang="scss" global>
    @import "assets/styles/global.scss";

    .sw-app {
        min-height: 100vh;
        background: linear-gradient(120deg, $c-gradient-primary 10%, $c-gradient-secondary 60%, $c-gradient-tertiary 100%);;
    }
</style>