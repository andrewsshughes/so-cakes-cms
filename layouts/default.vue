<template>
  <div class="wrapper">
    <header>
      <div class="container">
        <img src="/img/logo.png" />
        <nav>
          <NuxtLink to="/">Cakes</NuxtLink>
          <NuxtLink to="/pricing">Pricing</NuxtLink>
          <NuxtLink to="/about">About</NuxtLink>
          <NuxtLink to="/contact">Contact</NuxtLink>
        </nav>
      </div>
    </header>
    <div class="header-border"></div>
    <nuxt />
  </div>
</template>

<style scoped>
header {
  height: 300px;
  background-color: #ff66c4;
}
header nav {
  display: flex;
  flex-direction: row;
  width: 400px;
  justify-content: space-between;
}
header nav > * {
  color: white;
  text-decoration: none;
  font-size: 18px;
}
header img {
  width: 120px;
  height: 120px;
  margin-bottom: 30px;
}
.header-border {
  background-image: url('/img/border-bottom.png');
  background-size: 36px;
  padding-top: 50px;
  width: 100%;
}
</style>