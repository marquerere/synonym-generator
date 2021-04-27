<template>
  <div class="flex flex-row justify-center">
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
          v-show="wordList.length > 1 && index != wordList.length - 1"
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
  </div>
  <div class="flex justify-center">
    <button
      @click="handleClick()"
      class="border border-white rounded py-4 px-8 text-white transition hover:bg-purple-500 lato"
    >
      Generate!
    </button>
  </div>
  <div class="flex flex-row justify-center">
    <div
      v-for="key in Object.keys(synonymList)"
      :key="key"
      class="flex flex-col space-y-2 p-2 pt-8 text-white uppercase text-center"
    >
      <div class="text-xl font-bold">{{ key }}</div>
      <div v-for="synonym in synonymList[key]" :key="synonym" class="text-xs">
        {{ synonym }}
      </div>
      <div v-if="!synonymList[key].length" class="text-xs text-red-500">
        No synonyms found.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WordInput",
  data() {
    return {
      wordList: [{ word: "" }],
      synonymList: {},
      result: "",
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
    handleClick() {
      this.synonymList = {};
      this.wordList.forEach((entry) => {
        let word = entry.word;
        if (word) {
          this.synonymList[word] = [];
          this.callApi(word);
        }
      });

      console.log(this.synonymList);
    },
    callApi(word) {
      fetch(`https://api.dictionaryapi.dev/api/v2/entries/en_US/${word}`, {
        method: "GET",
      })
        .then((res) => {
          if (res.ok) {
            return res.json();
          }
        })
        .then((json) => {
          json.map((entry) => {
            console.log(entry);
            if (entry["meanings"]) {
              entry["meanings"].map((meaning) => {
                console.log(meaning);
                if (meaning["definitions"]) {
                  meaning["definitions"].map((definition) => {
                    console.log(definition);
                    if (definition["synonyms"]) {
                      definition["synonyms"].map((synonym) => {
                        console.log(synonym);
                        if (!this.synonymList[word].includes(synonym)) {
                          this.synonymList[word].push(synonym);
                        }
                      });
                    }
                  });
                }
              });
            }
          });
        })
        .catch((err) => {
          console.log(err);
          // In case a custom JSON error response was provided
          if (err.json) {
            return err.json.then((json) => {
              // set the JSON response message
              console.log(json.message);
            });
          }
        });
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
