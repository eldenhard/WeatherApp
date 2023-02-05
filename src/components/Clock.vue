<template>
    <div>
        <div class="text-center ma-2">
            <v-snackbar v-model="snackbar">
                <p>Здравствуйте, {{ mainText }}</p>
                <template v-slot:action="{ attrs }" style="z-index: 2000 !important">
                    <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
                        Close
                    </v-btn>
                </template>
            </v-snackbar>
        </div>
        <Loader :loader="loader" />
        <!-- <Notifications :snackbar="snackbar" :text="text" :timeout="timeout"/> -->
        <div class="currentTime">
            <span class="time">{{ currentTime }}</span>
        </div>

        <div class="weather">
            <div class="weather-block">
                <span class="weather-block__content" v-for="weat in weather.weather " :key="weat.id">
                    <img :src="iconCloud" alt="" class="icon">
                    <span class="weather-block__data"
                        style="margin-bottom: 25px !important; padding-bottom: 25px !important">
                        : {{ weat.description }}
                    </span></span>
                <br>
                <span class="weather-block__content">
                    <img :src="iconSrcTerm" alt="" class="icon">
                    <span class="weather-block__data"> :{{ KelvinToCels(temp.temp) }}
                        <span class="weather-block__icon">&#8451;</span></span></span>
                <br>
                <span class="weather-block__content"><img src="../assets/Humidity.png" alt="" class="icon">
                    <span class="weather-block__data"> :{{ temp.humidity }} <span
                            class="weather-block__icon">%</span></span></span>
                <br>
                <span class="weather-block__content"><img src="../assets/Wind.png" alt="" class="icon">
                    <span class="weather-block__data"> :{{ wind_speed.speed }} <span
                            class="weather-block__icon">m/sec</span></span></span>
            </div>
            <div class="geodata">
                <span>Ваши геоданные: <span>
                        Lat: {{ this.lat }}
                        Long: {{ this.long }}
                    </span>
                </span>
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

.text-center {
    position: fixed;
    top: 0;
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
    z-index: 150 !important;
}

.weather-block {
    position: relative;
    left: 50%;
    transform: translate(-50%, 0);
    width: 25%;
    padding-top: calc(var(--index) * 15);
    font-family: 'Saira', sans-serif;
    z-index: 150 !important;
}

.weather-block__content {
    color: var(--text);
    font-size: calc(var(--index) * .8);
    letter-spacing: calc(var(--index) / 10);
}

.weather-block__data {
    position: relative;
    bottom: 13px;
}

.weather-block__icon {
    font-size: calc(var(--index) * 0.65);
    padding-top: calc(var(--index) * 15);
    color: #ccccc6;

}

.geodata {
    color: #ccccc6;
    position: absolute;
    right: calc(var(--index) * 1);
    bottom: 10px;
    font-size: calc(var(--index)* 0.4);
    z-index: 150;
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

    .geodata {
        font-size: calc(var(--index)* 0.8);
    }

}
</style>

<script>
import axios from 'axios'
import Loader from './Loader.vue'
export default {
    name: 'Clock',
    components: { Loader},
    data() {
        return {
            currentTime: '',
            weather: '',
            temp: '',
            wind_speed: '',
            lat: '',
            long: '',
            icon_cloud: '',
            icon_term: '',
            loader: false,
            mainText: '',
            timeout: 2000,
        }
    },
    mounted() {
        this.loader = true
        setTimeout(() => this.loader = false, 2100)

        this.getCurrentTime()
        
       this.getCurrentPosition()
        this.getCurrentPosition()
        this.getCurrentWeather()
        setInterval(() => this.getCurrentWeather(), 2500)

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
            if (this.temp.temp >= 273.15) {
                this.icon_term = 'TempPlus.png'
                return `/src/assets/${this.icon_term}`;
            } else {
                this.icon_term = 'TempMin.png'
                return `/src/assets/${this.icon_term}`;
            }
        },
        partOfDay() {
            return new Promise((resolve, reject) => {
                let currentTime = new Date().getHours()
                if (currentTime > 6 && currentTime < 12) return this.mainText = 'Доброе утро';
                if (currentTime > 12 && currentTime < 18) return this.mainText = 'Добрый день';
                if (currentTime > 18 && currentTime < 0) return this.mainText = 'Добрый вечер';
                if (currentTime > 0 && currentTime < 6) return this.mainText = 'Доброй ночи';
                if (this.mainText) {
                    return resolve(this.mainText)
                } else {
                    reject(new Error('Ошибка. данных нет'))
                }
            })


        }

    },
    methods: {
        getCurrentTime() {
            setInterval(() => {
                let currentDate = new Date()
                this.currentTime = [currentDate.getHours(), currentDate.getMinutes()].map(function (time) {
                    return time < 10 ? '0' + time : time
                }).join(":")
            }, 1000)

        },
        getCurrentWeather() {
                let ApiKey = 'ea9eb2154a207351366a2b982d9de1c2'
                axios.get(`https://api.openweathermap.org/data/2.5/weather?lat=${this.lat}&lon=${this.long}&APPID=` + `${ApiKey}`)
                    .then(response => {
                        this.weather = response.data;
                        this.temp = response.data.main;
                        this.wind_speed = response.data.wind
                    }).catch(error => {
                        console.log(new Error('Данные не получены, перезагрузите браузер'))
                    })
        },
        getCurrentPosition() {
            navigator.geolocation.getCurrentPosition(position => {
                this.lat = position.coords.latitude
                this.long = position.coords.longitude
            })
        },
        KelvinToCels(str) {
            return Math.floor(Number(str - 273, 15))
        },

    }

}


</script>

