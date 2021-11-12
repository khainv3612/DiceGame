<template>
  <div>
    <div id="dice-1" class="dice">
      <dice-comp v-bind:diceRolled="diceRolleds[0]"></dice-comp>
    </div>

    <div id="dice-2" class="dice">
      <dice-comp v-bind:diceRolled="diceRolleds[1]"></dice-comp>
    </div>
  </div>
</template>


<script>
import DiceComp from "./DiceComp";

export default {
  name: "LstDiceComp",
  data() {
    return {}
  },
  props: {
    diceRolleds: Array
  },
  components: {
    DiceComp
  },
  methods: {}
}
</script>

<style scoped>

</style>
