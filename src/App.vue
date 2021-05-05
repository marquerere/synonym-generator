<template>
  <div :class="mode">
    <div class="app bg-white text-gray-900 dark:bg-gray-800 dark:text-white">
      <nav-bar @toggle="toggleTheme" />
      <word-input />
      <user-input />
    </div>
  </div>

  <word-roulette />
</template>

<script>
import NavBar from "./components/NavBar.vue";
import WordRoulette from "./components/WordRoulette.vue";
import WordInput from "./components/WordInput.vue";
import UserInput from "./components/UserInput.vue";

export default {
  name: "App",
  data() {
    return {
      mode: "",
    };
  },
  components: {
    WordRoulette,
    WordInput,
    UserInput,
    NavBar,
  },
  methods: {
    toggleTheme() {
      this.mode = this.mode === "" ? "dark" : "";
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@100;300;400;700;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Lato", sans-serif;
}

.app {
  width: 100vw;
  min-height: 100vh;
}
</style>
