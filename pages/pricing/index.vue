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
    const pricing = await $content('pricing').fetch()

    return {
      contents: pricing[0],
    }
  },
}
</script>

<style scoped>
.prices {
  background: #ffddf2;
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 41px;
}
.prices h2 {
  font-size: 32px;
  margin: 10px 0;
  padding: 0;
  margin-left: 20px;
}
.prices > div {
  min-height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 0px 20px;
  align-items: center;
  width: 100%;
  box-sizing: border-box;
  font-size: 24px;
  flex-wrap: wrap;
}
.prices > div:nth-child(2n) {
  background: rgba(255, 255, 255, 0.33);
}
</style>