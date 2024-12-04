<script setup>
definePageMeta({
  name: "Hoja de Trabajo",
});

const workOrder = ref({
  head: {
    technicianName: "",
    locationName: "",
    locationResponsible: "",
    createdAt: "",
    workType: "",
  },
  materials: [
    {
      id: 0,
      brand: "",
      model: "",
      sku: "",
      quantity: "",
      description: "",
      observations: "",
    },
  ],
  assistants: [
    {
      id: 0,
      name: "",
      dpi: "",
      attended: false,
      observations: "",
    },
  ],
  tasks: [
    {
      id: 0,
      task: "",
      description: "",
      status: "pending",
      observations: "",
    },
  ],
  tests: [
    {
      name: "",
      description: "",
      result: "",
      expectedResult: "",
      isSuccess: false,
      observations: "",
    },
  ],
});

const addMaterial = () => {
  workOrder.value.materials.push({
    brand: "",
    model: "",
    sku: "",
    quantity: "",
    description: "",
    observations: "",
    id: workOrder.value.materials.length,
  });
};

const removeMaterial = (id) => {
  workOrder.value.materials = workOrder.value.materials.filter((m) => m.id !== id);
};

const addTask = () => {
  workOrder.value.tasks.push({
    task: "",
    description: "",
    status: "pending",
    observations: "",
    id: workOrder.value.tasks.length,
  });
};

const removeTask = (id) => {
  workOrder.value.tasks = workOrder.value.tasks.filter((t) => t.id !== id);
};

const addAssistant = () => {
  workOrder.value.assistants.push({
    id: workOrder.value.assistants.length,
    name: "",
    dpi: "",
    attended: false,
    observations: "",
  });
};

const removeAssistant = (id) => {
  workOrder.value.assistants = workOrder.value.assistants.filter((a) => a.id !== id);
};
</script>
<template>
  <div class="bg-background min-h-screen p-4">
    <!-- Fixed Save Button -->
    <div class="fixed top-20 right-0 w-fit bg-transparent z-50 flex justify-center align-center p-4">
      <button class="bg-primary text-white rounded-full w-10 h-10 justify-center items-center">
        <Icon name="mdi:content-save" size="28" />
      </button>
    </div>

    <!-- Form -->
    <form class="mt-2 space-y-6">
      <WorkHeader v-model="workOrder.head" />
      <!-- Section 2: Dynamic Content -->
      <div v-if="workOrder.head.workType === 'installation'" class="space-y-4">
        <h2 class="text-primary text-lg font-bold flex justify-between">
          Materials
          <button
            type="button"
            class="bg-primary text-white rounded-full w-8 h-8 justify-center items-center"
            @click="addMaterial"
          >
            <Icon name="material-symbols:add-notes-rounded" size="18" />
          </button>
        </h2>
        <div class="overflow-x-auto">
          <!-- For desktop -->
          <MaterialTable v-model="workOrder.materials" />
          <!-- For mobile -->
          <MaterialCard
            v-for="(material, index) in workOrder.materials"
            :key="`material_card_${index}`"
            v-model="workOrder.materials[index]"
            class="mt-4"
            v-on:remove="removeMaterial"
          />
        </div>
      </div>

      <div v-if="workOrder.head.workType === 'support'" class="space-y-4">
        <h2 class="text-primary text-lg font-bold flex justify-between">
          Tasks
          <button
            type="button"
            class="bg-primary text-white rounded-full w-8 h-8 justify-center items-center"
            @click="addTask"
          >
            <Icon name="material-symbols:add-task-rounded" size="18" />
          </button>
        </h2>
        <div class="overflow-x-auto">
          <TaskTable v-model="workOrder.tasks" />

          <TaskCard
            v-for="(task, index) in workOrder.tasks"
            :key="`task_card_${index}`"
            v-model="workOrder.tasks[index]"
            v-on:remove="removeTask"
          />
        </div>
      </div>

      <div v-if="workOrder.head.workType === 'capacitation'" class="space-y-4">
        <h2 class="text-primary text-lg font-bold flex justify-between">
          Assistants
          <button
            type="button"
            class="bg-primary text-white rounded-full w-8 h-8 justify-center items-center"
            @click="addAssistant"
          >
            <Icon name="material-symbols:add-task-rounded" size="18" />
          </button>
        </h2>

        <AssistantTable v-model="workOrder.assistants" />

        <AssistantCard
          v-for="(assistant, index) in workOrder.assistants"
          :key="`assistant_card_${index}`"
          v-model="workOrder.assistants[index]"
          v-on:remove="removeAssistant"
        />
      </div>

      <div v-if="workOrder.head.workType === 'verification-tests'" class="space-y-4">
        <h2 class="text-primary text-lg font-bold">Verification Tests</h2>
        <table class="w-full border-collapse border border-gray-300">
          <thead>
            <tr>
              <th class="border border-gray-300 p-2">Test Name</th>
              <th class="border border-gray-300 p-2">Description</th>
              <th class="border border-gray-300 p-2">Result</th>
              <th class="border border-gray-300 p-2">Expected Result</th>
              <th class="border border-gray-300 p-2">Status</th>
              <th class="border border-gray-300 p-2">Observations</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><input type="text" class="border border-gray-300 p-2" /></td>
              <td><input type="text" class="border border-gray-300 p-2" /></td>
              <td><input type="text" class="border border-gray-300 p-2" /></td>
              <td><input type="text" class="border border-gray-300 p-2" /></td>
              <td>
                <select class="border border-gray-300 p-2">
                  <option value="failure">Failure</option>
                  <option value="successful">Successful</option>
                  <option value="warning">Warning</option>
                </select>
              </td>
              <td><input type="text" class="border border-gray-300 p-2" /></td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- Section 3: General Observations -->
      <div class="space-y-4">
        <h2 class="text-primary text-lg font-bold">General Observations</h2>
        <textarea
          rows="4"
          class="border border-gray-300 p-2 w-full rounded"
          placeholder="Write your observations here..."
        ></textarea>
      </div>
    </form>
  </div>
</template>
