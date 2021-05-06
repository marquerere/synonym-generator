<template>
  <div
    class="flex flex-row items-center flex-1 bg-gray-200 dark:bg-gray-700 rounded shadow py-8 px-8"
  >
    <input
      type="text"
      v-model="input"
      class="py-1 px-2 w-full bg-gray-100 text-gray-600 dark:bg-gray-500 border border-gray-500 dark:text-gray-200"
      placeholder="Insert some text to generate a list of synonyms."
    />
    <a
      class="pl-2 cursor-pointer text-gray-400 hover:text-gray-600 dark:hover:text-white"
    >
      <svg
        class="rounded-full transition-colors"
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="11" cy="11" r="8"></circle>
        <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
      </svg>
    </a>
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
