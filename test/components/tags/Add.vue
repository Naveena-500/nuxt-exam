<template>
  <div>
    <div>
      <label
        for="name"
        class="block text-sm font-medium leading-6 text-gray-900"
        >Tag Name</label
      >
      <div class="mt-2">
        <input
          placeholder="Enter tag name"
          v-model="tagName"
          type="text"
          name="name"
          id="name"
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
        @click="save(false)"
      >
        Save
      </button>

      <button
        type="button"
        class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:col-start-1 sm:mt-0"
        @click="cancel(false)"
        ref="cancelButtonRef"
      >
        Cancel
      </button>
    </div>
  </div>
</template>
<script setup lang="ts">
const tagName = ref("");

const emit = defineEmits(["formSave", "hide"]);
const cancel = (form: any) => {
  emit("hide", form);
};
const save = (form: any) => {
  emit("hide", form);
  tagName.value.length ? emit("form-save", tagName.value) : "";
};
</script>
