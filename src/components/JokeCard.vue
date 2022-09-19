<template>
  <div class="joker-card"> 
    <Loader v-if="isLoading" /> 
    <div>
      <h1>{{jokeCardTitle}}</h1> 
      <p>{{jokeCardText}}</p>
      <a class="btn" href="#" @click.prevent="showJoke">Render joke</a>
    </div> 
  </div>
</template> 

<script setup lang="ts">
    import Loader from './Loader.vue'

    const props = defineProps({
      jokeCardTitle: {
          type: String, 
          required: true,
      },
      jokeCardText: {
        type:String,
        required: true, 
      },
      isLoading: {
        type: Boolean, 
        required: true,
      }
    })

    const emit = defineEmits(['wantRenderJoke'])
    
    function showJoke() {
      emit('wantRenderJoke');  
    }
      
</script>  

<style lang="scss" scoped>  
  $dark_blue: #192A80; 
  .joker-card {
    position: relative;
    min-height: 200px; 
    text-align: center;
    display: block; 
    max-width: 600px;
    margin: 80px auto 0 auto; 
    padding: 40px; 
    box-shadow: 7px 10px 19px -1px rgba(0,0,0,0.27);
    h1 {
      color: $dark_blue; 
      font-size: 26px;
      font-weight: 700; 
      margin: 0 0 32px 0; 
    }
    p {
      line-height: 26px; 
      white-space: pre-line; 
    }
    .btn {
      margin: 32px 0 0 0; 
      border: 2px solid $dark_blue; 
      padding: 12px 25px; 
      display: inline-block; 
      text-transform: uppercase;
      font-weight: 700;
      color: $dark_blue; 
      transition: all .3s;
      &:hover {
        border: 2px solid $dark_blue;
        background: $dark_blue;
        color: white; 
        transition: all .3s;
      }
    }
  }
  
</style>