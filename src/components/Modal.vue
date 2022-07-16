<template>
  <div
    class="modal bg-black/20 fixed top-0 w-full h-full flex justify-center items-center"
  >
    <div
      class="modal bg-white shadow-xl rounded-xl w-3/5 h-[400px] p-8 items-center justify-center"
      role="dialog"
      ref="modal"
    >
      <div class="relative flex justify-between items-center">
        <h1 class="font-medium text-2xl py-2">Add Item</h1>
        <button
          class="font-medium text-4xl absolute right-0 top-0 -mt-5 -mr-2 hover:text-red-400"
          @click="$emit('close')"
        >
          ×
        </button>
      </div>
      <div class="py-5">
        <textarea
          v-model="typingText"
          name="txtArea"
          id=""
          rows="5"
          placeholder="write here"
          class="w-full resize-none outline-none border rounded-xl text-xl p-4"
        ></textarea>
      </div>
      <div
        class="flex justify-end hover:drop-shadow-[0_12px_9px_rgba(39,150,130,0.18)] pt-3"
      >
        <button
          class="bg-[#f5f9f9] text-gray-700 h-12 px-3 rounded-2xl text-lg font-medium"
          @click="$emit('responceText', typingText)"
        >
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";

defineEmits(['close','responceText']);
const typingText = ref('');
</script>
