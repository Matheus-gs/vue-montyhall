<template>
  <div id="app">
    <h2 class="app-title">Monty Hall <span>Vue.js</span></h2>
    <button class="btn-restart" @click="gameStarted = false" v-if="gameStarted">Reiniciar</button>

    <div class="game-settings" v-if="!gameStarted">
      <input
        type="text"
        id="numberOfDoors"
        v-model.number="numberOfDoors"
        size="3"
        placeholder="N° de portas"
        required
      />

      <input
        type="text"
        id="doorThatHasGift"
        v-model.number="doorThatHasGift"
        placeholder="N° da porta premiada"
        required
      />

      <button
        v-if="numberOfDoors && doorThatHasGift"
        @click="gameStarted = true"
      >
        Começar
      </button>
    </div>

    <div class="container" v-if="gameStarted">
      <span v-for="doorNumber in numberOfDoors" :key="doorNumber">
        <GameDoor
          :number="doorNumber"
          :hasGift="doorNumber === doorThatHasGift"
        />
      </span>
    </div>
  </div>
</template>

<script>
import GameDoor from "./components/GameDoor.vue";

export default {
  components: {
    GameDoor,
  },

  data: function () {
    return {
      gameStarted: false,
      numberOfDoors: null,
      doorThatHasGift: null,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  background: #000428; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to right,
    #004e92,
    #000428
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to right,
    #004e92,
    #000428
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  color: #eee;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1rem;
}

#app .app-title {
  margin-bottom: 1rem;
}

#app .app-title > span {
  color: #00df98;
}

#app .btn-restart {
  width: 180px;
  height: 40px;
  border: none;
  border-radius: 8px;
  background: rgb(162, 33, 16);
  color: #eee;
  margin-bottom: 1rem;
}

#app .container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 5rem;
}

#app .game-settings {
  width: 250px;
  display: flex;
  flex-direction: column;
}

#app .game-settings input,
#app .game-settings button {
  width: 100%;
  height: 50px;

  border-radius: 8px;
  border: 1px solid #eee;
  outline: none;

  background: none;
  color: #eee;

  margin: 0.5rem;
  padding: 1rem 0.5rem;

  transition: all 0.3s ease-in-out;
}

#app .game-settings input::placeholder {
  color: #ddd;
}

#app .game-settings input:focus,
#app .game-settings input:valid {
  border: 1px solid #00df98;
}

#app .game-settings button {
  border: 1px solid #00df98;
}

#app .game-settings button:hover {
  filter: brightness(0.9);
}

#app .game-settings input:valid ~ button {
  background: #00df98;
  color: #111;
}
</style>