<template>
  <div
    class="relative inline-block text-left text-gray-800 w-48"
    v-click-away="closeMenu"
  >
    <div>
      <span class="rounded-md shadow-sm">
        <button
          @click="isMenuOpen = !isMenuOpen"
          type="button"
          class="inline-flex items-center justify-between w-full rounded-md border border-gray-300 px-2 py-1 bg-white text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-100 active:text-gray-800 transition ease-in-out duration-150"
          id="options-menu"
          aria-haspopup="true"
          aria-expanded="true"
        >
          <span> {{ selectedCountry.name }} </span>
        </button>
      </span>
    </div>
    <transition
      enter-active-class="transition ease-out duration-100"
      enter-class="transform opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-class="transform opacity-100 scale-100"
      leave-to-class="transform opacity-0 scale-95"
    >
      <div
        v-if="isMenuOpen"
        class="origin-top-right absolute right-0 mt-1 rounded-md shadow-lg text-sm overflow-hidden border z-20"
      >
        <div
          class="rounded-md bg-white shadow-xs max-h-48 w-48 overflow-y-auto"
          role="menu"
          aria-orientation="vertical"
          aria-labelledby="options-menu"
        >
          <div
            v-for="country in countries"
            :key="country.value"
            @click="selectCountry(country)"
            class="hover:bg-gray-200 cursor-pointer p-2"
          >
            {{ country.name }}
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import { directive } from "vue3-click-away";

export default {
  directives: {
    ClickAway: directive,
  },
  data() {
    return {
      isMenuOpen: false,
      countries: [
        { value: "en_US", svg: "", name: "English (US)" },
        { value: "hi", svg: "", name: "Hindi" },
        { value: "es", svg: "", name: "Spanish" },
        { value: "fr", svg: "", name: "French" },
        { value: "ja", svg: "", name: "Japanese" },
        { value: "ru", svg: "", name: "Russian" },
        { value: "en_GB", svg: "", name: "English (UK)" },
        { value: "de", svg: "", name: "German" },
        { value: "it", svg: "", name: "Italian" },
        { value: "ko", svg: "", name: "Korean" },
        { value: "pt-BR", svg: "", name: "Brazilian Portuguese" },
        { value: "ar", svg: "", name: "Arabic" },
        { value: "tr", svg: "", name: "Turkish" },
      ],
      selectedCountry: { value: "en_US", svg: "", name: "English (US)" },
    };
  },
  methods: {
    closeMenu() {
      this.isMenuOpen = false;
    },
    selectCountry(country) {
      this.selectedCountry = country;
      this.closeMenu();
    },
  },
};
</script>
