<template>
  <read-progress-bar
    :percent="progressBarPercent"
  >
  </read-progress-bar>
</template>

<script>
import ReadProgressBar from './components/ReadProgressBar.vue'

export default {
  name: 'App',
  components: { ReadProgressBar },

  data() {
    return {
      percent: 0
    }
  },

  created() {
    this.handleScroll();
  },

  computed: {
    progressBarPercent() {
      const percentRes = this.percent;

      return isNaN(percentRes) ? 0 : percentRes
    }
  },

  methods: {
    handleScroll() {
      window.addEventListener('scroll', () => {
        const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
        const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
        const scrolled = (winScroll / height) * 100;

        this.percent = Math.round(scrolled);
      })
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: 200vh;
}
</style>
