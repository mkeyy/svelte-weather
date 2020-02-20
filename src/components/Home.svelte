<script>
    import Search from './Search.svelte';
</script>

<div class="sw-app sw-app--home">
    <div class="sw-container">
        <div class="sw-home">
            <h1>Weather App</h1>
            <Search/>
        </div>
    </div>
</div>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    h1 {
        font-size: 100px;
        margin: 0 0 30px;
    }
</style>