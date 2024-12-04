<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return [
        {
          id: 0,
          name: "",
          dpi: "",
          attended: false,
          observations: "",
        },
      ];
    },
  },
});

const assistants = ref(props.modelValue);

const emitter = defineEmits(["update:modelValue"]);

const handleRemove = (id) => {
  assistants.value = assistants.value.filter((assistant) => assistant.id !== id);
};

watch(
  assistants,
  (oldData, newData) => {
    emitter("update:modelValue", assistants);
  },
  { deep: true }
);
</script>
<template>
  <table class="w-full border-collapse border border-gray-300 bg-white shadow-md hidden md:table">
    <thead>
      <tr class="bg-gray-200">
        <th class="border border-gray-300 p-3 text-left">Name</th>
        <th class="border border-gray-300 p-3 text-left">DPI</th>
        <th class="border border-gray-300 p-3 text-left">Attended</th>
        <th class="border border-gray-300 p-3 text-left">Observations</th>
        <th class="border border-gray-300 p-3 text-left"></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(assistant, index) in assistants" :key="`assistant_row_${index}`">
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="assistant.name"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="assistant.dpi"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <div class="flex items-center">
            <input
              type="checkbox"
              id="attendedCheckbox"
              class="w-5 h-5 text-blue-500 border-gray-300 rounded focus:ring-2 focus:ring-blue-500"
              v-model="assistant.attended"
              :value="true"
            />
            <label for="attendedCheckbox" class="ml-2 text-gray-700">Attended</label>
          </div>
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="assistant.observations"
          />
        </td>
        <td class="border border-gray-300 p-2 flex justify-center items-center">
          <button
            type="button"
            class="w-8 h-8 flex justify-center items-center rounded-full bg-red-600 text-white mb-4"
            @click="handleRemove(assistant.id)"
          >
            <Icon name="material-symbols-light:delete" size="18" />
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
