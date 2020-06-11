<template>
  <section class="press-move">
    <div
      class="demo"
      v-gesture:pressMove="pressMove"
      v-gesture:touchEnd="touchOrMouse"
      v-gesture:mouseUp="touchOrMouse"
      :style="{transform:`translate3d(${distanceX}px,${distanceY}px,0)`}"
    ></div>
  </section>
</template>

<script>
export default {
  name: 'pressMove',
  data() {
    return {
      lastSpeed: 0,
      moveTime: 0,
      distanceX: 0,
      distanceY: 0
    }
  },
  methods: {
    pressMove(evt) {
      // 最后一次的速度
      this.moveX = evt.deltaX
        console.log('--')
      this.moveTime = evt.moveTime
        // console.log(evt.moveTime)
    },
    touchOrMouse() {
      let speed = this.moveX / this.moveTime
      this.distanceX += Math.round(speed * 175)
      console.log(this.distanceX)
    }
  }
}
</script>

<style scoped >
.demo {
  transition: transform linear 500ms;
  width: 100px;
  height: 100px;
  background: skyblue;
  cursor: pointer;
}
</style>
