<template>
  <div class="progressBackground">
    <div class="progress" :style="getStyle"></div>
  </div>
</template>

<script>
export default {
  name: "Progress",
  props: {
    colors: {
      type: Array,
      required: true,
    },
    threshold: {
      type: Number,
      required: true,
    },
    score: {
      type: Number,
      required: true,
    },
    max: {
      type: Number,
      required: true,
    },
  },
  computed: {
    getStyle: function() {
      let style = "";
      style += `background-color:  ${
        this.score >= this.threshold ? this.colors[0] : this.colors[1]
      };`;
      style += `width: ${(this.score / this.max) * 100}%;`;
      return style;
    },
  },
  methods: {},
};
</script>

<style>
.progressBackground {
  background-color: #cecece;
  height: 20px;
  border-radius: 15px;
}
.progress {
  height: 20px;
  border-radius: 15px;
  max-width: 100%;
}
</style>
