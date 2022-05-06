<template>
      <div class="container">
      <b-row>
        <b-col cols="9">
          <Card v-for="data in cardData" :key="data.id" :img="data.img" :Sbutton="data.showButton" class="my-5"></Card>
        </b-col>
        <b-col cols="3" style="background:black;">
          <ControlCard @addCard="addCard"></ControlCard>
        </b-col>
        </b-row>
      </div>
    
</template>

<script>
import Card from "./components/Card.vue";
import ControlCard from "./components/ControlCard.vue";
export default {
  components:{
    Card , ControlCard
  },
  data(){
    return{
      cardData: [{
      img:require('./assets/img1.png') ,
      showButton: true  ,
      id: 0 } ,{
      img:require('./assets/img1.png') ,
      showButton: false  ,
      id: 1  }] ,
      idCount: 3
    } 
  },
  methods: {
    addCard() {
      const newCard = {
        id: this.idCount ,
        img: require('./assets/img1.png') ,
        showButton: false  
      }
      this.cardData.push(newCard)
      this.idCount++; 
    } 

  }

}
</script>

<style>

</style>