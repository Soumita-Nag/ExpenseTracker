<template>
  <div class="p-4 bg-gradient-to-br from-purple-900 via-violet-800 to-pink-700 rounded-md shadow-md mt-5 w-full border border-pink-400/30">
    <h3 class="text-2xl font-semibold text-white mb-4 border-b border-pink-300 pb-2">
      Transaction History
    </h3>

    <div
      v-for="item in transactions"
      :key="item.id"
      class="list relative"
    >
      <div
        :class="item.cost >= 0 ? 'plus' : 'minus'"
        class="flex justify-between items-center bg-purple-950 text-white px-4 py-2 rounded mb-2 shadow-md"
      >
        <h4 class="font-medium">{{ item.text }}</h4>
        <h4 class="font-semibold">
          ₹{{ item.cost < 0 ? item.cost * -1 : item.cost }}
        </h4>
      </div>
      <button
        class="delete-btn absolute right-[-22px] top-1/2 -translate-y-1/2 bg-pink-600 hover:bg-pink-700 text-white border-0 px-[6px] py-[2px] rounded-r cursor-pointer shadow-lg opacity-0"
        @click="deleteList(item.id)"
      >
        X
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  }
});
const emit = defineEmits(['deleteTransaction']);
const deleteList = (id) => {
  emit('deleteTransaction', id);
}
</script>

<style scoped>
.plus {
  border-right: 5px solid #19c363;
}
.minus {
  border-right: 5px solid #ff4949;
}
.delete-btn {
  line-height: 20px;
  transition: opacity 0.3s ease;
}
.list:hover .delete-btn {
  opacity: 1;
}
</style>
