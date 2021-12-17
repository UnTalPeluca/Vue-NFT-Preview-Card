<template>
  <NFTCard 
    :img="card.img" 
    :name="card.name"
    :id="card.id"
    :description="card.description"
    :price="card.price"
    :time="card.time"
    :autor="card.autor"
    :avatar="card.avatar"
  />
</template>

<script>
import NFTCard from './components/NFTCard/NFTCard.vue'

export default {
  name: 'App',
  components: {
    NFTCard
  },
  data: () => ({
    card: {
      img: 'image-equilibrium.jpg',
      name: 'Equilibrium',
      description: 'Our Equilibrium collection promotes balance and calm.',
      id: 3429,
      price: 0.041,
      time: 3,
      autor: 'Jules Wyvern',
      avatar: 'image-avatar.png',
    }
  })
}
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600&display=swap');

* {
  margin: 0;
  box-sizing: border-box;
}
html {
  font-size: 62.5%;
}
img {
  width: 100%;
  vertical-align: middle;
}
body {
  background-color: #0D192C;
  font-family: 'Outfit', sans-serif;
}
#app {
  display: flex;
  justify-content: center;
  margin-top: 62px;
  @media screen and (min-width: 768px) {
      margin-top: 152px;
  }
}
</style>
