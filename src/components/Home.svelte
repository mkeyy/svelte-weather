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
        grid-area: content;
    }

    .sw-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100%;
    }

    h1 {
        font-size: 100px;
        line-height: 1.1;
        margin: 0 0 20px;
    }
</style>