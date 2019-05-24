<template>
  <table>
    <tr v-for="(row, index) in slicedRooms" :key="index">
      <td v-for="room in row" :key="room">
        <b-button
          variant="outline-primary"
          v-on:click="onClick(`facilities/${room}`)"
        >
          <img :src="require(`../assets/rooms/facilities/${room}.png`)" />
        </b-button>
      </td>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from "vue-property-decorator";

@Component
export default class Facilities extends Vue {
  rooms: Array<string> = [
    "empty",
    "hatchery",
    "lounge",
    "magic_gear",
    "operation_room",
    "laboratory",
    "meat_wagon",
    "tailwind",
    "frosty_wind",
    "revenge",
    "blood_shield",
    "blossoming_flame",
    "poison_weed",
    "thornder_weed",
    "special_ops_room",
    "blacksmith",
    "foundry",
    "secret_laboratory",
    "library",
    "ancient_bell",
    "the_seal",
    "iron_skin",
    "rainbow_flower",
    "sapling_of_yggdrasil"
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
