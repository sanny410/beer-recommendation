<template>
  <div class="profile col">
    <h2 class="app_title">Профиль пользователя</h2>
    <div class="profile_avatar">
      <img class="fadeIn" v-show="isLoaded" @load="onImgLoad" v-bind:src="userInfo.avatar">
      <img class="avatar_not_loaded fadeIn" v-if="!isLoaded" src="../assets/avatar.png">
    </div>
    <div><span class="title">Имя: </span> {{userInfo.first_name}}</div>
    <div><span class="title">Возраст:</span> {{userAge}}</div>
    <div><span class="title">Должность:</span> {{userInfo.employment.title}}</div>
  </div>
</template>

<script>

import axios from 'axios';
import BeerInfo from "@/components/BearInfo";

export default {
  name: 'ProfileUser',
  components: {BeerInfo},
  data: () => ({
    isLoaded: false,
    userInfo: {},
  }),
  methods: {
    onImgLoad() {
      return this.isLoaded = true
    }
  },
  created() {
    axios.get('https://random-data-api.com/api/users/random_user')
        .then(res => this.userInfo = res.data)
  },
  computed: {
    userAge() {
      return new Date().getFullYear() - this.userInfo.date_of_birth.slice(0, 4)
    }
  }
}

</script>

<style scoped>

.profile {
  justify-content: flex-start;
  align-items: center;
}


.avatar_not_loaded {
  max-width: 300px;
  max-height: 300px;
}

.fadeIn {
  -webkit-animation-name: fadeIn;
  animation-name: fadeIn;
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
  -webkit-animation-fill-mode: both;
  animation-fill-mode: both;
}
@-webkit-keyframes fadeIn {
  0% {opacity: 0;}
  100% {opacity: 1;}
}
@keyframes fadeIn {
  0% {opacity: 0;}
  100% {opacity: 1;}
}

</style>