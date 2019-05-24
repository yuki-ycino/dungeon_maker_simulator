<template>
  <div class="dungeon">
    <table>
      <tr v-for="row in rows" :key="row">
        <td v-for="col in cols" :key="`${row}-${col}`">
          <Room :room-id="`${row}-${col}`" />
        </td>
      </tr>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

import Room from "./Room.vue";

@Component({
  components: {
    Room
  }
})
export default class Dungeon extends Vue {
  @Prop() rows!: number;
  @Prop() cols!: number;
}
</script>

<style scoped>
table td {
  border: 0;
  padding: 0;
}

.button {
  height: auto;
  border-width: 0;
}
</style>
