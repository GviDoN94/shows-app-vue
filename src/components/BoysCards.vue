<script setup>
  import axios from 'axios';
  import CardItem from '@/components/CardItem.vue';
  import { ref } from 'vue';

  const API_URL = 'https://www.theboysapi.com/api/character';

  const characters = ref(null);
  const nextPageUrl = ref(null);
  const prevPageUrl = ref(null);

  const fetchData = async (url) => {
    try {
      const response = await axios.get(url);
      characters.value = response.data.results;
      nextPageUrl.value = response.data.next;
      prevPageUrl.value = response.data.prev;
      console.log(response);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  };

  const getNextOrPrevPage = async (url) => {
    if (url) {
      fetchData(url);
    }
  };

  fetchData(API_URL);
</script>

<template>
  <div class="container">
    <div
      v-if="characters"
      class="cards"
    >
      <CardItem
        v-for="character in characters"
        :key="character.id"
        :image="character.image"
        :name="character.name"
      >
        <p>{{ character.real_name }}</p>
      </CardItem>
    </div>
    <div
      v-else
      class="cards spinner"
    >
      <NSpin size="large" />
    </div>
    <div class="button-container">
      <button
        v-show="prevPageUrl"
        @click="getNextOrPrevPage(prevPageUrl)"
      >
        &lt;
      </button>
      <button
        v-show="nextPageUrl"
        @click="getNextOrPrevPage(nextPageUrl)"
      >
        >
      </button>
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
    min-height: 700px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
  }
  .cards h3 {
    font-weight: bold;
  }
  .cards p {
    font-size: 10px;
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
