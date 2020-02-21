<script>
    import Search from './parts/Search.svelte';
</script>

<div class="sw-error sw-container">
    <h1>Ups!</h1>
    <span>We are sorry but something went wrong. Please try again.</span>
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

    h2 {
        text-align: center;
        margin: 0 0 20px;
    }

    span {
        display: block;
        font-size: 16px;
        line-height: 1.1;
        text-align: center;
        margin: 0 0 25px;
    }
</style>