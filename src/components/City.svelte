<script>
    import Search from './parts/Search.svelte';
    import Date from './parts/Date.svelte';
    import Location from './parts/Location.svelte';
    import Weather from './parts/Weather.svelte';
    import Wind from './parts/Wind.svelte';
    import Sun from './parts/Sun.svelte';

    import {data} from '../stores';
</script>

<div class="sw-app sw-app--city">
    <div class="sw-container">
        {#if $data && $data.cod === 200}
            <div class="sw-city">
                <header class="sw-header">
                    <Search header="true"/>
                    <Date/>
                </header>

                <main class="sw-main">
                    <Location/>
                    <Weather/>
                    <Wind/>
                    <Sun/>
                </main>
            </div>
        {:else}
            <div class="sw-error">
                <h1>Sorry</h1>
                <h2>Something went wrong. Please try again.</h2>
                <Search/>
            </div>
        {/if}
    </div>
</div>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 40px 0 20px;
    }

    .sw-main {
        display: grid;
        grid-template-areas: "location weather" "wind sun";
        grid-template-columns: 1fr 1fr;
        padding: 50px 0;
    }

    .sw-error {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        min-height: 100vh;

        h2 {
            margin: 0 0 20px;
        }
    }
</style>