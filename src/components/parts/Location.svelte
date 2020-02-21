<script>
    import {data} from '../../stores';
</script>

<div class="sw-location">
    <h1>{$data.name}<span>{$data.sys.country}</span></h1>
    <div class="sw-coordinates">
        <span>longitude: {$data.coord.lon}&#176;</span>
        <span>latitude: {$data.coord.lat}&#176;</span>
    </div>

    <div class="sw-stats">
        <span>Temp min: <strong>{Math.round($data.main.temp_min)}&#8451;</strong></span>
        <span>Temp max: <strong>{Math.round($data.main.temp_max)}&#8451;</strong></span>
        <span>Pressure: <strong>{$data.main.pressure} hPa</strong></span>
        <span>Humidity: <strong>{$data.main.humidity}%</strong></span>
    </div>
</div>

<style lang="scss">
    @import "../../assets/styles/settings.scss";

    .sw-location {
        grid-area: location;
    }

    h1 {
        text-align: center;

        @media (min-width: $media-sm) {
            text-align: left;
        }
    }

    h1 > span {
        font-size: 15px;

        @media (min-width: $media-sm) {
            font-size: 25px;
        }

        @media (min-width: $media-lg) {
            font-size: 40px;
        }
    }

    .sw-coordinates {
        display: flex;
        justify-content: center;
        margin: 10px 0 0;

        @media (min-width: $media-sm) {
            justify-content: flex-start;
        }
    }

    .sw-coordinates span {
        font-size: 14px;
        line-height: 1;

        @media (min-width: $media-sm) {
            font-size: 16px;
        }

        @media (min-width: $media-lg) {
            font-size: 20px;
        }
    }

    .sw-coordinates span + span {
        margin-left: 10px;
    }

    .sw-stats {
        display: flex;
        flex-direction: column;
        align-items: center;
        border-top: 1px solid rgba($c-secondary, 0.5);
        padding: 20px 0 0;
        margin: 20px 0 0;

        span {
            display: block;
            font-size: 15px;
            font-weight: 300;
            line-height: 1;
            letter-spacing: 1px;
            margin: 0 0 15px;
        }

        @media (min-width: $media-sm) {
            align-items: flex-start;
            padding: 40px 0 0;
            margin: 40px 0;

            span {
                font-size: 20px;
            }
        }
    }
</style>