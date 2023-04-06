<template>
  <div class="flex">
    <span
      class="bg-blue-100 text-blue-800 font-medium mr-2 px-2.5 py-0.5 rounded dark:bg-blue-900 dark:text-blue-300"
      >{{ tag.name }}</span
    >
    <div class="group-hover:visible invisible">
      <PencilIcon
        class="h-5 right-0 sm:mb-[-20px] sm:ml-[12px] text-gray-600 w-4"
        @click="
          emit('emitData', { tag: tag, value: 'edit', index: props.index })
        "
      />
      <TrashIcon
        class="h-5 w-4 sm:ml-[40px] sm:mb-[-20px] text-gray-600 right-0"
        @click="
          emit('emitData', { tag: tag, value: 'delete', index: props.index })
        "
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { PencilIcon, TrashIcon } from "@heroicons/vue/24/outline";
const emit = defineEmits(["emitData"]);
const props = defineProps({
  tag: { type: Object, required: true },
  index: { type: Number, required: true },
});
</script>
