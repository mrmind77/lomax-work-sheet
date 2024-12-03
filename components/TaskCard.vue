<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return {
        task: "",
        description: "",
        status: "",
        observations: "",
      };
    },
  },
});

const task = ref(props.modelValue);

const emitter = defineEmits(["update:modelValue"]);

watch(
  task,
  (oldData, newData) => {
    emitter("update:modelValue", task);
  },
  { deep: true }
);
</script>
<template>
  <div class="md:hidden space-y-4">
    <div class="bg-white shadow-md rounded-lg p-4 border border-gray-300">
      <div class="space-y-4">
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Task</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.task"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Description</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.description"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Status</label>
          <select
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.status"
          >
            <option value="" selected disabled>Choose status</option>
            <option value="done">Done</option>
            <option value="pending">Pending</option>
            <option value="canceled">Canceled</option>
            <option value="in-progress">In Progress</option>
          </select>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700 mb-1">Observation</label>
          <input
            type="text"
            class="block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.observation"
          />
        </div>
      </div>
    </div>
  </div>
</template>
