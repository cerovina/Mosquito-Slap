<template>
    <div>
      <h1>Catch the mosquito!</h1>
      <p>Can you beat 3000 ms?</p>
      <button @click="startGame" v-if="!started">Start</button>
      <button @click="endGame" v-else :class="{ mosquitoButton: isMosquitoButton }">{{ buttonText }}</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        started: false,
        startTime: null,
        buttonText: "Click me!",
        isMosquitoButton: false,
        mosquitoAppearTime: null, // Timestamp when mosquito button appears
      };
    },
    methods: {
      startGame() {
        this.started = true;
        this.startTime = Date.now();
        this.buttonText = "I can hear it!";
        setTimeout(() => {
          this.buttonText = "";
          this.isMosquitoButton = true;
          this.mosquitoAppearTime = Date.now(); // Record timestamp when the mosquito appears
        }, this.randomDelay());
      },
      endGame() {
        if (!this.buttonText) {
          const reactionTime = this.mosquitoAppearTime - this.startTime; // Calculate reaction time
          this.started = false;
          this.isMosquitoButton = false;
          this.$emit("gameOver", reactionTime);
        }
      },
      randomDelay() {
        return Math.floor(Math.random() * 3000) + 1000; // Random delay between 1 to 4 seconds
      },
    },
  };
  </script>
  
  <style scoped>
  .mosquitoButton {
    background-image: url('@/assets/komarac.png');
    background-size: cover;
    width: 400px;
    height: 325px;
  }
  
  p {
    padding: 30px;
  }
  
  h1 {
    padding-top: 30px;
    color: yellow
  }
  </style>
  
