<template lang="html">
  <div>
    <h1>Current Astronaughts aboard the ISS:</h1>
    <ul>
      <list-item v-for="(astro, index) in astros" :astro="astro" :key="index"></list-item>
    </ul>
  </div>
</template>

<script>
import eventBus from '../main.js'
import AstroList from './AstroList.vue'

export default {
  name: 'astros-in-space',
  props: ['astros'],
  components: {
    'list-item': AstroList
  }
}
</script>


<style lang="css" scoped>

  list-item {
    text-decoration: none;
    list-style-type: none;
    font-size: 70px;
  }

  h1 {
    font-size: 20px;
  }

</style>
