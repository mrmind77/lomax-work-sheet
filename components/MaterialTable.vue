<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return [
        {
          brand: "",
          model: "",
          sku: "",
          quantity: "",
          description: "",
          observations: "",
        },
      ];
    },
  },
});

const materials = ref(props.modelValue);

const emitter = defineEmits(["update:modelValue"]);

// watch(
//   props.modelValue,
//   (newData, oldData) => {
//     materials.value = props.modelValue;
//   },
//   { deep: true }
// );

watch(
  materials,
  (newData, oldData) => {
    emitter("update:modelValue", materials);
  },
  { deep: true }
);
</script>
<template>
  <!-- Desktop Table -->
  <table class="w-full border-collapse border border-gray-300 bg-white shadow-md hidden md:table">
    <thead>
      <tr class="bg-gray-200">
        <th class="border border-gray-300 p-3 text-left">Brand</th>
        <th class="border border-gray-300 p-3 text-left">Model</th>
        <th class="border border-gray-300 p-3 text-left">SKU</th>
        <th class="border border-gray-300 p-3 text-left">Quantity</th>
        <th class="border border-gray-300 p-3 text-left">Description</th>
        <th class="border border-gray-300 p-3 text-left">Observations</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(material, index) in materials" :key="`material_row_${index}`">
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.brand"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.model"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.sku"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="number"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.quantity"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.description"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="material.observations"
          />
        </td>
      </tr>
    </tbody>
  </table>
</template>
