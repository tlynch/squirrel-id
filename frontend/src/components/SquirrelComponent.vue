<template>
  <div>
    <img :class="{ flipped: squirrel.images[currentImg].flipped }" @click="rotateImg" :src="'./images/' + squirrel.images[currentImg].src" :alt="imgDesc">
    <div>
        {{ imgDesc }}
        <span v-if="squirrel.images[currentImg].flipped">
            (flipped)
        </span>
    </div>
   <div>{{ squirrel.name }}</div>

    <button @click="flipImg">Flip</button>
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
    },
    flipImg: function () {
      this.squirrel.images[this.currentImg].flipped = !this.squirrel.images[this.currentImg].flipped;
    }
  },

  created() {
    this.squirrel.images.map(item => this.$set(item, 'flipped', false))
  }
}
</script>

<style scoped>
  img {
    width: 100%;
  }

  img.flipped {
    transform: scaleX(-1);
  }
</style>
