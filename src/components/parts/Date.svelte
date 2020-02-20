<script>
    import {onMount} from 'svelte';

    let displayDate = null;
    let monthShort = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

    onMount(() => {
        handleDate();
    });

    function handleDate() {
        let date = new Date();
        let d = date.getUTCDay(), M = monthShort[date.getUTCMonth()], Y = date.getUTCFullYear();
        let h = date.getUTCHours(), m = date.getUTCMinutes();
        displayDate = d + ' ' + M + ' ' + Y + ' ' + h + ':' + (m < 10 ? '0' : '') + m;

        setTimeout(handleDate, 1000);
    }
</script>

{#if displayDate}
    <div class="sw-date">{displayDate} UTC</div>
{/if}

<style lang="scss">
    @import "../../assets/styles/settings.scss";

    .sw-date {
        font-family: $f-fancy;
        font-size: 15px;
        line-height: 1;
        color: $c-secondary;
    }
</style>