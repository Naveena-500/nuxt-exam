<template>
  <div>
    <div>
      <label
        for="email"
        class="block text-sm font-medium leading-6 text-gray-900"
        >Task Name</label
      >
      <div class="mt-2">
        <input
          v-model="taskName"
          type="text"
          name="email"
          id="email"
          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div
      class="mt-5 sm:mt-6 sm:grid sm:grid-flow-row-dense sm:grid-cols-2 sm:gap-3"
    >
      <button
        type="button"
        class="inline-flex w-full justify-center rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 sm:col-start-2"
        @click="updateTask(false)"
      >
        Update
      </button>
      <button
        type="button"
        class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:col-start-1 sm:mt-0"
        @click="closeModal(false)"
        ref="cancelButtonRef"
      >
        Cancel
      </button>
    </div>
  </div>
</template>
<script setup>
const props = defineProps({
  editData: Object,
});
const taskName = ref("");
taskName.value = props.editData ? props.editData.name : "";
// Close modal
const emit = defineEmits(["hide", "update-task"]);
const closeModal = (close) => {
  emit("hide", close);
};
// Update task
const updateTask = (close) => {
  emit("hide", close);
  emit("update-task", props.editData, taskName);
};
</script>
