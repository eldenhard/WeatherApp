<template>
  <div>
    <div class="mainPic" v-if="this.day">
      <img src="@/assets/Mountain.jpg" alt="">
      <Clock />
    </div>
    <!-- <AboutTech /> -->
    <div>
      <NightBlock v-if="this.night"/>
    </div>

  </div>
</template>

<script>
import NightBlock from '@/components/NightBlock.vue'
import Clock from '@/components/Clock.vue'
import AboutTech from '@/components/AboutTech.vue'
export default {
  components: { Clock, AboutTech, NightBlock },
  name: 'Home',
  data() {
    return {
      day: Boolean,
      night: Boolean
    }
  },
  mounted(){
    this.currentBackground()
  },
  methods: {
    currentBackground(){
      if(new Date().getHours() > 22){
        this.day = false 
        this.night = true
        console.log('Сейчас ночь')
      } else{
        this.day = true 
        this.night = false
        console.log('Сейчас день')

      }
    }
  }
}
</script>


<style scoped>
.mainPic {
  overflow: hidden;
  width: 100%;
  height: 100vh;
  position: relative;
}

.mainPic img {
  width: 100% !important;
  height: 100% !important;
  object-fit: cover;
}
</style>