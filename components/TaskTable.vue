<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return [
        {
          task: "",
          description: "",
          status: "pending",
          observations: "",
          id: 0,
        },
      ];
    },
  },
});

const tasks = ref(props.modelValue);

const emitter = defineEmits(["update:modelValue"]);

const handleRemove = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id);
};

watch(
  tasks,
  (oldData, newData) => {
    emitter("update:modelValue", tasks);
  },
  { deep: true }
);
</script>
<template>
  <table class="w-full border-collapse border border-gray-300 bg-white shadow-md hidden md:table">
    <thead>
      <tr class="bg-gray-200">
        <th class="border border-gray-300 p-3 text-left">Task</th>
        <th class="border border-gray-300 p-3 text-left">Description</th>
        <th class="border border-gray-300 p-3 text-left">Status</th>
        <th class="border border-gray-300 p-3 text-left">Observation</th>
        <th class="border border-gray-300 p-3 text-left"></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(task, index) in tasks" :key="`task_row_${index}`">
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.task"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.description"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <select
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.status"
          >
            <option value="pending">Pending</option>
            <option value="done">Done</option>
            <option value="canceled">Canceled</option>
            <option value="in-progress">In Progress</option>
          </select>
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="task.observations"
          />
        </td>
        <td class="border border-gray-300 p-2 flex justify-center items-center">
          <button
            type="button"
            class="w-8 h-8 flex justify-center items-center rounded-full bg-red-600 text-white mb-4"
            @click="handleRemove(task.id)"
          >
            <Icon name="material-symbols-light:delete" size="18" />
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
