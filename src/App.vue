<script setup>
  import BoysCards from '@/components/BoysCards.vue';
  import RickMortyCards from '@/components/RickMortyCards.vue';
  import HeroTitle from './components/HeroTitle.vue';
  import { ref } from 'vue';

  const isBoys = ref(true);
</script>

<template>
  <main>
    <HeroTitle
      @selectShow="isBoys = !isBoys"
      :isBoys="isBoys"
    />
    <BoysCards v-if="isBoys" />
    <RickMortyCards v-else />
  </main>
</template>
