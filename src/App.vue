<template>
  <div id="app">
    <SizeSelector v-on:set-size="setSize" />
    <Dungeon :rows="rows" :cols="cols" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Dungeon from "./components/Dungeon.vue";
import SizeSelector from "./components/SizeSelector.vue";

@Component({
  components: {
    Dungeon,
    SizeSelector
  }
})
export default class App extends Vue {
  rows: number = 3;
  cols: number = 4;

  setSize(rows: number, cols: number) {
    this.rows = rows;
    this.cols = cols;
  }
}
</script>

<style scoped></style>
