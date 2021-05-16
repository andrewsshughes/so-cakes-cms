<template>
  <div class="container page">
    <h1>{{ contents.title }}</h1>
    <p>{{ contents.content }}</p>
    <div class="prices">
      <h2>Menu</h2>
      <div v-for="(price, index) in contents.prices" :key="index">
        <span>{{ price.name }}</span>
        <span>£{{ price.price }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const pricing = await $content('about').fetch()

    return {
      contents: pricing[0],
    }
  },
}
</script>

<style scoped>
</style>