<template>
  <div>
    <b-button variant="outline-primary" v-on:click="onClick(3, 4)"
      >3x4</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(3, 5)"
      >3x5</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(3, 6)"
      >3x6</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(4, 4)"
      >4x4</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(4, 5)"
      >4x5</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(4, 6)"
      >4x6</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(5, 4)"
      >5x4</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(5, 5)"
      >5x5</b-button
    >
    <b-button variant="outline-primary" v-on:click="onClick(5, 6)"
      >5x6</b-button
    >
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from "vue-property-decorator";

@Component
export default class SizeSelector extends Vue {
  @Emit("set-size")
  setSize(rows: number, cols: number) {}

  onClick(rows: number, cols: number) {
    this.setSize(rows, cols);
  }
}
</script>

<style scoped>
button {
  margin: 4px;
}
</style>
