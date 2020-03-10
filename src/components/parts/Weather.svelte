<script>
    import {data} from '../../stores';
</script>

<div class="sw-weather">
    <div class="sw-condition">
        <img src={`http://openweathermap.org/img/wn/${$data.weather[0].icon}@2x.png`}
             alt={$data.weather[0].description}>
        <span>{$data.weather[0].main}</span>
    </div>

    <span class="sw-temp">{Math.round($data.main.temp)}&#8451;</span>
    <span class="sw-temp-feels">Feels like <strong>{Math.round($data.main.feels_like)}
        &#8451;</strong></span>
</div>

<style lang="scss">
    @import "../../assets/styles/settings.scss";

    .sw-weather {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        grid-area: weather;
        margin: -20px 0 0;
    }

    .sw-condition {
        display: flex;
        align-items: center;

        img {
            max-width: 80px;
            object-fit: contain;

            @media (min-width: $media-md) {
                max-width: 100px;
            }
        }

        span {
            font-size: 16px;
            line-height: 1;

            @media (min-width: $media-sm) {
                font-size: 20px;
            }

            @media (min-width: $media-md) {
                font-size: 25px;
            }
        }
    }

    .sw-temp {
        font-size: 50px;
        font-weight: 700;
        line-height: 1.1;

        @media (min-width: $media-md) {
            font-size: 100px;
        }

        @media (min-width: $media-lg) {
            font-size: 150px;
        }
    }

    .sw-temp-feels {
        font-size: 16px;
        line-height: 1.1;

        strong {
            font-weight: 900;
        }

        @media (min-width: $media-lg) {
            font-size: 20px;
        }
    }
</style>