<script>
    import Location from './parts/Location.svelte';
    import Weather from './parts/Weather.svelte';
    import Wind from './parts/Wind.svelte';
    import Sun from './parts/Sun.svelte';
</script>

<main class="sw-city sw-container">
    <div class="sw-content">
        <Location/>
        <Weather/>
        <Wind/>
        <Sun/>
    </div>
</main>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-city {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .sw-content {
        display: grid;
        grid-template-areas: "location" "weather" "wind" "sun";
        grid-template-columns: auto;
        grid-row-gap: 50px;
        width: 100%;
        padding: 50px 0;

        @media (min-width: $media-sm) {
            grid-template-areas: "location weather" "wind sun";
            grid-template-columns: repeat(2, 1fr);
            grid-row-gap: 60px;
        }
    }
</style>