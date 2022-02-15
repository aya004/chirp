<template>
<!--TODO-->
  <div style="margin-top:13px">
  
  <b-card no-body><b-row no-gutters>
      <b-col cols="3"><div class="mt-1 ml-1">
        <b-avatar :src="getImgUrl(chirps.thumbnail)" size="64px" variant="light"></b-avatar>
      </div></b-col>
      <b-col cols="9">
        <b-card-body>
          <b-card-titel style="margin-bottom: 12px"><h4>{{chirps.author}}</h4></b-card-titel>
          <p><b-card-text>{{chirps.text}}
            <span class="hashtag">
            <span class="m-0">
              
                {{chirps.hashtags[0]}}
                {{chirps.hashtags[1]}}
                {{chirps.hashtags[2]}}
                {{chirps.hashtags[3]}}
                {{chirps.hashtags[4]}}
                {{chirps.hashtags[5]}}
                {{chirps.hashtags[6]}}
              
            </span>
          </span></b-card-text></p>
      </b-card-body>
      </b-col>
      </b-row>
  </b-card></div>
</template>

<script>
export default {
  name: "ChirpCard",
  props:{
   chirps:Object,
  },
  methods:{
    // TODO
    getImgUrl(thumbnailPath) {
      return require("../assets/" + thumbnailPath);
    },
    
  },
};
</script>

<style scoped>
.hashtag{
  color: cornflowerblue;
}
</style>