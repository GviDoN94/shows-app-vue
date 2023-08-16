<script setup>
  import BoysCards from '@/components/BoysCards.vue';
  import RickMortyCards from '@/components/RickMortyCards.vue';
</script>

<template>
  <main>
    <h1>HERO</h1>
    <Suspense>
      <template #default>
        <BoysCards />
      </template>
      <template #fallback>Loading...</template>
    </Suspense>
    <RickMortyCards />
  </main>
</template>
