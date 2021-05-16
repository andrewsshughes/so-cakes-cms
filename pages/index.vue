<template>
  <div class="container page">
    <h1>Our Past Work</h1>
    <div class="image-filter">
      <span>Birthday</span>
      <span>Wedding</span>
      <span>New Born</span>
      <span>Miscellaneous</span>
    </div>
    <div class="image-gallery">
      <div v-for="(cake, index) in shownCakes" :key="index">
        <img :src="cake.image" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const cakes = await $content('cakes').fetch()

    return {
      cakes,
      filter: [],
    }
  },
  computed: {
    shownCakes() {
      if (this.filter.length == 0) {
        return this.cakes
      }
    },
  },
}
</script>

<style scoped>
.image-filter {
  font-size: 18px;
  margin-top: 24px;
  margin-bottom: 24px;
  display: flex;
  flex-direction: row;
}
.image-filter > span {
  margin-right: 30px;
  cursor: pointer;
}
.image-gallery {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-gap: 30px;
  width: 100%;
  min-width: 100%;
}
.image-gallery > div {
  aspect-ratio: 1;
}
.image-gallery > div > img {
  width: 100%;
  height: 100%;
}
</style>