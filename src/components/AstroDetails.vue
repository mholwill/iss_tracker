
<template lang="html">
<div v-if='astro'>
  <!-- <h3>{{astro.name}}</h3> -->
</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'astro-detail',
  props: ['astro'],
}
</script>

<style lang="css" scoped>

img {
  height: 200px
}
</style>
