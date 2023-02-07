<template>
  <div>
    <Loader :loader="loader" />
    <div class="mainPic" v-if="this.day">
      <Clock />
    </div>
    <div>
      <NightBlock v-if="this.night" />
    </div>

  </div>
</template>

<script>
import NightBlock from '@/components/NightBlock.vue'
import Clock from '@/components/Clock.vue'
import AboutTech from '@/components/AboutTech.vue'
import Loader from '@/components/Loader.vue'
export default {
  components: { Clock, AboutTech, NightBlock, Loader },
  name: 'Home',
  data() {
    return {
      day: Boolean,
      night: Boolean,
      loader: false
    }
  },
  mounted() {
    this.loader = true
    this.currentBackground()
    this.loader = false
  },
  methods: {
    currentBackground() {
      if (new Date().getHours() >= 20) {
        this.day = false
        this.night = true
      } else {
        this.day = true
        this.night = false

      }
    }
  }
}
</script>


<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

:root {
  --index: calc(1vw + 1vh);
  --text: #e7e7e0;
}

.mainPic {

  background-image: url(@/assets/Mountain.jpg);
  /* background-image: url(@/assets/stars.jpg); */
  height: 100% !important;
  width: 100% !important;
  position: absolute !important;
  background-size: cover !important;
  background-position: center !important;
}
</style>