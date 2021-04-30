<template>
  <div>
    <b-button v-b-modal.modal-1 size="sm" variant="outline-light">Chirpen!</b-button>
    <b-modal id="modal-1" title="Neuen Chirp erstellen" @ok="addChirp">

      <!-- TODO -->
    <label for="input-live">Dein Name *</label>
    <b-form-input
      id="input-live"
      v-model="newChirp.author"
      aria-describedby="input-live-help input-live-feedback"
      placeholder=""
    ></b-form-input>

    <br>

    <b-form-group
      label="Deine Nachricht *"
      label-for="textarea-formatter"
      :description="restString"
      class="mb-0"
    >
      <b-form-textarea
        id="textarea-formatter"
        v-model="newChirp.text"
        placeholder="max. 200 Zeichen"
        :formatter="langtest"
        rows="3"
        max-rows="6"
      >
      </b-form-textarea>
    </b-form-group>
    <br>

    <b-form-group
      label="Hashtags:"
      label-for="textarea-formatter"
      description="Hashtags durch Leerzeichen getrennt angeben"
      class="mb-0"
    >
      <b-form-input
        id="input-live"
        v-model="hashtagString"
        :state="nameState"
        aria-describedby="input-live-help input-live-feedback"
        placeholder="z.B. #hashtag1 #hashtag2"
      >
      </b-form-input>
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
    langtest(e){
     return String(e).substring(0,200);
    },
  },
  computed:{
    restString:function(){
      return "noch "+ (200-this.newChirp.text.length ).toString() + " Zeichen übrig"
    }
  }
};
</script>   

<style scoped>
</style>