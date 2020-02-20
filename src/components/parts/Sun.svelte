<script>
    import AssetSVG from '../AssetSVG.svelte';
    import icSunrise from '../../assets/img/ic-sunrise.svg';
    import icSunset from '../../assets/img/ic-sunset.svg';

    import {data} from '../../stores';

    let sunriseTime, sunsetTime;

    data.subscribe(() => {
        if($data.cod === 200) {
            let sunriseDate = new Date($data.sys.sunrise * 1000 + ($data.timezone * 1000));
            let sunsetDate = new Date($data.sys.sunset * 1000 + ($data.timezone * 1000));
            sunriseTime = sunriseDate.getUTCHours() + ':' + (sunriseDate.getUTCMinutes() < 10 ? '0' : '') + sunriseDate.getUTCMinutes();
            sunsetTime = sunsetDate.getUTCHours() + ':' + (sunsetDate.getUTCMinutes() < 10 ? '0' : '') + sunsetDate.getUTCMinutes();
        }
    })
</script>

<div class="sw-sun">
    <div class="sw-sunrise">
        <AssetSVG svgSRC={icSunrise} classes="sw-svg--sunrise"/>
        <span class="sw-title">Sunrise</span>
        <span>{sunriseTime} (UTC {($data.timezone/3600 >= 0 ? '+ ' : '- ') +  Math.abs($data.timezone/3600)})</span>
    </div>

    <span class="sw-line"></span>

    <div class="sw-sunset">
        <AssetSVG svgSRC={icSunset} classes="sw-svg--sunset"/>
        <span class="sw-title">Sunset</span>
        <span>{sunsetTime} (UTC {($data.timezone/3600 >= 0 ? '+ ' : '- ') +  Math.abs($data.timezone/3600)})</span>
    </div>
</div>

<style lang="scss">
    @import "../../assets/styles/settings.scss";

    .sw-sun {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 40px 0 0;
    }

    .sw-sunrise,
    .sw-sunset {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 0 20px;
    }

    .sw-title {
        font-family: $f-fancy;
        font-size: 18px;
        font-weight: 900;
        letter-spacing: 1px;
        text-transform: uppercase;
    }

    .sw-line {
        @include sw-size(200px, 3px);

        display: block;
        border-radius: 5px;
        background-color: rgba($c-secondary, 0.5);
    }
</style>