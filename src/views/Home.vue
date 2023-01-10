<template>
  <div>
    <div class="mainPic">
      <img src="@/assets/Mountain.jpg" alt="">
      <Clock />
    </div>
    <AboutTech />

  </div>
</template>

<script>

import Clock from '@/components/Clock.vue'
import AboutTech from '@/components/AboutTech.vue'
export default {
  components: { Clock, AboutTech },
  name: 'Home',
  data() {
    return {

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