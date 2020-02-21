<script>
    import Search from './parts/Search.svelte';
    import Date from './parts/Date.svelte';
</script>

<header class="sw-header sw-container">
    <Search header="true"/>
    <Date/>
</header>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-header {
        display: flex;
        flex-direction: column;
        grid-area: header;
        padding: 30px 15px 0;

        @media (min-width: $media-xs) {
            flex-direction: row;
            justify-content: space-between;
            align-items: center;
            padding: 40px 15px 0;
        }
    }
</style>
