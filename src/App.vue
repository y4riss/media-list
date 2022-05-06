<template>
      <div class="container" ref="container" >
      <b-row>
        <b-col cols="9">
          <Card v-for="data in cardData" :key="data.id" :img="data.img" :Sbutton="data.showButton" class="my-5 " ></Card>
        </b-col>
        <b-col cols="3" style="background:black;">
          <ControlCard @addCard="addCard" @changeBackground="changeBackground"></ControlCard>
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
    } ,
    changeBackground(color){
      if(color === 'white') {
        this.$refs.container.classList.add("bg-white");
        this.$refs.container.classList.remove(
          "bg-light","bg-secondary");

      }
      else if(color === 'light gray') {
        this.$refs.container.classList.remove("bg-white");
        this.$refs.container.classList.add("bg-light");
        this.$refs.container.classList.remove("bg-secondary");
      }
      else {
        this.$refs.container.classList.remove("bg-white");
        this.$refs.container.classList.remove("bg-light");
        this.$refs.container.classList.add("bg-secondary");
      }
    }

  }

}
</script>

<style>

</style>