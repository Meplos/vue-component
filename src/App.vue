<template>
  <v-app>
    <draggable-chip class="mt-11" :color="chipColor">
      Hello world
      <template v-slot:chip-actions>
        <div>
          <v-btn> <v-icon small>fas fa-save</v-icon> </v-btn>
          <v-btn> <v-icon small>fas fa-trash</v-icon> </v-btn>
        </div>
      </template>
    </draggable-chip>
  </v-app>
</template>

<script>
import DraggableChip from "./components/DraggableChip.vue";
export default {
  name: "App",

  components: { DraggableChip },

  data: () => ({
    chipColor: "#faee45",
    //
  }),
};
</script>
