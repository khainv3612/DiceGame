<template>
  <div>
    <div v-bind:class="getClassDice">
      <div class="face1">1</div>
      <div class="face2">2</div>
      <div class="face3">3</div>
      <div class="face4">4</div>
      <div class="face5">5</div>
      <div class="face6">6</div>
    </div>
  </div>
</template>

<script>
import Dice from "../model/Dice";

export default {
  name: "DiceComp",
  data: function () {
    return {}
  },
  props: {
    diceRolled: Dice
  },
  computed: {
    getClassDice() {
      return "spinner dice-" + ++this.diceRolled.id;
    }
  }
};
</script>

<style></style>
