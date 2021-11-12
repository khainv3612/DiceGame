<template>
  <div>
    <div v-for="player in lstPlayer ">
      <div>
        <player-comp v-bind:player="player" v-bind:id-playing="idPlaying"></player-comp>
      </div>
    </div>
  </div>
</template>

<script>
import PlayerComp from "./PlayerComp";

export default {
  name: "LstPlayer",
  data() {
    return {}
  },
  props: {
    lstPlayer: Array,
    idPlaying: Number
  },
  components: {PlayerComp},
  methods: {}
}
</script>

<style scoped>
</style>
