<template>
  <JokerCard
    joke-card-title="Joke application!" 
    :joke-card-text="joke.content" 
    :is-loading="joke.isLoading"
    @want-render-joke="renderJoke"
  />
</template>

<script setup lang="ts"> 
  import JokerCard from './components/JokeCard.vue'
  import  {api, baseURL} from './services/api' 
  import {ref, reactive} from 'vue'

  const joke = reactive({
    content: 'Please render you first joke.',
    isLoading: false
  })

  async function renderJoke() {
    try {
      joke.isLoading = true;  
      const getJoke = await api.get(`${baseURL}/joke/Programming?type=single`); 
      joke.content = getJoke.data.joke;   
    } catch(error) {
      console.warn(`Oups - ${error}`);  
    }
    joke.isLoading = false;
  }
</script>


 