<script>

</script>

<footer class="sw-footer sw-container">
    <p>
        build with <a href="https://svelte.dev/" target="_blank" rel="nofollow">Svelte</a> and
        <a href="https://openweathermap.org/" target="_blank" rel="nofollow">OpenWeather API</a>
    </p>
</footer>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-footer {
        display: flex;
        justify-content: flex-end;
        grid-area: footer;
        padding: 20px 15px;
    }

    p, a {
        font-size: 14px;
        font-weight: 400;
        line-height: 1;
        color: rgba($c-primary, 0.5);
    }

    a {
        color: rgba($c-primary, 0.8);
        transition: color 0.3s ease-in-out;

        &:hover {
            color: $c-primary;
        }
    }
</style>