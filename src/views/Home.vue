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
      day: false,
      night: true
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