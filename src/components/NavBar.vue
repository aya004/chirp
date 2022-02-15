<template>
<!-- TODO -->
    <b-navbar type="dark" style="background-color: cornflowerblue;">
    <b-navbar-brand href="#" @click="filterCategory('')">Chirper</b-navbar-brand>
      <b-navbar-nav>
        <b-nav-item href="#" @click="filterCategory('')">Alle</b-nav-item>
        <b-nav-item href="#" @click="filterCategory('featured')">Featured</b-nav-item>
        <b-nav-item href="#" @click="filterCategory('friends')">Freunde</b-nav-item>
      </b-navbar-nav>

      <b-navbar-nav class="ml-auto">
        <b-form-input size="sm" class="mr-4" placeholder="#hashtag suchen" v-model="hashtag" @keydown.enter="filterHashtag"></b-form-input>
        <create-chirp-modal @added-chirp="addedChirp"></create-chirp-modal>
        
      </b-navbar-nav>
  </b-navbar>
</template>

<script>
import CreateChirpModal from './CreateChirpModal.vue';

export default {
  components: {
    CreateChirpModal
  },
    name: "NavBar",
    data() {
      return {
        activeCategory: '',
        hashtag: ''
      }
    },
    methods: {
          // TODO
      filterCategory(category){
        this.activeCategory = category;
        this.$emit("filter-chirps" , category);
          
      },
      filterHashtag(){
        this.$emit("filter-chirps", "#" + this.hashtag.replace("#", ""));
        this.hashtag = "";

      },
      addedChirp(newChirp){
        this.$emit("added-chirp", newChirp);
      },
    }
}

</script>

<style scoped>

</style>