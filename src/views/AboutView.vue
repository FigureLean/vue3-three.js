<script setup lang="ts">
import { useRouter } from 'vue-router';

const router = useRouter();

function goNews() {
  router.push("/three");
}
</script>

<template>
   <div class="about">
      <button @click="goNews">跳转</button>
    </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
