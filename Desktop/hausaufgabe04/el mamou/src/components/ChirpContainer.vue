<template>
  <b-container>
    <!-- TODO -->
    <b-row>
        <chirp-card   v-for="user in chirps" :key="user.id" :name="user.author" :text="user.text" :img="user.thumbnail" :ht="user.hashtags"></chirp-card>
    </b-row>
  
  </b-container>
</template>

<script>
import ChirpCard from '@/components/ChirpCard.vue'

export default {
  name: "ChirpContainer",
  //TODO
  props:['chirps'],
  components:{
    "chirp-card": ChirpCard
  },
  
};
</script>

<style scoped>

</style>