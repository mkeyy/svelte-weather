<script>
    import {data} from '../../stores';

    let deg, compassSector, windDirection;

    data.subscribe(() => {
        if($data.wind) {
            deg = $data.wind.deg ? $data.wind.deg : 0;
            compassSector = ["N", "NNE", "NE", "ENE", "E", "ESE", "SE", "SSE", "S", "SSW", "SW", "WSW", "W", "WNW", "NW", "NNW", "N"];
            windDirection = compassSector[Math.floor(deg / 22.5)];
        }
    });

</script>

<div class="sw-wind">
    <div class="sw-compass">
        <span>N</span>
        <div class="sw-compass__inner">
            <span>W</span>
            <span class="sw-circle" style={`transform: rotate(${$data.wind.deg}deg)`}></span>
            <span>E</span>
        </div>
        <span>S</span>
    </div>
    <div class="sw-details">
        <span>Wind Direction: <strong>{windDirection}</strong></span>
        <span>Wind Speed: <strong>{$data.wind.speed} m/s</strong></span>
    </div>
</div>

<style lang="scss">
    @import "../../assets/styles/settings.scss";

    .sw-wind {
        display: flex;
        grid-area: wind;
    }

    .sw-compass {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .sw-compass .sw-compass__inner {
        display: flex;
        align-items: center;
    }

    .sw-compass .sw-circle {
        @include sw-size(125px);

        position: relative;
        display: block;
        border-radius: 50%;
        border: 3px solid rgba($c-secondary, 0.5);
        margin: 10px 15px;
        transition: transform 0.3s ease-in-out;

        &::before {
            @include sw-pseudo();
            @include sw-size(0);

            top: -13px;
            left: calc(50% - 10px);
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            border-bottom: 8px solid $c-secondary;
            transform-origin: 0;
        }
    }

    .sw-details {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin: 0 45px;

        span {
            display: block;
            font-size: 16px;
            font-weight: 300;
            line-height: 1;
        }

        span + span {
            margin-top: 10px;
        }

        strong {
            font-weight: 900;
        }
    }
</style>