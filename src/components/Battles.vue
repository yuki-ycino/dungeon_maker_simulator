<template>
  <table>
    <tr v-for="(row, index) in slicedRooms" :key="index">
      <td v-for="room in row" :key="room">
        <b-button
          variant="outline-primary"
          v-on:click="onClick(`battles/${room}`)"
        >
          <img :src="require(`../assets/rooms/battles/${room}.png`)" />
        </b-button>
      </td>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from "vue-property-decorator";

@Component
export default class Battles extends Vue {
  rooms: Array<string> = [
    "empty",
    "arena",
    "barrier",
    "battle",
    "ambush",
    "blood_altar",
    "darkness",
    "excess",
    "frenzy",
    "iron_maiden",
    "meditation",
    "panic",
    "rage",
    "sloth",
    "solitude",
    "sprout",
    "sword_and_shield",
    "amplify",
    "gigantify",
    "graveyard",
    "betrayal",
    "temptation",
    "vampire",
    "sacrifice",
    "bloodlust",
    "double_giant",
    "haste",
    "scream",
    "warhorn",
    "three_gianteers",
    "gunpowder",
    "pressure",
    "dynamite",
    "blood_pool",
    "tree_of_life",
    "healing_wind",
    "bigger_room",
    "bigger_fight",
    "necropolis",
    "mirror_room",
    "prism",
    "shield_of_steel",
    "iron_wall",
    "iron_curtain",
    "steel_thorn",
    "thorn_bush",
    "the_absolute",
    "swirl_of_anger",
    "silent_temple",
    "demonic_barrier",
    "bloody_mist",
    "death_mist",
    "infinity_clock"
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
