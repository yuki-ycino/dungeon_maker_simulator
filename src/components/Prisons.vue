<template>
  <table>
    <tr v-for="(row, index) in slicedRooms" :key="index">
      <td v-for="room in row" :key="room">
        <b-button
          variant="outline-primary"
          v-on:click="onClick(`prisons/${room}`)"
        >
          <img :src="require(`../assets/rooms/prisons/${room}.png`)" />
        </b-button>
      </td>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from "vue-property-decorator";

@Component
export default class Prisons extends Vue {
  rooms: Array<string> = [
    "empty",
    "altar_level_1",
    "altar_level_2",
    "altar_level_3",
    "altar_level_4",
    "old_prison",
    "prison",
    "iron_prison",
    "magic_prison",
    "workhouse",
    "prison_factory",
    "power_station",
    "prisoner_and_guard",
    "prisoner_lab",
    "giant_laboratory",
    "howling_prison",
    "execution_ground",
    "bloodcry"
  ];

  get slicedRooms(): Array<Array<string>> {
    return this.rooms.reduce(
      (rows: Array<Array<string>>, item) => {
        const lastRow = rows[rows.length - 1];
        if (lastRow.length === 5) {
          rows.push([item]);
          return rows;
        } else {
          lastRow.push(item);
          return rows;
        }
      },
      [[]]
    );
  }

  @Emit("set-room")
  setRoom(room: string) {}

  onClick(room: string) {
    this.setRoom(room);
  }
}
</script>

<style scoped>
img {
  width: 48px;
  height: 48px;
}

button {
  margin: 4px;
  padding: 4px;
  border: 0;
}

button:hover,
button:active,
button:focus,
button:not(:disabled):not(.disabled):active {
  background-color: #fff;
  box-shadow: none !important;
}
</style>
