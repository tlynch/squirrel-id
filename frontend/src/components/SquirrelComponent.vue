<template>
  <div>
    <img v-bind:class="{ flipped: isFlipped }" @click="rotateImg" :src="'./images/' + squirrel.images[currentImg].src" :alt="imgDesc">
    <div>{{ squirrel.name }}</div>

    <button @click="isFlipped=!isFlipped">Flip</button>
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
      currentImg: 0,
      isFlipped: false
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

  .flipped {
    transform: scaleX(-1);
  }
</style>
