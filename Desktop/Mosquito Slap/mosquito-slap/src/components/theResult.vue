<template>
    <div>
      <h1>Reaction Time: <span class="resultText">{{ reactionTime }}</span> ms</h1>
      <button @click="restartGame">Play Again</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      reactionTime: Number,
    },
    methods: {
      restartGame() {
        this.$emit("restartGame");
      },
    },
  };
  </script>
  
  <style scoped>
    .resultText {
      color: red;
    }
  </style>