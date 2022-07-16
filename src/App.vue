<template>
  <div
    class="min-h-screen bg-[#fefefe] w-full flex items-center justify-center"
  >
    <!-- container -->
    <div
      class="flex bg-[#f5f9f9] p-5 flex-col justify-center rounded-[30px] w-[680px]"
    >
      <!--col1 todo and badge -->
      <div class="flex items-center pt-6 justify-between">
        <h1 class="flex text-2xl font-medium text-gray-800">To do</h1>
        <span
          class="flex bg-[#e8f1f0] text-[#279682] text-lg p-1 rounded-xl px-3"
          >{{ myList.length }}</span
        >
      </div>
      <!-- col2 button -->
      <div class="flex w-full mx-auto py-4">
        <button
          class="w-full text-4xl text-[#279682] h-[4rem] rounded-2xl bg-[#e7f0ef] hover:bg-[#cad4d4]"
          @click="open = true"
        >
          +
        </button>
      </div>
      <!-- col3 list -->
      <div>
        <ul v-for="(item, index) in myList" class="my-3">
          <div
            class="flex items-center justify-between p-2 border rounded-xl text-xl cursor-pointer hover:bg-white/50"
            @click="item.checked = !item.checked"
          >
            <div>
              <input
                type="checkbox"
                :checked="item.checked"
                name=""
                id=""
                class="w-5 h-5 accent-[#279682]"
              />
              <span class="ml-3" :class="{ 'line-through': item.checked }">{{
                item.message
              }}</span>
            </div>
            <button class="text-sm" @click="removeItem(index)">❌</button>
          </div>
        </ul>
      </div>
    </div>
  </div>

  <teleport to="body">
    <div v-if="open">
      <Modal @close="open = false" @responceText="addtoList" />
    </div>
  </teleport>
</template>

<script setup>
import { reactive, ref } from "vue";
import Modal from "./components/Modal.vue";

const open = ref(false);
const myList = reactive([]);

const addtoList = (item) => {
  myList.push({ id: Date.now(), message: item, checked: false });
  open.value = false;
};
const removeItem = (index) => {
  myList.splice(index,1);
};
</script>
