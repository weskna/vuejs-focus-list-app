<template>
  <div class="container mx-auto p-10">
    <ul class="bg-yellow-200 shadow-xl max-h-72 overflow-y-auto">
      <li
        v-for="listItem in list"
        class="
          p-2
          mx-4
          border-b border-gray-500 border-opacity-30
          flex
          justify-between
          text-gray-900
        "
      >
        <span>{{ listItem.value }}</span>
        <span>
          <button v-on:click="">
            <svg id="icon-pencil2" viewBox="0 0 32 32">
              <path
                d="M12 20l4-2 14-14-2-2-14 14-2 4zM9.041 27.097c-0.989-2.085-2.052-3.149-4.137-4.137l3.097-8.525 4-2.435 12-12h-6l-12 12-6 20 20-6 12-12v-6l-12 12-2.435 4z"
              ></path>
            </svg>
          </button>
        </span>
      </li>
    </ul>

    <div class="flex justify-center mt-10 mb-4">
      <input
        v-on:keydown.enter="
          addToList($event.target.value);
          $event.target.value = '';
        "
        ref="input"
        placeholder="What is your focus today?"
        class="
          border-b border-gray-500
          text-gray-400
          bg-transparent
          text-center
          px-4
          py-1
          transition
          duration-150
          ease-in-out
        "
        :class="{ 'border-red-500': error, 'focus:border-green-500': !error }"
      />
      <button
        v-on:click="
          addToList($refs.input.value);
          $refs.input.value = '';
        "
        class="px-4"
      >
        <svg
          id="icon-pushpin"
          class="w-6 h-6 text-gray-500"
          :class="{ 'text-red-500': error }"
          viewBox="0 0 32 32"
        >
          <path
            fill="currentColor"
            d="M17 0l-3 3 3 3-7 8h-7l5.5 5.5-8.5 11.269v1.231h1.231l11.269-8.5 5.5 5.5v-7l8-7 3 3 3-3-15-15zM14 17l-2-2 7-7 2 2-7 7z"
          ></path>
        </svg>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        {
          value: 'Vue.js',
        },
      ],
      error: false,
    };
  },
  methods: {
    addToList(value) {
      if (value) {
        this.error = false;
        this.list.push({
          value: value,
        });
      } else {
        this.error = true;
      }
    },
  },
};
</script>

<style scoped>
ul {
  font-family: 'Courgette', cursive;
}
li:last-of-type {
  border: none;
}
:focus-visible {
  outline: none;
}
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}
::-webkit-scrollbar-thumb {
  background: #556984;
  border-radius: 2rem;
}
::-webkit-scrollbar-thumb:hover {
  background: #b3afb3;
}
::-webkit-scrollbar-track {
  background: #1f2937;
  border-radius: 0px;
  box-shadow: inset 0px 0px 0px 0px #f0f0f0;
}
</style>
