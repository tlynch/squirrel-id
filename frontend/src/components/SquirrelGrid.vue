<template>
    <div>
        <h1 v-text="title"></h1>

        <label>
            Filter:
            <input type="text" v-model="filter"/>
        </label>

        <div id="grid">
            <figure v-for="squirrel in filteredSquirrels" :key="squirrel.id">
                <img :src="'./images/' + squirrel.images[0].src" :alt="''">
            </figure>
        </div>
    </div>
</template>

<script>
import data from '../assets/squirrels.json'

export default {
  name: 'SquirrelGrid',
  data: function () {
    return {
        title: data.title,
        squirrels: data.squirrels,
        filter: ''
    }
  },

  computed: {
    filteredSquirrels: function () {
      if (!this.filter || this.filter.length < 2) {
        return this.squirrels;
      }

      /*return this.squirrels.filter(item => 
        item.color.localeCompare(this.filter, 'en', {sensitivity: 'base'}) === 0
            || item.name.localeCompare(this.filter, 'en', {sensitivity: 'base'}) === 0
      )*/
      return this.squirrels.filter(item => 
        item.color.startsWith(this.filter) || item.name.startsWith(this.filter))
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

  img {
    width: 150px;
    height: 150px;
   } 
</style>
