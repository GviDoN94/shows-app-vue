<script setup>
  import axios from 'axios';
  import CardItem from './CardItem.vue';
  import { ref } from 'vue';

  const characters = ref(null);

  const response = await axios.get('https://www.theboysapi.com/api/character');

  characters.value = response.data.results;
</script>

<template>
  <div class="container">
    <div class="cards">
      <CardItem
        v-for="character in characters"
        :key="character.id"
        :image="character.image"
        :name="character.name"
      />
    </div>
  </div>
</template>

<style scoped>
  .container {
    background-color: rgb(27, 26, 26);
    padding: 30px;
  }
  .cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 700px;
  }
  .cards h3 {
    font-weight: bold;
  }
  .cards p {
    font-size: 10px;
  }
  .jobs {
    display: flex;
    flex-wrap: wrap;
  }
  .button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px;
  }
  .button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
  }
  .spinner {
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
