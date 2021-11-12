<template>
  <div id="app">
    <div class="wrapper clearfix">
      <lst-player v-bind:lstPlayer="lstPLayer" v-bind:idPlaying="idPlaying"></lst-player>
      <button class="control btn-new"><span class="ion-ios-plus-outline"></span>New game</button>
      <button class="control btn-roll" v-on:click="rollDice"><span class="ion-ios-loop"></span>Roll dice</button>
      <button class="control btn-hold" v-on:click="addScore"><span class="ion-ios-download-outline"></span>Hold</button>

      <input type="number" placeholder="Final score" class="final-score">
      <lst-dice-comp v-bind:diceRolleds="diceRolleds"></lst-dice-comp>
    </div>
  </div>
</template>

<script>
import LstDiceComp from "./components/LstDiceComp";
import DiceComp from "./components/DiceComp";
import PlayerComp from "./components/PlayerComp";
import LstPlayer from "./components/LstPlayer";
import Dice from "./model/Dice";
import Player from "./model/Player";

export default {
  name: "app",
  data() {
    return {
      isFirstLoad: true,
      prefixImage: './assets/image',
      amountDice: 2,
      winScore: 5,
      dices: [
        {id: 0, image: this.prefixImage + 'dice-1.png', value: 1},
        {id: 1, image: this.prefixImage + 'dice-2.png', value: 2},
        {id: 2, image: this.prefixImage + 'dice-3.png', value: 3},
        {id: 3, image: this.prefixImage + 'dice-4.png', value: 4},
        {id: 4, image: this.prefixImage + 'dice-5.png', value: 5},
        {id: 5, image: this.prefixImage + 'dice-6.png', value: 6},
      ],
      lstPLayer: [
        new Player(0, 'Khai', 0, 0, false),
        new Player(1, 'Nhat', 0, 0, false),
      ],
      idPlaying: 0,
      diceRolleds: [],
    };
  },

  components: {
    LstDiceComp,
    DiceComp,
    LstPlayer,
    PlayerComp
  },
  methods: {
    rollDice() {
      this.diceRolleds = [];
      for (let i = 0; i < this.amountDice; i++) {
        let result = this.dices[Math.floor(Math.random() * this.dices.length)];
        this.diceRolleds.push(new Dice(result.id, result.image, result.value));
      }
      if (!this.isFirstLoad)
        this.getRollValue();
      this.isFirstLoad = false;
      return this.diceRolleds;
    },
    getRollValue() {
      let result = 0;
      for (let dice of this.diceRolleds) {
        if (dice.value === 1) {
          this.lstPLayer[this.idPlaying].score = 0;
          setTimeout(() => alert("MAT LUOT"), 1000);
          return;
        }
        result += dice.value;
      }
      this.lstPLayer[this.idPlaying].rollScore = result;
    },
    addScore() {
      let play = this.lstPLayer[this.idPlaying];
      play.score += play.rollScore;
      play.rollScore = 0;
      play.isWin = play.score === this.winScore;
      this.idPlaying = 1 - this.idPlaying;
    }
  },
  created() {
    this.rollDice();
  }
};
</script>

<style>
@import url("./assets/css/style.css");
@import url("./assets/css/style-dice.css");

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothdsding: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
