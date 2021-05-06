<template>
  <div :class="mode">
    <div
      class="app antialiased flex flex-col items-center justify-center space-y-8 bg-white dark:bg-gray-900 dark:text-gray-50"
    >
      <page-header />
      <div class="flex flex-row space-x-4 w-1/2">
        <settings @toggle="toggleTheme" />
        <user-input />
      </div>
      <word-input />
    </div>
  </div>

  <word-roulette />
</template>

<script>
import PageHeader from "./components/PageHeader.vue";
import Settings from "./components/Settings.vue";
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
    PageHeader,
    WordRoulette,
    WordInput,
    UserInput,
    Settings,
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
  font-family: "Helvetica", sans-serif;
}

.app {
  width: 100vw;
  height: 100vh;
  min-height: 100vh;
}
</style>
