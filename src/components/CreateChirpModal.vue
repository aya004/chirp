<template>
  <div>
  <!-- TODO -->
    <b-button v-b-modal.modal-1 size="sm" variant="outline-light">Chirpen!</b-button>
    <b-modal id="modal-1" title="Neuen Chirp erstellen" @ok="addChirp">
    <b-form-group id="author" label="Dein Name *" >
      <b-form-input v-model="newChirp.author" trim></b-form-input>
    </b-form-group>
    <b-form-group id="text" label="Deine Nachricht *" :description=" 'Noch ' + chCount + ' Zeichen übrig'">
      <b-form-textarea v-model="newChirp.text" placeholder="max. 200 Zeichen" rows ="3" max-rows="6"></b-form-textarea>
    </b-form-group>
    <b-form-group id="hashtag" label="Hashtags:" description="Hashtags durch Leerzeichen getrennt angeben">
      <b-form-input v-model="hashtagString" placeholder="z.B. #hashtag1 #hashtag2"></b-form-input>
    </b-form-group>
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "CreateChirpModal",
  data() {
    return {
      hashtagString: "",
      newChirp: {
        author: "",
        text: "",
        hashtags: [],
      },
    };
  },
  methods: {
    addChirp(bvModalEvt) {
      if (this.newChirp.author && this.newChirp.text) {
        this.newChirp.hashtags = this.hashtagString
          .split(" ")
          .map((h) => "#" + h.replace("#", ""));
        this.$emit("added-chirp", this.newChirp);
        return;
      } else {
        bvModalEvt.preventDefault();
        return;
      }
    },
  },
  computed:{
    chCount(){
      return  200 - this.newChirp.text.length ;
    }
  }
};
</script>

<style scoped>
</style>