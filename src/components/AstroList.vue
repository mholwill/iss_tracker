<template lang="html">
  <li @click='handleClick'>{{astro.name}}</li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'list-item',
  props: ['astro'],
  methods: {
    handleClick(){
      eventBus.$emit("astro-selected", this.astro);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
