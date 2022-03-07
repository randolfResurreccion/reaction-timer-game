<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">Rank: {{ rank }}</p>
</template>

<script>
export default {
  name: 'Results',
  props: ['score'],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Rapid Finger'
    } else if (this.score < 400) {
      this.rank = 'Trigger Finger'
    } else {
      this.rank = 'Snail pace..'
    }
  },
}
</script>

<style scoped>
.rank {
    font-size: 1.4em;
    color: #38d9a9;
    font-weight: bold;
}
</style>
