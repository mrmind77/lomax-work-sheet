<script setup></script>
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
      <tr>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="number"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
        <td class="border border-gray-300 p-2">
          <input
            type="text"
            class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </td>
      </tr>
    </tbody>
  </table>
</template>
