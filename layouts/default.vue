<script setup>
import LomaxLogo from "~/assets/logo-lomax-10aniv.png";
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <!-- Top Bar -->
    <header class="bg-white border-b border-gray-200 py-4">
      <div class="container mx-auto flex justify-center">
        <img :src="LomaxLogo" alt="LOMAX Technologies S.A." class="h-12 w-auto" />
      </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow container mx-auto py-8 w-full md:w-4/5">
      <NuxtPage />
    </main>

    <!-- Footer -->
    <footer class="bg-gray-100 border-t border-gray-200 py-6">
      <div class="container mx-auto text-center text-sm text-gray-600">
        <p>Centro de Negocios Spazio Zona 15 Oficina 1502B, Ciudad de Guatemala</p>
        <p>Phone: +502 2429-6353 | Email: info@lomax.com.gt</p>
      </div>
    </footer>
  </div>
</template>
