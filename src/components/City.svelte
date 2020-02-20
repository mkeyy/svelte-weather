<script>
    import Search from './Search.svelte';

    export let city = null;

    let date = new Date();
    let monthShort = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
</script>

<div class="sw-app sw-app--city">
    <div class="sw-container">
        <div class="sw-city">
            <header class="sw-header">
                <Search header="true"/>
                <div class="sw-date">{ date.getDate() + ' ' + monthShort[date.getMonth()] + ' ' + date.getFullYear() + ' ' + date.getHours() + ":" + (date.getMinutes()<10?'0':'') + date.getMinutes()}</div>
            </header>

            {#if city}
                <main class="sw-main">
                    <div class="sw-location">
                        <h1>{city.name}</h1>
                        <div class="sw-coordinates">
                            <span>longitude: {city.coord.lon}&#176;</span>
                            <span>latitude: {city.coord.lat}&#176;</span>
                        </div>

                        <div class="sw-stats">
                            <span>Temp min: <strong>{city.main.temp_min}&#8451;</strong></span>
                            <span>Temp max: <strong>{city.main.temp_max}&#8451;</strong></span>
                            <span>Pressure: <strong>{city.main.pressure} hPa</strong></span>
                            <span>Humidity: <strong>{city.main.humidity}%</strong></span>
                        </div>
                    </div>
                    <div class="sw-weather">
                        <div class="sw-weather__condition">
                            <img src={`http://openweathermap.org/img/wn/${city.weather[0].icon}@2x.png`}
                                 alt={city.weather[0].description}>
                            <span>{city.weather[0].main}</span>
                        </div>

                        <span class="sw-weather__temp">{city.main.temp}&#8451;</span>
                        <span class="sw-weather__temp-feels">Feels like <strong>{city.main.feels_like}
                            &#8451;</strong></span>
                    </div>
                    <div class="sw-wind">
                        <div class="sw-compass">
                            <span>N</span>
                            <div class="sw-wrapper">
                                <span>W</span>
                                <span class="sw-circle" style={`transform: rotate(${city.wind.deg - 90}deg)`}></span>
                                <span>E</span>
                            </div>
                            <span>S</span>
                        </div>
                    </div>
                </main>
            {/if}
        </div>
    </div>
</div>

<style lang="scss">
    @import "../assets/styles/settings.scss";

    .sw-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px 0;

        .sw-date {
            font-family: $f-fancy;
            font-size: 15px;
            line-height: 1;
            color: $c-secondary;
        }
    }

    .sw-main {
        display: grid;
        grid-template-areas: "location weather" "wind wind";
        grid-template-columns: 1fr 1fr;
        padding: 50px 0;
    }

    .sw-location {
        grid-area: location;

        h1 {
            font-size: 80px;
            line-height: 1;
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
    }

    .sw-weather {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        grid-area: weather;

        .sw-weather__condition {
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

        .sw-weather__temp {
            font-size: 100px;
            line-height: 1.1;
        }

        .sw-weather__temp-feels {
            font-size: 20px;
            line-height: 1.1;

            strong {
                font-weight: 900;
            }
        }
    }

    .sw-wind {
        display: flex;
        grid-area: wind;

        .sw-compass {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 50px 0 0;

            .sw-wrapper {
                display: flex;
                align-items: center;
            }

            .sw-circle {
                @include sw-size(150px);

                position: relative;
                display: block;
                border-radius: 50%;
                border: 3px solid $c-secondary;
                margin: 0 5px;

                &::before {
                    @include sw-pseudo();
                    @include sw-size(50%, 1px);

                    top: 50%;
                    left: 50%;
                    background-color: $c-secondary;
                    transform-origin: 0;
                }
            }
        }
    }
</style>