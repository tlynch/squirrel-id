<template>
  <div id="grid">
    <SquirrelComponent v-for="squirrel in squirrels" :key="squirrel.id" :squirrel="squirrel"></SquirrelComponent>
  </div>
</template>

<script>
import squirrels from '../assets/squirrels.json'
import SquirrelComponent from './SquirrelComponent'

export default {
  name: 'SquirrelGrid',
  components: {
    SquirrelComponent
  },
  data: function () {
    return squirrels
  }
}
</script>

<style scoped>
  #grid {
    display: grid;
    grid-template-columns: 50% 50%;
  }
</style>