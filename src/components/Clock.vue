<template>
    <div>
        <div class="currentTime">
            <span class="time">{{ currentTime }}</span>
        </div>


        <div class="weather">
            <br>
            <div class="weather-block">
           <span v-for="weat in weather.weather " :key="weat.id"> <img :src="iconSrc" alt="" class="icon">
               : {{ weat.description }}</span>
            <br>
            <span>Temp : {{ FarenheitToCels(temp.temp) }} &#8451;</span>
            <br>
            <span>Humidity : {{ temp.humidity }} %</span>
            <br>
            <span>Wind : {{ wind_speed.speed }} </span>
        </div>
            <!-- <br>
            <span>Sunrise : {{ new Date(sunrise.sunrise) }} </span>
            <br>
            <span>Sunset : {{ new Date(sunset.sunset).getHours() }} </span> -->
        </div>


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
    z-index: 15 !important;
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
    background: rgba(87, 87, 87, 0.1);
    border-radius: 10px;
    box-shadow: 10px 15px rgb(189, 189, 189, 0,5);
    z-index: 15 !important;

}
.weather-block{
    position: relative;
    left: 60%;
    transform: translate(-60%,0);
    width: 25%;
}
.icon {
    width: 30px;
    height: 20px;
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
    async mounted() {
        this.getCurrentTime()
        setInterval(() => this.getCurrentTime(), 1000)
        this.getCurrentWeather()
        setInterval(() => this.getCurrentWeather(), 10000)
    },
    computed: {
        iconSrc(){
            let currentDateWeather = new Date()
            if(currentDateWeather.getHours() >= 22){
                this.icon_cloud = 'Night.png'
                return `/src/assets/${this.icon_cloud}`; 
            } else {
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

