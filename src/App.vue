<template>
      <div class="container" ref="container" >
      <b-row >
        <b-col cols="9"  class="d-flex justify-content-center flex-column align-items-center">
            <div ref="widthSelector" >
              <Card v-for="data in filteredCards" @focus="handleFocus(data.id)" :key="data.id"  :img="data.img" :Sbutton="data.showButton" :imgLeft="data.imageOrder" :showDeleteBtn="data.showDeleteBtn"  class="my-3 justify-content-center"
              :bgcolor="data.color" @modifyText="handleText">
                      <b-icon ref="icon" style="cursor:pointer;" v-if="data.showDeleteBtn" icon="trash" aria-hidden="true" @click="data.isSet = false" ></b-icon>
              </Card>
            </div>
        </b-col>
        <b-col cols="3 "   >
          <ControlCards @addCard="addCard" @changeCardWidth="changeCardWidth" @changeBackground="changeBackground" @handleMouseLeave="handleMouseLeave"></ControlCards>
          <ControlCard v-if="focusOn != null" @changeCardOrder="changeCardOrder" @changeCardBackground="changeCardBackground"  @handleCardButton="handleCardButton" @uploadImg="uploadImg"></ControlCard>
          <ControlText v-if="showControlText" @changeText="changeText" @changeWeight="changeWeight" @changetextColor="changetextColor"></ControlText>
        </b-col>
      </b-row>
      </div>
</template>

<script>

import Card from "./components/Card.vue";
import ControlCards from "./components/ControlCards.vue";
import ControlCard from "./components/ControlCard.vue";
import ControlText from "./components/ControlText.vue";

export default {
  components:{
    Card,
    ControlCards,
    ControlCard,
    ControlText
},
  data(){
    return{
      hover : false,
      previousClass : 'w-100',
      focusOn: null ,
      showControlText: null ,
      selectedText: null ,
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
        color : 'white',
      }
      this.cardData.push(newCard)
      this.idCount++; 
    } ,
    changeBackground(color){
        document.body.style.background = color
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
    changeCardWidth(width,e){
      if(e.type == 'mouseenter'){
          this.hover = true
      if(width === 'small'){

        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add("w-50");
      }
      if(width === 'medium'){
        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add("w-75");

      }
      if(width === 'big'){
        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add("w-100");

      }
      }

      else if (e.type == 'click') {
        this.previousClass = this.$refs.widthSelector.className
        this.hover = false
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
      },
      handleCardButton(action){
          this.cardData.map(card =>{
            if(card.id == this.focusOn) {
              if(action === 'del') card.showButton = false
              else card.showButton = true
            }
          })
      },
      handleText(e){
        this.showControlText = true ;
        this.selectedText = e.target ;
      },
      changeText(cls){
        this.selectedText.className = '';
        if ( cls !== 'n')
          this.selectedText.classList.add(cls);
      },
      changeWeight(cls){
        this.selectedText.classList.toggle(cls)
      },
      handleMouseLeave(e){
          if(this.hover){
              this.$refs.widthSelector.className = '';
              this.$refs.widthSelector.classList.add(this.previousClass)
          }
          this.hover = false
      },
      changetextColor(clr){
        this.selectedText.style.color = clr ;
      },
      uploadImg(e){
        const image = e.target.files[0]
        if(image){
        this.cardData.map(card =>{
          if(card.id === this.focusOn){
           card.img = window.URL.createObjectURL(image)
           return
           }
        })
        }

      }
    },
    mounted(){
        document.body.addEventListener("click",(e)=>{
          if(e.altKey){
            this.handleFocus(null)
            this.showControlText = null
            
          }
        })
    },
   computed : {
    filteredCards(){
    return this.cardData.filter(card => card.isSet)
    }
  },
}

</script>

<style>
.col-3{
    position: fixed;
    max-width : 290px !important;
    right: 0;
    height: 100vh;
    background : #3e3e46;
}

</style>