<template>
  <section>
    <div v-if="!edit" class=".d-inline">
      <div :style="style">
        <v-icon class="pa-2" small>fa fa-equals</v-icon>
        <span> <slot></slot> </span>
      </div>
      <slot name="chip-actions"> </slot>
    </div>
    <div v-else></div>
  </section>
</template>

<script>
export default {
  props: {
    dark: {
      type: Boolean,
      default: false,
    },
    edit: {
      type: Boolean,
      default: false,
    },
    color: {
      type: String,
      default: "#ffffff",
    },
  },
  data() {
    return {};
  },
  computed: {
    style: function() {
      let str = `background-color:${this.color};`;
      //   str += `max-width: 300px;`;
      str += "color:";
      str += this.dark ? "#ffffff" : "#000000";

      return str;
    },
  },
};
</script>

<style lang="scss" scoped></style>
