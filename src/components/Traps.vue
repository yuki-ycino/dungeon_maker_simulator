<template>
  <table>
    <tr v-for="(row, index) in slicedRooms" :key="index">
      <td v-for="room in row" :key="room">
        <b-button
          variant="outline-primary"
          v-on:click="onClick(`traps/${room}`)"
        >
          <img :src="require(`../assets/rooms/traps/${room}.png`)" />
        </b-button>
      </td>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from "vue-property-decorator";

@Component
export default class Traps extends Vue {
  rooms: Array<string> = [
    "empty",
    "arrow",
    "ice",
    "pit",
    "rock",
    "distortion",
    "guillotine",
    "hunger",
    "ignition",
    "incineration",
    "return",
    "venom",
    "curse",
    "explosion",
    "extraction",
    "thunder",
    "blitz",
    "exploit",
    "combustion",
    "crossbow",
    "curtain_of_darkness",
    "electric_field",
    "explosive_arrow",
    "icebolt",
    "lightning",
    "multishot",
    "poison_arrow",
    "poison_leak",
    "skewer",
    "slingshot",
    "meteor",
    "arrows",
    "chain_lightning",
    "electrical_short",
    "chaos_arrow",
    "chaos_rain",
    "ice_pit",
    "frost_storm",
    "fire_pillar",
    "fire_storm",
    "meteor_shower",
    "disease",
    "infection",
    "plague",
    "arrow_bomb",
    "big_explosion",
    "curse_wave",
    "big_bang",
    "white_frost",
    "death_wave",
    "lightning_rod",
    "flamethrower",
    "snowman",
    "sting",
    "death_and_corruption",
    "electric_discharge",
    "plague_spreader",
    "frozen_mist",
    "crater",
    "lightning_bolt",
    "broken_mirror",
    "swamp_monster",
    "yggdrasil"
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
