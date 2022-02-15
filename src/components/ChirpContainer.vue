<template>
  <b-container class="containerStyle">
    <b-row class="styleRow" style="flex-grow: initial">
        <chirp-card :key="chirps" v-for="chirps in chirps"  :chirps="chirps" class="col-md-6 col-lg-4 col-12" style="padding-left: 15px, padding-right:15px">
        </chirp-card>
    </b-row>
 </b-container>
</template>

<script>
import ChirpCard from './ChirpCard.vue'
export default {
  //TODO
  name: "ChirpContainer",
  components:{
    ChirpCard
  },
  props:{
    chirps:Array,
  
  }
  
};
</script>

<style scoped>
.containerStyle{
  padding-left: 15px;
  padding-right: 15px;
}
.styleRow{
  margin-left:-15px;
  margin-right:-15px;
}
</style>