<template>
  <profile-user></profile-user>
  <beer-info />
</template>

<script>
import ProfileUser from "@/components/ProfileUser";
import BeerInfo from "@/components/BearInfo";
import '../App.css'

export default {
  name: "App",
  components: {BeerInfo, ProfileUser}
}
</script>

<style scoped>

</style>
