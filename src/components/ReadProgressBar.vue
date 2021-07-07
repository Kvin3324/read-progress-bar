<template>
  <section class="progress-bar">
    <div class="progress-bar__background">
      <div class="progress-bar__percent" :style="styleProgress">
        <p :class="percent === 0 ? 'no-percent' : 'percent-number'"></p>
      </div>
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
  },

  computed: {
    styleProgress() {
      return {
        background: 'red',
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
    padding-top: 6px;
    padding-bottom: 15px;
    position: fixed;
    top: 0;
    width: 100%;

    &__background {
      display: flex;
      justify-content: space-between;
      background-color: white;
      box-shadow: 0px 3px 6px #00000029;
      border-radius: 30px;
      height: 20px;
      width: inherit;
    }

    &__percent {
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 30px;
      height: 20px;

      .percent-number {
        color: white;
      }

      .no-percent {
        color: black;
        padding-left: 30px;
      }
    }
  }
</style>