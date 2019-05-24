<template>
  <div>
    <b-button variant="outline-primary" v-b-modal="roomId">
      <img :src="require(`../assets/rooms/${room}.png`)" />
    </b-button>
    <b-modal :id="roomId" ref="modal" hide-header hide-footer>
      <b-nav tabs>
        <b-nav-item v-on:click="setType('battles')" :active="type === 'battles'"
          >戦闘</b-nav-item
        >
        <b-nav-item v-on:click="setType('traps')" :active="type === 'traps'"
          >罠</b-nav-item
        >
        <b-nav-item
          v-on:click="setType('facilities')"
          :active="type === 'facilities'"
          >機能</b-nav-item
        >
        <b-nav-item v-on:click="setType('prisons')" :active="type === 'prisons'"
          >監獄・祭壇</b-nav-item
        >
      </b-nav>
      <Battles v-if="type === 'battles'" v-on:set-room="setRoom" />
      <Traps v-if="type === 'traps'" v-on:set-room="setRoom" />
      <Facilities v-if="type === 'facilities'" v-on:set-room="setRoom" />
      <Prisons v-if="type === 'prisons'" v-on:set-room="setRoom" />
    </b-modal>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

import Battles from "./Battles.vue";
import Traps from "./Traps.vue";
import Facilities from "./Facilities.vue";
import Prisons from "./Prisons.vue";

@Component({
  components: {
    Battles,
    Traps,
    Facilities,
    Prisons
  }
})
export default class Room extends Vue {
  @Prop() roomId!: string;

  type: string = "battles";
  room: string = "empty";

  setType(type: string) {
    this.type = type;
  }

  setRoom(room: string) {
    this.room = room;

    const modal = this.$refs.modal as any;
    modal.hide();
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
