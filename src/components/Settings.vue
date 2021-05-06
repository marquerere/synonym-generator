<template>
  <div
    class="flex flex-col border border-gray-600 dark:border-gray-500 dark:bg-gray-700 dark:text-gray-200 rounded p-4 divide-y justify-center"
  >
    <div class="flex flex-row items-center space-x-2 pb-2">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="22"
        height="22"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <circle cx="12" cy="12" r="3"></circle>
        <path
          d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"
        ></path>
      </svg>
      <h2 class="text-xl font-bold">Settings</h2>
    </div>
    <div class="flex flex-col justify-center pt-2 space-y-1">
      <div class="flex flex-row">
        <span class="font-semibold pr-2">Theme:</span>
        <input
          type="checkbox"
          id="toggleTheme"
          class="hidden"
          v-model="lightMode"
          @change="$emit('toggle')"
        />
        <label
          for="toggleTheme"
          class="cursor-pointer flex items-center"
          title="Toggle Light and Dark Mode"
        >
          <h2 :class="lightMode ? '' : 'text-gray-400'" class="transition">
            Light
          </h2>
          <span class="px-2">/</span>
          <h2 :class="!lightMode ? '' : 'text-gray-400'" class="transition">
            Dark
          </h2>
        </label>
      </div>

      <div class="flex flex-row items-center">
        <span class="font-semibold pr-2">Language:</span>
        <country-dropdown />
      </div>
    </div>
  </div>
</template>

<script>
import CountryDropdown from "./CountryDropdown.vue";
export default {
  data() {
    return {
      lightMode: true,
    };
  },
  components: { CountryDropdown },
};
</script>
