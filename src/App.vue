<template>
  <div id="app">
    <Progress
      :colors="colors"
      :max="max"
      :score="score"
      :threshold="threshold"
    />
    <br />
    <VersusBar :colors="colors" :max="max" :score="score" />
  </div>
</template>

<script>
import Progress from "./components/Progress.vue";
import VersusBar from "./components/VersusBar.vue";
export default {
  name: "App",
  components: {
    Progress,
    VersusBar,
  },
  data: () => ({
    colors: ["#5fa85f", "#cc3732"],
    score: 0,
    threshold: 50,
    max: 100,
    timer: null,
  }),
  methods: {
    progress: function() {
      this.timer = setInterval(() => {
        this.score++;
      }, 50);
    },
  },
  created: function() {
    this.progress();
  },
  watch: {
    score: function(val) {
      if (val >= this.max) {
        clearInterval(this.timer);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
