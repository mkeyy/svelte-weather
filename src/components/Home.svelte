<script>
    import Search from './parts/Search.svelte';
</script>

<main class="sw-home sw-container">
    <div class="sw-content">
        <h1>Weather App</h1>
        <Search/>
    </div>
</main>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-home {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        grid-area: content;
    }

    h1 {
        text-align: center;
        margin: 0 0 20px;
    }
</style>