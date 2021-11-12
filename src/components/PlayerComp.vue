<template>
  <div>
    <div class="player-panel" v-bind:class="{winner:player.isWin, playing:player.id===idPlaying}">
      <div class="player-name" v-if="player.isWin">Winner</div>
      <div class="player-name" v-else>{{ player.name }}</div>
      <div class="player-score">{{ player.score }}</div>
      <div class="player-current-box">
        <div class="player-current-label">Current</div>
        <div class="player-current-score">{{ player.rollScore }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import Player from "../model/Player";

export default {
  name: "player-comp",
  data() {
    return {}
  },
  props: {
    player: Player,
    idPlaying: Number
  },
  methods: {}

};
</script>

<style>
.playing {
  color: red;
}
</style>
