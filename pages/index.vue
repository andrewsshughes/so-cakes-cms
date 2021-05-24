<template>
  <div class="container page">
    <h1>Our Past Work</h1>
    <div class="image-filter">
      <span :class="{ selected: filterIsSelected('gaming') }" @click.stop.prevent="toggleFilter('gaming')">Gaming</span>
      <span :class="{ selected: filterIsSelected('baby') }" @click.stop.prevent="toggleFilter('baby')">Baby</span>
      <span
        :class="{ selected: filterIsSelected('pretty and pink') }"
        @click.stop.prevent="toggleFilter('pretty and pink')"
        >Pretty and Pink</span
      >
      <span
        :class="{ selected: filterIsSelected('themed drip cakes') }"
        @click.stop.prevent="toggleFilter('themed drip cakes')"
        >Themed Drip Cakes</span
      >
      <span :class="{ selected: filterIsSelected('children') }" @click.stop.prevent="toggleFilter('children')"
        >Children</span
      >
    </div>
    <div class="image-gallery">
      <div
        v-for="(cake, index) in shownCakes"
        :key="index"
        @click.stop.prevent="setActiveCake(index)"
        :class="{ active: index == active }"
      >
        <img :src="cake.image" />
        <div class="details">
          <p>{{ cake.description }}</p>
          <!--<div class="order-like">Order a cake like this</div>-->
        </div>
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
      active: null,
    }
  },
  methods: {
    toggleFilter(cat) {
      let ind = this.filter.indexOf(cat)
      if (ind > -1) {
        this.filter.splice(ind, 1)
      } else {
        this.filter.push(cat)
      }
      if (this.filter.length == 4) {
        this.filter = []
      }
    },
    filterIsSelected(filter) {
      return this.filter.indexOf(filter) > -1 || this.filter.length == 0
    },
    setActiveCake(index) {
      this.active = this.active == index ? null : index
    },
  },
  computed: {
    shownCakes() {
      if (this.filter.length == 0) {
        return this.cakes
      } else {
        return this.cakes.filter((c) => {
          let found = false
          c.category.forEach((cat) => {
            if (this.filter.indexOf(cat) > -1) {
              found = true
            }
          })
          return found
        })
      }
    },
  },
}
</script>

<style scoped>
.image-filter {
  font-size: 18px;
  margin-top: 12px;
  margin-bottom: 24px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.image-filter > span {
  margin-right: 30px;
  cursor: pointer;
  margin-top: 12px;
}
.selected {
  color: #ff66c4;
}
.image-gallery {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-gap: 30px;
  width: 100%;
  min-width: 100%;
  grid-auto-flow: dense;
}
@media screen and (max-width: 500px) {
  .image-gallery {
    grid-template-columns: 1fr 1fr;
  }
}
.image-gallery > div {
  aspect-ratio: 1;
  position: relative;
  grid-column: span 1;
  transition: 250ms ease-in-out;
}
.image-gallery > div.active {
  grid-column: span 2;
  grid-row: span 2;
}
.image-gallery > div > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.image-gallery > div > .details {
  position: absolute;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  width: 100%;
  text-align: center;
  padding-bottom: 10px;
  box-sizing: border-box;
  opacity: 0;
  transition: 250ms ease-in-out;
}
.image-gallery > div > .details > p {
  width: 90%;
  margin-left: 5%;
}
.image-gallery > div.active > .details {
  opacity: 1;
}
.order-like {
  background: white;
  color: #ff66c4;
  width: 200px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  border-radius: 5px;
  padding: 5px 2px;
  cursor: pointer;
  user-select: none;
}
</style>