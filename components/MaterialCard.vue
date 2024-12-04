<script setup>
const props = defineProps({
  modelValue: {
    default() {
      return {
        id: "",
        brand: "",
        model: "",
        sku: "",
        quantity: "",
        description: "",
        observations: "",
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
      <div class="grid grid-cols-2 gap-4">
        <div>
          <label class="block text-sm font-medium text-gray-700">Brand</label>
          <input
            type="text"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.brand"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700">Model</label>
          <input
            type="text"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.model"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700">SKU</label>
          <input
            type="text"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.sku"
          />
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700">Quantity</label>
          <input
            type="number"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.quantity"
          />
        </div>
        <div class="col-span-2">
          <label class="block text-sm font-medium text-gray-700">Description</label>
          <input
            type="text"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.description"
          />
        </div>
        <div class="col-span-2">
          <label class="block text-sm font-medium text-gray-700">Observations</label>
          <input
            type="text"
            class="mt-1 block w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="modelValue.observations"
          />
        </div>
      </div>
    </div>
  </div>
</template>
