<template>
  <section class="progress-bar">
    <div class="progress-bar__background" :style="styleProgress">
    </div>
  </section>
</template>

<script>
export default {
  name: 'read-progress-bar',

  props: {
    percent: {
      type: Number,
      default: 0
    },
    color: {
      type: String,
      default: ''
    }
  },

  computed: {
    styleProgress() {
      return {
        background: `${this.color}`,
        width: `${this.percent}%`
      }
    }
  },
}
</script>

<style lang="scss" scoped>
  .progress-bar {
    display: flex;
    flex-direction: row;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;

    &__background {
      display: flex;
      justify-content: space-between;
      background-color: white;
      height: 4px;
      width: inherit;
    }
  }
</style>