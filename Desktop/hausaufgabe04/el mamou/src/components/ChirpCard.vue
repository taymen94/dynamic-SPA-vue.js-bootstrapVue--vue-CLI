<template> 
  <b-col sm="12" md="6" lg="4">
    <b-card class="card" no-body  >
      <b-row  >
        <b-col md="3" >
          <b-avatar :src=getImgUrl(img) size="4rem"></b-avatar>
        </b-col>
        <b-col md="9">
          <b-card-body :title="name">
            <span v-text="text" >
            </span>
            <span v-text=htstr(ht) style="color:cornflowerblue">
            </span>
            
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>
  </b-col>
  
  
</template>

<script>
export default {
  name: "ChirpCard",
  props:["name","text","img","ht"],
  methods: {
    getImgUrl(thumbnailPath) {
      return require("../assets/" + thumbnailPath);
    },
    // TODO
    htstr(ht){
      return " "+ ht.join(" ")
    }
    
  },
};
</script>

<style scoped>
 .card{
  margin:10px 0;
  padding: 5px;
}

</style>