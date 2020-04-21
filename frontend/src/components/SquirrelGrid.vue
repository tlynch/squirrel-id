<template>
    <div>
        <h1 v-text="title"></h1>
        <div id="grid">
            <SquirrelComponent v-for="squirrel in squirrels" :key="squirrel.id" :squirrel="squirrel"></SquirrelComponent>
        </div>
    </div>
</template>

<script>
import data from '../assets/squirrels.json'
import SquirrelComponent from './SquirrelComponent'

export default {
  name: 'SquirrelGrid',
  components: {
    SquirrelComponent
  },
  data: function () {
    return {
        title: data.title,
        squirrels: data.squirrels
    }
  }
}
</script>

<style scoped>
  h1 {
    text-align: center;
  }

  #grid {
    display: grid;
    grid-template-columns: 50% 50%;
  }
</style>
