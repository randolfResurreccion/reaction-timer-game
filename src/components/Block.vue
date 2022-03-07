<template>
  <div
    class="block"
    :style="{ backgroundColor: randomColor() }"
    v-if="showBlock"
    @click="stopTimer"
  >
    click me
  </div>
</template>

<script>
export default {
  name: 'Block',
  props: ['delay', 'isPlaying'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      colors: ['#f783ac', '#da77f2', '#748ffc', '#ffa94d'],
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('endtimer', this.reactionTime)
    },
    randomColor() {
      const random = Math.floor(Math.random() * this.colors.length)
      return this.colors[random]
    },
  },
}
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  color: #fefefe;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
