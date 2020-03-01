<template lang="html">
  <div class="list">
    <li @click='handleClick'>{{astro.name}}</li>
  </div>
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

li {
  color: white;
  flex-direction: row;
}

</style>
