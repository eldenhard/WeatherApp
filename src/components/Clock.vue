<template>
    <div>
        <div class="currentTime">
            <span class="time">{{ currentTime }}</span>
        </div>


        <div class="weather" style=" z-index: 150 !important;">
            <div class="weather-block" style=" z-index: 150 !important;">
                <span class="weather-block__content" v-for="weat in weather.weather " :key="weat.id">
                    <img :src="iconCloud" alt="" class="icon">
                    : <span class="weather-block__data" style="margin-bottom: 25px !important; padding-bottom: 25px !important">{{ weat.description }}</span></span>
                <br>
                <span class="weather-block__content">
                    <img :src="iconSrcTerm" alt="" class="icon"> :
                    <span class="weather-block__data">{{ FarenheitToCels(temp.temp) }}</span>
                    <span class="weather-block__icon">&#8451;</span></span>
                <br>
                <span class="weather-block__content"><img src="../assets/Humidity.png" alt="" class="icon"> :
                    <span class="weather-block__data">{{ temp.humidity }}</span> <span
                        class="weather-block__icon">%</span></span>
                <br>
                <span class="weather-block__content"><img src="../assets/Wind.png" alt="" class="icon">:
                    <span class="weather-block__data">{{ wind_speed.speed }} </span><span
                        class="weather-block__icon">m/sec</span></span>
            </div>
        </div>






    </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Saira:wght@100&display=swap');

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

:root {
    --index: calc(1vw + 1vh);
    --text: #e7e7e0;
}

.currentTime {
    position: absolute;
    padding-top: calc(var(--index) * 20);
    left: 50%;
    transform: translate(-50%, -50%);
    color: var(--text);
    font-family: 'Saira', sans-serif;
    z-index: 15 !important;
}

.time {
    font-size: calc(var(--index) * 6);
}

.weather {
    height: 100vh;
    align-items: center;
    justify-content: center;
    text-align: center;
    overflow: hidden;
    z-index: 15 !important;
}

.weather-block {
    position: relative;
    left: 50%;
    transform: translate(-50%, 0);
    width: 25%;
    padding-top: calc(var(--index) * 15);
    font-family: 'Saira', sans-serif;
    z-index: 15 !important;
}

.weather-block__content {
    color: var(--text);
    font-size: calc(var(--index) * .8);
    letter-spacing: calc(var(--index) / 10);
}

.weather-block__icon {
    font-size: calc(var(--index) * 0.65);
    padding-top: calc(var(--index) * 15);
    color: #ccccc6;

}

.icon {
    width: calc(var(--index) * 2);
    height: calc(var(--index) * 2);
}

@media screen and (max-width: 600px) {
    .currentTime {
        padding-top: calc(var(--index) * 50);
    }

    .weather-block {
        padding-top: calc(var(--index) * 30);
    }

}
</style>

<script>
import axios from 'axios'
export default {
    name: 'Clock',
    data() {
        return {
            currentTime: '',
            seconds: '',
            weather: '',
            clouds: '',
            temp: '',
            wind_speed: '',
            sunrise: '',
            sunset: '',
            alignments: [
                'center',
            ],
            icon_cloud: '',
        }
    },
    mounted() {
        this.getCurrentTime()
        setInterval(() => this.getCurrentTime(), 1000)
        this.getCurrentWeather()
        setInterval(() => this.getCurrentWeather(), 10000)
    },
    computed: {
        iconCloud() {
            let currentDateWeather = new Date()
            if (currentDateWeather.getHours() <= 20) {
                this.icon_cloud = 'Cloud.png'
                return `/src/assets/${this.icon_cloud}`;
            } else {
                this.icon_cloud = 'Night.png'
                return `/src/assets/${this.icon_cloud}`;

            }
        },
        iconSrcTerm() {
            if (this.temp.temp >= 0) {
                this.icon_cloud = 'TempPlus.png'
                return `/src/assets/${this.icon_cloud}`;
            } else {
                this.icon_cloud = 'TempMin.png'
                return `/src/assets/${this.icon_cloud}`;
            }
        }
    },
    methods: {
        getCurrentTime() {
            let currentDate = new Date()
            this.currentTime = [currentDate.getHours(), currentDate.getMinutes()].map(function (time) {
                return time < 10 ? '0' + time : time
            }).join(":")
        },
        getCurrentWeather() {
            let ApiKey = 'd251f5d1371952ee5d01f6805fac142f'
            axios.get('https://api.openweathermap.org/data/2.5/weather?lat=55.85832197778835&lon=37.58639574050904&APPID=' + `${ApiKey}`)
                .then(response => {

                    this.weather = response.data;
                    this.temp = response.data.main;
                    this.wind_speed = response.data.wind
                    this.sunrise = response.data.sys
                    this.sunset = response.data.sys
                })
        },
        FarenheitToCels(str) {
            return Math.floor(Number(str - 273, 15))
        }
    }

}


</script>

