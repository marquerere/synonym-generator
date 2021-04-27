<template>
  <div class="flex flex-col items-center justify-center space-y-4 py-8">
    <div class="text-center text-white lato tracking-widest">
      <h1 class="font-black uppercase text-3xl ">
        synonym generator
      </h1>
      <h2>
        Select up to 5 words then press Generate.
      </h2>
    </div>
    <div>
      <word-input />
    </div>

    <word-roulette />
  </div>
</template>

<script>
import WordRoulette from "./components/WordRoulette.vue";
import WordInput from "./components/WordInput.vue";

export default {
  name: "App",
  components: {
    WordRoulette,
    WordInput,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@100;300;400;700;900&display=swap");
.lato {
  font-family: "Lato", sans-serif;
}
</style>
