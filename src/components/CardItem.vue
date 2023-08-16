<script setup>
  const { image, name, occupation } = defineProps([
    'image',
    'name',
    'occupation',
  ]);
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
    <p>{{ occupation }}</p>
  </NCard>
</template>

<style scoped>
  .n-card {
    width: 200px;
    margin: 10px 20px;
  }

  p {
    font-size: 10px;
  }

  .jobs {
    display: flex;
    flex-wrap: wrap;
  }
</style>
