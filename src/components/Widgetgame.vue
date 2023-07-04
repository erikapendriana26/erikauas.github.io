<template>
  <div>
    <h2>Tebak Angka</h2>
    <p v-if="!gameOver">Tebak angka antara 1 dan 100:</p>
    <div v-if="!gameOver">
      <input type="number" v-model.number="userGuess" />
      <button @click="checkGuess">Tebak</button>
    </div>
    <p v-if="gameOver">Permainan Selesai! Angka yang benar adalah {{ randomNumber }}.</p>
    <button @click="resetGame" v-if="gameOver">Mulai Ulang</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      randomNumber: Math.floor(Math.random() * 100) + 1,
      userGuess: null,
      gameOver: false,
    };
  },
  methods: {
    checkGuess() {
      if (this.userGuess === this.randomNumber) {
        this.gameOver = true;
      } else if (this.userGuess < this.randomNumber) {
        alert("Tebakan Anda terlalu rendah!");
      } else {
        alert("Tebakan Anda terlalu tinggi!");
      }
      this.userGuess = null;
    },
    resetGame() {
      this.randomNumber = Math.floor(Math.random() * 100) + 1;
      this.userGuess = null;
      this.gameOver = false;
    },
  },
};
</script>
