<script>
    import Search from './parts/Search.svelte';
    import Location from './parts/Location.svelte';
    import Weather from './parts/Weather.svelte';
    import Wind from './parts/Wind.svelte';
    import Sun from './parts/Sun.svelte';

    import {data} from '../stores';
</script>

<main class="sw-city sw-container">
    {#if $data && $data.cod === 200}
        <div class="sw-content">
            <Location/>
            <Weather/>
            <Wind/>
            <Sun/>
        </div>
    {:else}
        <div class="sw-error">
            <h1>Sorry</h1>
            <h2>Something went wrong. Please try again.</h2>
            <Search/>
        </div>
    {/if}
</main>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-content {
        display: grid;
        grid-template-areas: "location weather" "wind sun";
        grid-template-columns: 1fr 1fr;
        grid-row-gap: 60px;
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