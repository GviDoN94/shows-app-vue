<script setup>
  const { image, name } = defineProps(['image', 'name']);
</script>

<template>
  <NCard>
    <template #cover>
      <img
        :src="image"
        :alt="name"
      />
    </template>
    <h3>{{ name }}</h3>
    <slot></slot>
  </NCard>
</template>

<style scoped>
  .n-card {
    width: 200px;
    margin: 10px 20px;
  }
</style>
