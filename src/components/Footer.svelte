<script>

</script>

<footer class="sw-footer">
    <p>build with <a href="https://svelte.dev/" target="_blank" rel="nofollow">Svelte</a> and
        <a href="https://openweathermap.org/" target="_blank" rel="nofollow">OpenWeather API</a></p>

    <div class="sw-line"></div>
</footer>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-footer {
        position: relative;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        grid-area: footer;
        padding: 20px 0 20px 15px;
    }

    .sw-footer .sw-line {
        @include sw-size(10%, 1px);

        display: block;
        background-color: rgba($c-secondary, 0.3);
    }

    .sw-footer p,
    .sw-footer a {
        font-family: $f-basic;
        font-size: 12px;
        font-weight: 400;
        line-height: 1;
        color: rgba($c-secondary, 0.5);

        @media (min-width: $media-lg) {
            font-size: 14px;
        }
    }

    .sw-footer p {
        margin: 0 20px;
    }

    .sw-footer a {
        color: rgba($c-secondary, 0.7);
        white-space: nowrap;
        transition: color 0.3s ease-in-out;

        &:hover {
            color: $c-secondary;
        }
    }
</style>