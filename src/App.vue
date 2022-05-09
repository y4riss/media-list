<template>
      <div class="container" ref="container" >
      <b-row >
        <b-col cols="9"  class="d-flex justify-content-center flex-column align-items-center">
            <div ref="widthSelector" >
              <Card v-for="data in filteredCards" @focus="handleFocus(data.id)" :key="data.id"  :img="data.img" :Sbutton="data.showButton" :imgLeft="data.imageOrder" :showDeleteBtn="data.showDeleteBtn"  class="my-3 justify-content-center"
              :bgcolor="data.color" >
                      <b-icon ref="icon" v-if="data.showDeleteBtn" icon="trash" aria-hidden="true" @click="data.isSet = false" ></b-icon>
              </Card>
            </div>
        </b-col>
        <b-col cols="3 "  style="width: fit-content;" >
          <ControlCards @addCard="addCard" @changeCardWidth="changeCardWidth" @changeBackground="changeBackground"></ControlCards>
          <ControlCard v-if="focusOn != null" @changeCardOrder="changeCardOrder" @changeCardBackground="changeCardBackground"  ></ControlCard>
        </b-col>
      </b-row>
        

      </div>
    
</template>

<script>
import Card from "./components/Card.vue";
import ControlCards from "./components/ControlCards.vue";
import ControlCard from "./components/ControlCard.vue";
export default {
  components:{
    Card , ControlCards,ControlCard
  },
  data(){
    return{
      body : null,
      focusOn: null ,
      cardData: [{
      isSet : true,
      img:require('./assets/img1.png') ,
      showButton: true  ,
      showDeleteBtn : false,
      id: 0 ,
      imageOrder: 0,
      color : 'white',} ,
      {
      img:require('./assets/img1.png') ,
      isSet : true,
      showButton: false  ,
      showDeleteBtn : false,
      imageOrder: 0,
      id: 1 ,
      color : 'white',
      }
      ] ,
      idCount: 3
    } 
  },
  methods: {
    addCard() {
      const newCard = {
        id: this.idCount ,
        img: require('./assets/img1.png') ,
        showButton: false  ,
        isSet : true,
        showDeleteBtn : false,
        imageOrder: 0,
        color : white,
      }
      this.cardData.push(newCard)
      this.idCount++; 
    } ,
    changeBackground(color){
      if(color === 'white') {
        this.body.style.background = "white"

      }
      else if(color === 'light gray') {
    this.body.style.background = "gray"
      }
      else {
    this.body.style.background = "#2f2f2f"
      }
    },
    changeCardBackground(color){

            this.cardData.map( (card)=>{
            if(card.id == this.focusOn) {
              if(color === 'white'){
                  card.color = 'white'
              }
              else if(color === 'light gray'){
                  card.color = 'light gray'
              }
              else {
                  card.color = 'dark gray'
              }
            }
          })
    },

    changeCardWidth(width){
      if(width === 'small'){
        this.$refs.widthSelector.classList.add("w-50");
        this.$refs.widthSelector.classList.remove("w-75");
        this.$refs.widthSelector.classList.remove("w-100");
      }
      if(width === 'medium'){
        this.$refs.widthSelector.classList.add("w-75");
        this.$refs.widthSelector.classList.remove("w-50");
        this.$refs.widthSelector.classList.remove("w-100");
      }
      if(width === 'big'){
        this.$refs.widthSelector.classList.add("w-100");
        this.$refs.widthSelector.classList.remove("w-50");
        this.$refs.widthSelector.classList.remove("w-75");
      }
      },
      handleFocus(id){
        this.handleDeleteBtn(id) ;
        this.focusOn = id ;
      },
      handleDeleteBtn(id){
          this.cardData.map( (card)=>{
            if(card.id == id) card.showDeleteBtn = true
            else card.showDeleteBtn = false
          })
      },
      changeCardOrder(a){
        let order = 0 ;
        if(a === 'right')
          order = 1 ;
        {
         this.cardData.map( (card)=>{
            if(card.id == this.focusOn) card.imageOrder = order
          }) 
        }
      }
    },

   computed : {
    filteredCards(){
    return this.cardData.filter(card => card.isSet)
    }
  },
  mounted(){
    this.body = document.body
  }

}

</script>

<style>
.col-3{
    position: fixed;
    right: 0;
    height: 100vh;
    background : #3e3e46;
}

</style>