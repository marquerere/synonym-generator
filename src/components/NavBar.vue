<template>
  <nav
    class="w-full flex flex-row  lato tracking-widest py-4 px-8 items-center justify-between"
  >
    <h1 class="font-black uppercase text-2xl ">
      Synonym Generator
    </h1>
    <div class="flex flex-row space-x-4 items-center">
      <select class="py-1 px-2 bg-gray-100 dark:text-black dark:bg-white">
        <option value="en_US">English (US)</option>
        <option value="hi">Hindi</option>
        <option value="es">Spanish</option>
        <option value="fr">French</option>
        <option value="ja">Japanese</option>
        <option value="ru">Russian</option>
        <option value="en_GB">English (UK)</option>
        <option value="de">German</option>
        <option value="it">Italian</option>
        <option value="ko">Korean</option>
        <option value="pt-BR">Brazilian Portuguese</option>
        <option value="ar">Arabic</option>
        <option value="tr">Turkish</option>
      </select>
      <input
        type="checkbox"
        id="toggleTheme"
        class="hidden checkbox"
        v-model="lightMode"
        @change="$emit('toggle')"
      />
      <label
        for="toggleTheme"
        class="cursor-pointer flex items-center"
        title="Toggle Light and Dark Mode"
      >
        <svg
          v-if="lightMode"
          xmlns="http://www.w3.org/2000/svg"
          width="22"
          height="22"
          viewBox="0 0 24 24"
          fill="none"
          stroke="#000000"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
        </svg>
        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          width="22"
          height="22"
          viewBox="0 0 24 24"
          fill="none"
          stroke="#ffffff"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <circle cx="12" cy="12" r="5" />
          <path
            d="M12 1v2M12 21v2M4.2 4.2l1.4 1.4M18.4 18.4l1.4 1.4M1 12h2M21 12h2M4.2 19.8l1.4-1.4M18.4 5.6l1.4-1.4"
          />
        </svg>
      </label>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      lightMode: true,
    };
  },
};
</script>

<style></style>
