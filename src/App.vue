<template>
  <div id="app">
    <div ref="vantaRef" style="height: 100%;"></div>
    <router-view class="my_title"/>
  </div>
</template>

<script>
import * as THREE from 'three'
import GLOBE from 'vanta/src/vanta.globe'

export default {
  name: 'App',
  mounted () {
    this.vantaEffect = GLOBE({
      el: this.$refs.vantaRef,
      THREE: THREE
    })
    // eslint-disable-next-line no-undef
    this.vantaEffect.setOptions({
      el: this.$refs.vantaRef,
      mouseControls: true,
      touchControls: true,
      gyroControls: false,
      minHeight: 200.00,
      minWidth: 200.00,
      scale: 1.00,
      scaleMobile: 1.00,
      color: 0x2299ee,
      color2: 0x909399,
      backgroundColor: 0x1c1720,
      size: 2.00
    })
  },
  beforeDestroy () {
    if (this.vantaEffect) {
      this.vantaEffect.destroy()
    }
  }
}
</script>

<style>
#app {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  color: white;
}

html::-webkit-scrollbar {
  display: none;
}

.my_title {
  position: absolute;
  top: 0;
  left: 0;
  margin: 0;
  height: 100%;
}
</style>
