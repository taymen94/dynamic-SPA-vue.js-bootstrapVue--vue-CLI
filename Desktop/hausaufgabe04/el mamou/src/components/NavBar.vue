<template>
    <b-navbar type="dark" style="background-color: cornflowerblue;">
    <b-navbar-brand href="#" @click="filterCategory('')">Chirper</b-navbar-brand>
      <b-navbar-nav>
        <b-nav-item href="#" @click="cickedNavItem('')" :active= "activeCategory === '' "  >Alle</b-nav-item>
        <b-nav-item href="#" @click="cickedNavItem('featured')" :active="activeCategory === 'featured' ">Featured</b-nav-item>
        <b-nav-item href="#" @click="cickedNavItem('friends')" :active="activeCategory === 'friends' ">Freunde</b-nav-item>
      </b-navbar-nav>

      <b-navbar-nav class="ml-auto">
        <b-form-input size="sm" class="mr-4" placeholder="#hashtag suchen" v-model="hashtag" @keydown.enter="filterHashtag"></b-form-input>
        <!-- TODO -->
        <create-chirpmodal @added-chirp="add" ></create-chirpmodal>
      </b-navbar-nav>
  </b-navbar>
</template>

<script>
import CreateChirpModal from '@/components/CreateChirpModal.vue';
export default {
    name: "NavBar",
    components:{
      "create-chirpmodal": CreateChirpModal
    },
    data() {
      return {
        activeCategory: '',
        hashtag: ''
      }
    },
    methods: {
      // TODO
      cickedNavItem(item){
        this.activeCategory=item
        this.$emit('filter-chirps', this.activeCategory)
      },
      filterHashtag(){
        if (this.hashtag.startsWith("#")) {
          this.$emit('filter-chirps', this.hashtag)
        } else {
          var str="#"+ this.hashtag;
          this.$emit('filter-chirps', str)
        }
      this.hashtag=''
      },
      add(newChirp){
        this.$emit('added-chirp',newChirp)
      }  
    }
};
</script>

<style scoped>
  
</style>