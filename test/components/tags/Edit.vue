<template>
  <div>
    <!--Edit tag starts here-->
    <div
      v-if="editInput"
      class="flex flex-row items-center h-16 bg-white w-full"
    >
      <div class="flex-grow">
        <div class="relative w-full">
          <input
            placeholder="Enter tag name"
            v-model="selectedTag"
            type="text"
            class="flex w-full border rounded-lg focus:outline-none border-gray-300 focus:border-indigo-300 h-10"
          />
        </div>
      </div>
      <div class="ml-4">
        <!--Update button-->
        <button
          class="flex items-center justify-center bg-indigo-600 hover:bg-indigo-500 rounded-lg text-white p-2 px-3 flex-shrink-0"
          @click="edit(selectedTag), (editInput = false)"
        >
          Save
        </button>
      </div>
    </div>
    <!--Edit tag ends here-->
  </div>
</template>
<script setup lang="ts">
const props = defineProps({
  tag: { type: String, required: true }, // Edited tag
});

const selectedTag = ref(props.tag.name);
// Close input after editing
const editInput = ref("true");
const emit = defineEmits(["edit"]);
const edit = (data: any) => {
  emit("edit", { uid: props.tag.uid, tag: data });
  // Empty the Tag value
  selectedTag.value = "";
};
</script>
