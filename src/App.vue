<template>
      <div class="container">
      <b-row>
        <b-col cols="9">
          <Card :img="img"/>
          <Card :img="img"/>
          <Card :img="img"/>
        </b-col>
        <b-col style="background:black;">

        </b-col>
        </b-row>
      </div>
    
</template>

<script>
import Card from "./components/Card.vue";
export default {
  components:{
    Card
  },
  data(){
    return{
      img:require('./assets/img1.png')
    }
  }

}
</script>

<style>

</style>