<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return {
        task: "",
        description: "",
        status: "",
        observations: "",
        id: 0,
      };
    },
  },
});

const emitter = defineEmits(["remove"]);

const handleRemove = () => {
  emitter("remove", props.modelValue.value.id);
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
          <label class="block text-sm font-medium text-gray-700 mb-1">Task</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.task"
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
          <label class="block text-sm font-medium text-gray-700 mb-1">Status</label>
          <select
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.status"
          >
            <option value="pending">Pending</option>
            <option value="done">Done</option>
            <option value="canceled">Canceled</option>
            <option value="in-progress">In Progress</option>
          </select>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Observation</label>
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
