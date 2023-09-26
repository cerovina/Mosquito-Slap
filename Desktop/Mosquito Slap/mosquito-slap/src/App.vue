<template>
  <div id="app">
    <theGame @gameOver="showResult" v-if="!gameOver" />
    <theResult v-else :reactionTime="reactionTime" @restartGame="startGame" />
  </div>
</template>

<script>
import theGame from "./components/theGame.vue"
import theResult from "./components/theResult.vue";

export default {
  data() {
    return {
      gameOver: false,
      reactionTime: null,
    };
  },
  methods: {
    showResult(reactionTime) {
      this.gameOver = true;
      this.reactionTime = reactionTime;
    },
    startGame() {
      this.gameOver = false;
      this.reactionTime = null;
    },
  },
  components: {
    theGame,
    theResult,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #ffffff;
  margin-top: 20px;
}

button {
  padding: 40px 80px;
  font-size: 1.5rem;
}
</style>
