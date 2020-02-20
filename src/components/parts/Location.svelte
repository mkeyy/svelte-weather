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
        <span>Temp min: <strong>{$data.main.temp_min}&#8451;</strong></span>
        <span>Temp max: <strong>{$data.main.temp_max}&#8451;</strong></span>
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
        font-size: 80px;
        line-height: 1;

        > span {
            font-size: 40px;
        }
    }

    .sw-coordinates span {
        font-size: 20px;
        line-height: 1;
    }

    .sw-coordinates span + span {
        margin-left: 10px;
    }

    .sw-stats {
        display: flex;
        flex-direction: column;
        border-top: 1px solid rgba($c-secondary, 0.5);
        padding: 40px 0 0;
        margin: 40px 0;

        span {
            display: block;
            font-size: 20px;
            font-weight: 300;
            line-height: 1;
            letter-spacing: 1px;
            margin: 0 0 15px;
        }
    }
</style>