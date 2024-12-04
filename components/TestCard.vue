<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return {
        id: 0,
        name: "",
        description: "",
        result: "",
        expectedResult: "",
        isSuccess: false,
        observations: "",
      };
    },
  },
});

const emitter = defineEmits(["remove"]);

const handleRemove = () => {
  emitter("remove", props.modelValue.id);
};
</script>
<template>
  <div class="md:hidden space-y-4">
    <div class="bg-white shadow-md rounded-lg p-4 border border-gray-300">
      <button
        type="button"
        class="w-8 h-8 flex justify-center items-center rounded-full bg-red-600 text-white mb-4"
        @click="handleRemove"
      >
        <Icon name="material-symbols-light:delete" size="18" />
      </button>
      <div class="space-y-4">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Name</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.name"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Description</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.description"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Result</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.result"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Expected Result</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.expectedResult"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Is Success</label>
          <div class="flex items-center">
            <input
              type="checkbox"
              class="w-5 h-5 text-blue-500 border-gray-300 rounded focus:ring-2 focus:ring-blue-500"
              v-model="modelValue.isSuccess"
              :value="true"
            />
          </div>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Observations</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.observations"
          />
        </div>
      </div>
    </div>
  </div>
</template>
