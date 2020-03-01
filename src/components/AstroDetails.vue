
<template lang="html">
<div v-if='astro'>
  <h3>{{astro.name}}</h3>
  <p>Craft: {{astro.craft}}</p>
</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
name: 'munro-detail',
props: ['astro']
}
</script>

<style lang="css" scoped>
</style>
