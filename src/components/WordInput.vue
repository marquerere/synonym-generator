<template>
  <div
    v-for="(input, index) in wordList"
    :key="`word-${index}`"
    class="flex p-2 flex-col"
  >
    <input type="text" v-model="input.word" class="rounded py-1 px-2" />
    <div class="flex flex-row mx-auto pt-2 space-x-1">
      <svg
        v-show="wordList.length > 1 && index > 0"
        @click="moveInput(index, index - 1)"
        class="cursor-pointer opacity-40 hover:opacity-100 transition"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="#F7F4E9"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="10" />
        <path d="M12 8l-4 4 4 4M16 12H9" />
      </svg>
      <svg
        v-show="wordList.length < 5 && index === wordList.length - 1"
        @click="addInput()"
        xmlns="http://www.w3.org/2000/svg"
        class="cursor-pointer opacity-40 hover:opacity-100 transition"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="#438945"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="10"></circle>
        <line x1="12" y1="8" x2="12" y2="16"></line>
        <line x1="8" y1="12" x2="16" y2="12"></line>
      </svg>
      <svg
        v-show="wordList.length > 1"
        @click="removeInput(index)"
        class="cursor-pointer opacity-40 hover:opacity-100 transition"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="#E40C2B"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="10"></circle>
        <line x1="15" y1="9" x2="9" y2="15"></line>
        <line x1="9" y1="9" x2="15" y2="15"></line>
      </svg>
      <svg
        v-show="wordList.length > 1 && index < 4"
        @click="moveInput(index, index + 1)"
        class="cursor-pointer opacity-40 hover:opacity-100 transition"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="#F7F4E9"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="10" />
        <path d="M12 8l4 4-4 4M8 12h7" />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "WordInput",
  data() {
    return {
      wordList: [{ word: "" }],
    };
  },
  methods: {
    addInput() {
      this.wordList.push({ word: "" });
    },
    removeInput(index) {
      this.wordList.splice(index, 1);
    },
    moveInput(index, target) {
      [this.wordList[index], this.wordList[target]] = [
        this.wordList[target],
        this.wordList[index],
      ];
    },
  },
};
</script>
<style>
.svg-icon {
  width: 1em;
  height: 1em;
}

.svg-icon path,
.svg-icon polygon,
.svg-icon rect {
  fill: #4691f6;
}

.svg-icon circle {
  stroke: #4691f6;
  stroke-width: 1;
}
</style>
