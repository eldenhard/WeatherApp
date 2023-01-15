<template>
    <div>
        <div class="currentTime">
            {{ weather }}
            <span class="time">{{ currentTime }}</span>
        </div>
  

        <div class="weather">
            <br>
            <span v-for="weat in weather.weather " :key="weat.id"> <img :src="iconSrc" alt="" class="icon">
                : {{ weat.description }}</span>
            <br>
            <span>Temp : {{ FarenheitToCels(temp.temp) }} &#8451;</span>
            <br>
            <span>Humidity : {{ temp.humidity }} %</span>
            <br>
            <span>Wind : {{ wind_speed.speed }} </span>
            <!-- <br>
            <span>Sunrise : {{ new Date(sunrise.sunrise) }} </span>
            <br>
            <span>Sunset : {{ new Date(sunset.sunset).getHours() }} </span> -->
        </div>



        <div class="weateeher">
            <v-container v-for="align in alignments" :key="align" class="grey lighten-5 mb-6">
                <v-row :align="align" no-gutters style="height: 150px;">
                    <v-col>
                        <v-card class="pa-2" justify="3">
                            {{ this.clouds }}
                        </v-card>
                    </v-col>
                    <v-col>
                        <v-card class="pa-2" justify="3">
                            One of three columns
                        </v-card>
                    </v-col>
                    <v-col>
                        <v-card class="pa-2" justify="3">
                            One of three columns
                        </v-card>
                    </v-col>
                </v-row>
            </v-container>
        </div>
        <!-- {{ weather }} -->
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Saira:wght@100&display=swap');

.currentTime {
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: rgb(233, 233, 233);
    font-family: 'Saira', sans-serif;
}

.time {
    font-size: 160px;
}

.weather {
    position: absolute;
    width: 50%;
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: rgb(233, 233, 233);
    font-family: 'Saira', sans-serif;
    background: rgba(0, 0, 0, 0.1);
}

.icon {
    width: 20px;
    height: 15px;
}
</style>

<script>
import axios from 'axios'
export default {
    name: 'Clock',
    data() {
        return {
            currentTime: '',
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
        iconSrc() {
            if (new Date().getHours() > 22) {
                this.icon_cloud = 'Nigth.png'
                return `/src/assets/${this.icon_cloud}`;
            } else if (this.weather.main == 'Clouds') {
                this.icon_cloud = 'Cloudly.png'
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

