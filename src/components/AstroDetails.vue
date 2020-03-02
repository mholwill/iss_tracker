
<template lang="html">
<div v-if='astro'>
  <!-- <img v-if="astro.name" :src="@/public/images/AndrewMorgan.jpg" alt=""> -->
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
