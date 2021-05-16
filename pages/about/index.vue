<template>
  <div class="container page">
    <h1>{{ contents.title }}</h1>
    <p>{{ contents.content }}</p>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const about = await $content('about').fetch()

    return {
      contents: about[0],
    }
  },
}
</script>

<style scoped>
p {
  width: 60%;
}
</style>