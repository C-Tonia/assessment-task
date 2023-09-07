<script setup>
import From from "./From.vue";
</script>
<template>
  <div
    class="lg:flex lg:items-center lg:justify-center font-inter bg-[#f9f9f9]"
  >
    <div class="register lg:w-1/2">
      <div class="w-10/12 mx-auto max-[900px]:py-10">
        <h1 class="font-semibold text-4xl leading-none">Register with us</h1>
        <p class="font-light mb-6 leading-none tracking-tight">
          Swap your old laptop for a new one
        </p>
        <From />
      </div>
    </div>
    <div class="image w-1/2 min-h-screen hidden lg:block">
      <img class="h-full w-full" src="../assets/img/task-bg.png" alt="" />
    </div>
  </div>
</template>
<style></style>
