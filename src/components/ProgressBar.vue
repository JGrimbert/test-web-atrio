<template>
  <p>{{ input.label }}</p>
  <div class="wrapper">
    <div class="percentage">{{ percent }}%</div>
    <div class="progressBar">
      <div
        class="progress"
        :style="style"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "ProgressBar",
  props: {
    input: { type: Object },
  },
  computed: {
    percent () {
      return Math.trunc((this.input.value / this.input.max) * 100)
    },
    style () {
      return {
        width: this.percent + "%",
        'background-color': this.backgroundColor
      }
    },
    backgroundColor () {
      switch (true) {
        case (this.percent <= 25):
          return '#7160E8'
        case (this.percent <= 50):
          return '#60ADE8'
        case (this.percent <= 75):
          return '#60E8B6'
        default:
          return '#30DB63'
      }
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  place-items: center;
  margin:0 0 1em;
}
.progressBar {
  width:100%;
  height: 16px;
  margin:0 1em;
}
.progress {
  height:100%;
}
.percentage {
  font-size: 1.222em;
}
p {
  margin: 0;
}
</style>