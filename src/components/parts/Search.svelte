<script>
    import AssetSVG from '../helpers/AssetSVG.svelte';
    import icSearch from '../../assets/img/ic-search.svg';

    import {search} from '../../stores';

    export let header = false;

    function handleSearch() {
        let value = document.getElementById('city-search').value;
        search.set(value);
    }
</script>

<div class={`sw-search${header ? ' sw-search--header' : ''}`}>
    <input id="city-search" type="search" placeholder="Search City"
           on:keypress={e => e.keyCode === 13 ? handleSearch() : ''}>

    <button on:click={()=> handleSearch()}>
        <AssetSVG svgSRC={icSearch} classes={`sw-svg--search${header ? ' sw-svg--search-small' : ''}`}/>
    </button>
</div>

<style lang="scss">
    @import "../../assets/styles/settings";

    .sw-search {
        position: relative;
        display: flex;
        width: 400px;
        margin: 0 auto;
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
        padding: 15px 50px 15px 20px;
        margin: 0 auto;

        &::placeholder {
            color: rgba($c-secondary, 0.6);
        }
    }

    button {
        position: absolute;
        top: 0;
        bottom: 0;
        right: 0;
        border: none;
        background-color: transparent;
        cursor: pointer;
        padding: 0;
        margin: 0 20px 0 0;
    }

    .sw-search--header {
        width: 300px;
        margin: 0;

        input[type="search"] {
            font-size: 14px;
            padding: 10px 40px 10px 15px;
            margin: 0;
        }

        button {
            margin: 0 15px 0 0;
        }
    }

    /* clears the 'X' from Internet Explorer */
    input[type=search]::-ms-clear {
        display: none;
        width: 0;
        height: 0;
    }

    input[type=search]::-ms-reveal {
        display: none;
        width: 0;
        height: 0;
    }

    /* clears the 'X' from Chrome */
    input[type="search"]::-webkit-search-decoration,
    input[type="search"]::-webkit-search-cancel-button,
    input[type="search"]::-webkit-search-results-button,
    input[type="search"]::-webkit-search-results-decoration {
        display: none;
    }
</style>