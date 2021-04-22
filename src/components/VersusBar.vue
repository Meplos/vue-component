<template>
  <div class="bar">
    <div class="bar__info">{{ Math.round((score / max) * 100) }}%</div>
    <div class="versusbar">
      <div class="versusbar__success" :style="getSuccessStyle"></div>
      <div class="versusbar__failure" :style="getFailureStyle"></div>
    </div>
    <div class="bar__info">{{ Math.round(100 - (score / max) * 100) }}%</div>
  </div>
</template>

<script>
export default {
  name: "VersusBar",
  props: {
    colors: {
      type: Array,
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
    getSuccessStyle: function() {
      let style = "";
      style += `background-color:  ${this.colors[0]};`;
      const percentage = (this.score / this.max) * 100;
      if (percentage >= 100) style += `border-radius: 15px;`;
      else style += `border-radius: 15px 0px 0px 15px;`;
      style += `width: ${percentage}%;`;
      return style;
    },
    getFailureStyle: function() {
      let style = "";
      style += `background-color:  ${this.colors[1]};`;
      const percentage = 100 - (this.score / this.max) * 100;
      if (percentage >= 100) style += `border-radius: 15px;`;
      else style += `border-radius: 0px 15px 15px 0px;`;
      style += `width: ${percentage}%;`;
      return style;
    },
  },
};
</script>

<style>
.bar {
  display: flex;
  flex-direction: row;
}
.bar__info {
  padding: 0px 10px 0px 10px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-size: 18px;
}
.versusbar {
  display: flex;
  flex-direction: row;
  width: 100%;
  background-color: #cecece;
  height: 20px;
  border-radius: 15px;
}

.versusbar__success {
  border-radius: 15px 0px 0px 15px;
  max-width: 100%;
}
.versusbar__failure {
  max-width: 100%;
  border-radius: 0px 15px 15px 0px;
}
</style>
