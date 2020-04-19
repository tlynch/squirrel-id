<template>
  <div>
    <img @click="rotateImg" :src="'./images/' + squirrel.images[currentImg].src" :alt="imgDesc">
    <div>{{ squirrel.name }}</div>
  </div>
</template>

<script>
export default {
  name: 'SquirrelComponent',
  props: {
    squirrel: Object
  },
  data: function () {
    return {
      currentImg: 0
    }
  },
  computed: {
    imgDesc: function () {
      return this.squirrel.images[this.currentImg].tags.join(', ')
    }
  },
  methods: {
    rotateImg: function () {
      this.currentImg = (this.currentImg + 1) % this.squirrel.images.length;
    }
  }
}
</script>

<style scoped>
  img {
    width: 100%;
  }
</style>