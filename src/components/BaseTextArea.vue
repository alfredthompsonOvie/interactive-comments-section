<template>
  <form>
    <label for="c"></label>
    <textarea 
    name="comment" 
    id="comment" 
    cols="30" 
    rows="5"
    v-model="username">
  </textarea>
  <!-- {{ username }} -->
    <button type="submit">Reply</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

// v-model
const username = ref('@amyrobson')
</script>

<style scoped>

</style>