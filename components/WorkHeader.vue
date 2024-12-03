<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return {
        technicianName: "",
        locationName: "",
        locationResponsible: "",
        createdAt: "",
        workType: "",
      };
    },
  },
});

const emitter = defineEmits(["update:modelValue"]);

const workOrderHeading = ref(props.modelValue);

watch(
  workOrderHeading,
  (newData, oldData) => {
    emitter("update:modelValue", workOrderHeading);
  },
  { deep: true }
);
</script>
<template>
  <div class="space-y-4">
    <div class="flex items-center space-x-4 justify-between">
      <h2 class="text-primary text-lg font-bold">Technician Information</h2>
      <select class="border border-gray-300 p-2 rounded flex-grow max-w-xs" v-model="workOrderHeading.workType">
        <option value="" disabled selected>Select a work type</option>
        <option value="installation">Installation</option>
        <option value="support">Support</option>
        <option value="capacitation">Capacitation</option>
        <option value="verification-tests">Verification Tests</option>
      </select>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <input
        type="text"
        placeholder="Technician Name"
        class="border border-gray-300 p-2 rounded w-full"
        v-model="workOrderHeading.technicianName"
      />

      <input
        type="text"
        placeholder="Location Name"
        class="border border-gray-300 p-2 rounded w-full"
        v-model="workOrderHeading.locationName"
      />

      <input
        type="text"
        placeholder="Location Responsible"
        class="border border-gray-300 p-2 rounded w-full"
        v-model="workOrderHeading.locationResponsible"
      />

      <input
        type="datetime-local"
        class="border border-gray-300 p-2 rounded w-full"
        v-model="workOrderHeading.createdAt"
      />
    </div>
  </div>
</template>
