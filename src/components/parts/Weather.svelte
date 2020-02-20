<script>
    import {data} from '../../stores';
</script>

<div class="sw-weather">
    <div class="sw-condition">
        <img src={`http://openweathermap.org/img/wn/${$data.weather[0].icon}@2x.png`}
             alt={$data.weather[0].description}>
        <span>{$data.weather[0].main}</span>
    </div>

    <span class="sw-temp">{$data.main.temp}&#8451;</span>
    <span class="sw-temp-feels">Feels like <strong>{$data.main.feels_like}
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
    }

    .sw-condition {
        display: flex;
        align-items: center;

        img {
            max-width: 100px;
            object-fit: contain;
        }

        span {
            font-size: 25px;
            line-height: 1;
        }
    }

    .sw-temp {
        font-size: 100px;
        line-height: 1.1;
    }

    .sw-temp-feels {
        font-size: 20px;
        line-height: 1.1;

        strong {
            font-weight: 900;
        }
    }
</style>