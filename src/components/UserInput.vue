<template>
  <div class="flex flex-row justify-center w-full">
    <div class="flex flex-row justify-center w-full items-center">
      <input
        type="text"
        v-model="input"
        class="py-1 px-2 w-1/4"
        placeholder="Insert some text to generate a list of synonyms."
      />
      <a class="p-1 cursor-pointer">
        <svg
          class="rounded-full"
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="#ffffff"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <circle cx="11" cy="11" r="8"></circle>
          <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
        </svg>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserInput",
  data() {
    return {
      input: "",
      language: "",
      words: [],
    };
  },
};
</script>

<style></style>
