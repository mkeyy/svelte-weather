<script>
    import Search from './parts/Search.svelte';
</script>

<div class="sw-error sw-container">
    <h1>Ooops!</h1>
    <span>Something went wrong. Try again.</span>
    <Search/>
</div>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-error {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        grid-area: content;
    }

    h1 {
        text-align: center;
        margin: 0 0 10px;
    }

    span {
        display: block;
        font-size: 20px;
        line-height: 1.1;
        text-align: center;
        margin: 0 0 40px;

        @media (min-width: $media-md) {
            font-size: 40px;
        }
    }
</style>