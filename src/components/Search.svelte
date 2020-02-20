<script>
    import AssetSVG from './AssetSVG.svelte';
    import icSearch from '../assets/img/ic-search.svg';

    import {search} from '../stores';

    export let icon;
    export let header = false;

    function handleSearch(e) {
        if (e.keyCode === 13) {
            search.set(e.target.value);
        }
    }
</script>

<div class={`sw-search${header ? ' sw-search--header' : ''}`}>
    <input type="search" placeholder="Search City" on:keypress={e => handleSearch(e)}>

    {#if icon}
        <button>
            <AssetSVG svgSRC={icSearch} classes="ic-search"/>
        </button>
    {/if}
</div>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-search {
        display: flex;
        min-width: 300px;
    }

    input[type="search"] {
        width: 100%;
        font-size: 18px;
        font-weight: 400;
        line-height: 1.2;
        color: $c-secondary;
        border: none;
        background-color: rgba($c-secondary, 0.2);
        outline: none;
        padding: 15px 50px;
        margin: 0 80px;

        &::placeholder {
            color: rgba($c-secondary, 0.6);
        }
    }

    .sw-search--header input[type="search"] {
        font-size: 14px;
        padding: 10px 15px;
        margin: 0;
    }

</style>