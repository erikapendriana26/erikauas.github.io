<template>
    <div>
      <h2>Stopwatch</h2>
      <div class="stopwatch">{{ formattedTime }}</div>
      <button @click="startStopwatch">Start</button>
      <button @click="stopStopwatch">Stop</button>
      <button @click="resetStopwatch">Reset</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        startTime: 0,
        elapsedTime: 0,
        timerInterval: null,
      };
    },
    computed: {
      formattedTime() {
        const milliseconds = Math.floor(this.elapsedTime % 1000 / 10);
        const seconds = Math.floor(this.elapsedTime / 1000 % 60);
        const minutes = Math.floor(this.elapsedTime / 1000 / 60 % 60);
        const hours = Math.floor(this.elapsedTime / 1000 / 60 / 60);
  
        return `${this.pad(hours)}:${this.pad(minutes)}:${this.pad(
          seconds
        )}.${this.pad(milliseconds)}`;
      },
    },
    methods: {
      startStopwatch() {
        this.startTime = Date.now() - this.elapsedTime;
        this.timerInterval = setInterval(this.updateStopwatch, 10);
      },
      stopStopwatch() {
        clearInterval(this.timerInterval);
      },
      resetStopwatch() {
        this.stopStopwatch();
        this.elapsedTime = 0;
      },
      updateStopwatch() {
        const currentTime = Date.now();
        this.elapsedTime = currentTime - this.startTime;
      },
      pad(number) {
        return (number < 10 ? "0" : "") + number;
      },
    },
  };
  </script>
  
  <style scoped>
  .stopwatch {
    font-size: 2rem;
    text-align: center;
  }
  .stopwatch {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }
  
  .timer {
    font-size: 48px;
    margin-bottom: 20px;
  }
  
  .buttons {
    display: flex;
    justify-content: center;
  }
  
  .button {
    margin: 0 10px;
    padding: 8px 16px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
  }
  
  .button:hover {
    background-color: #0056b3;
  }
  </style>
  