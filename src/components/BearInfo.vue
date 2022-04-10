<template>
  <div class="beer col">
    <h2 class="app_title">Рекомендованное пиво</h2>
    <div><span class="title">Бренд:</span> {{beerInfo.brand}}</div>
    <div><span class="title">Название:</span> {{beerInfo.name}}</div>
    <div><span class="title">Хмель:</span> {{beerInfo.hop}}</div>
    <div><span class="title">Дрожжи:</span> {{beerInfo.yeast}}</div>
    <div><span class="title">Горечь:</span> {{beerInfo.ibu}}</div>
    <div><span class="title">Солод:</span> {{beerInfo.malts}}</div>
    <div><span class="title">Крепость:</span> {{beerInfo.alcohol}}</div>
    <button class="btn change_beer" @click="changeBeer">Изменить пиво</button>
  </div>
</template>

<script>


import axios from "axios";

export default {
  name: "BeerInfo",
  data: () => {
    return {
      beerInfo: {}
    }
  },
  methods: {
    changeBeer() {
      axios.get('https://random-data-api.com/api/beer/random_beer')
          .then(res => this.beerInfo = res.data)
    }
  },
  created() {
    axios.get('https://random-data-api.com/api/beer/random_beer')
        .then(res => this.beerInfo = res.data)
  }
}
</script>

<style scoped>

.app_title {
  font-size: 1.7rem;
  text-align: center;
}

.btn {
  background: #22C55E;
  box-shadow: 0 1px 2px rgba(105, 81, 255, 0.05);
  border-radius: 6px;
  border: none;
  color: white;
  width: 80%;
  padding: 10px;
  font-family: 'Grape Nuts', cursive;
  font-size: 16px;
  margin-top: 20px;
  align-self: center;
}
</style>