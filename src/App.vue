<template>
      <div class="container" ref="container" >
      <b-row>
        <b-col cols="9"  class="d-flex justify-content-center flex-column align-items-center" id="main">
            <div ref="widthSelector" >
              <Card v-for="data in filteredCards" @focus="handleFocus(data.id)" :key="data.id"  :img="data.img" :Sbutton="data.showButton" :imgLeft="data.imageOrder" :showDeleteBtn="data.showDeleteBtn" :border="data.border" :corner="data.corner"  :shadow="data.shadow" class="my-3 justify-content-center"
              :bgcolor="data.color" @modifyText="handleText" :buttonSize="data.buttonSize" :buttonColor="data.buttonColor" :textInput="data.textInput" >
                      <b-icon ref="icon" style="cursor:pointer;" v-if="data.showDeleteBtn" icon="trash" aria-hidden="true" @click="data.isSet = false" ></b-icon>
              </Card>
            </div>
        </b-col>
        <b-col cols="3"  class="hide p-0" style="overflow-y : auto;" >
          <cardConfigurator  :options="options" @uploadImgBackground="uploadImgBackground" @addCard="addCard" @changeCardWidth="changeCardWidth" @changeBackground="changeBackground" @handleMouseLeave="handleMouseLeave"
          @changeCardOrder="changeCardOrder" @changeCardBackground="changeCardBackground"  @handleCardButton="handleCardButton" @uploadImg="uploadImg" @handleBorder="handleBorder" @handleBorderStyle="handleBorderStyle" @handleShadowBtn="handleShadowBtn" @handleShadow="handleShadow"
          @changeButtonSize="changeButtonSize"  @changeButtonColor="changeButtonColor" @toggleOutline="toggleOutline"
          @changeText="changeText" @changeWeight="changeWeight" @changetextColor="changetextColor" @changeFontSize="changeFontSize"

          ></cardConfigurator>
        </b-col>
      </b-row>
      </div>
</template>

<script>

import Card from "./components/Card.vue";
import cardConfigurator from "./components/cardConfigurator";

export default {
  // comment
  components:{
    Card,
    cardConfigurator,
},
  data(){
    return{
      options : {
      textInputprop:{
        title : "test",
        paragraph : "This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content",
        button : "test me",
      },
      hover : false,
      previousClass : 'w-100',
      focusOn: null ,
      showControlText: null ,
      selectedText: null ,
      cardData: [{
      textInput: {
        title : "Heading 1",
        paragraph : "This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content",
        button : "click me",
      },
      shadow : {
        active : false,
        offset : {x : 0 , y : 8},
        blur : 16,
        spread : 0,
        color : "#000000"
      },
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },
      corner : 0,
      isSet : true,
      img:require('./assets/img1.png') ,
      showButton: true  ,
      showDeleteBtn : false,
      buttonSize : '',
      buttonColor : 'btn-primary',
      id: 0 ,
      imageOrder: 0,
      color : 'white',} ,
      {      
        textInput: {
          title : "Heading 2",
          paragraph : "This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content",
          button : "click me",
        },
        shadow : {
        active : false,
        offset : {x : 0 , y : 8},
        blur : 16,
        spread : 0,
        color : "#000000"
      },
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },
      corner : 0,
      img:require('./assets/img1.png') ,
      isSet : true,
      showButton: false  ,
      showDeleteBtn : false,
      buttonSize : '',
      buttonColor : 'btn-primary',
      imageOrder: 0,
      id: 1 ,
      color : 'white',
      }
      ] ,
      idCount: 3
    } 
          }
  },
  methods: {
    addCard() {
      const newCard = {
        textInput: {
          title : "Heading",
          paragraph : "This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content",
          button : "click me",
        },
        shadow : {
        active : false,
        offset : {x : 0 , y : 8},
        blur : 16,
        spread : 0,
        color : "#000000"
      },
         border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
        },
        corner : 0,
        id: this.options.idCount ,
        img: require('./assets/img1.png') ,
        showButton: false  ,
        isSet : true,
        showDeleteBtn : false,
        buttonSize : '',
        buttonColor : 'btn-primary',
        imageOrder: 0,
        color : 'white',
      }
      this.options.cardData.push(newCard)
      this.options.idCount++; 
    } ,
    changeBackground(color){
        document.body.style.background = color
    },
    changeCardBackground(color){
            this.options.cardData.map( (card)=>{
            if(card.id == this.options.focusOn) {
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
      if(e.type === 'mouseenter'){
          this.options.hover = true
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
        this.options.previousClass = this.$refs.widthSelector.className
        this.options.hover = false
      }
      
      },
      handleFocus(id){
        this.handleDeleteBtn(id) ;
        this.options.focusOn = id ;
        this.options.showControlText = null;
        this.textInputprop = this.options.cardData.find(card => card.id ===this.options.focusOn).textInput ;
     
      },
      handleDeleteBtn(id){
          this.options.cardData.map( (card)=>{
            if(card.id == id) card.showDeleteBtn = true
            else card.showDeleteBtn = false
          })
      },
      changeCardOrder(a){
        let order = 0 ;
        if(a === 'right')
          order = 1 ;
        {
         this.options.cardData.map( (card)=>{
            if(card.id == this.options.focusOn) card.imageOrder = order
          }) 
        }
      },
      handleCardButton(action){
          this.options.cardData.map(card =>{
            if(card.id == this.options.focusOn) {
              if(action === 'del') card.showButton = false
              else card.showButton = true
            }
          })
      },
      handleText(e){
        this.options.showControlText = true ;
        this.options.selectedText = e.target ;
      },
      changeText(cls){
       this.options.selectedText.style.fontSize = ''
        this.options.selectedText.className = '';
        if ( cls !== 'n')
          this.options.selectedText.classList.add(cls);
          
      },
      changeWeight(cls){
        this.options.selectedText.classList.toggle(cls)
      },
      handleMouseLeave(e){
          if(this.options.hover){
              this.$refs.widthSelector.className = '';
              this.$refs.widthSelector.classList.add(this.options.previousClass)
          }
          this.options.hover = false
      },
      changetextColor(clr){
        this.options.selectedText.style.color = clr ;
      },
      uploadImg(e){
        const image = e.target.files[0]
        if(image){
        this.options.cardData.map(card =>{
          if(card.id === this.options.focusOn){
           card.img = window.URL.createObjectURL(image)
           e.target.value= '' ;
           return
           }
        })
        }
      },
      uploadImgBackground(e){
        console.log(e)
        const image = e.target.files[0] ;    
        document.body.style.backgroundImage = 'url(' + window.URL.createObjectURL(image) + ')' ;
        e.target.value = '' ;
      },
      handleBorder(c,type){
        this.options.cardData.map(card => {
          if(card.id === this.options.focusOn){
                      if(type == 'width')
                      card.border.width = c
                      else if(type == 'color')
                      card.border.color = c
                      else
                      card.border.radius = c
  
          }
        })

      },
      handleBorderStyle(style){
        this.options.cardData.map(card =>{
          if(card.id === this.options.focusOn) card.border.style = style
        })
      },
      changeFontSize(fs){
        this.options.selectedText.style.fontSize = fs ;
      },
      changeButtonSize(size){
        this.options.cardData.map(card =>{
          if(card.id === this.options.focusOn) card.buttonSize = size ;
        }) 
      },
      changeButtonColor(clr){
        this.options.cardData.map(card =>{
          if(card.id === this.options.focusOn) card.buttonColor = clr ;
        })        
      },
      toggleOutline(){
        this.options.cardData.map(card =>{
          if(card.id === this.options.focusOn){
            if (!card.buttonColor.includes('outline')){
              const  newColor = 'btn-outline' + card.buttonColor.substring(3, card.buttonColor.length) ;
              card.buttonColor = newColor ;
            }else {
              const newColor =  'btn-' + card.buttonColor.substring(12, card.buttonColor.length) ;
              card.buttonColor = newColor ;
            }
          }
        })  
      },
          handleShadowBtn(value){
        this.options.cardData.map(box=>{
          if(box.id===this.options.focusOn) {
              box.shadow.active = value
             if(value===false){
            box.shadow.offset.x = 0
            box.shadow.offset.y = 0
            box.shadow.color = '#000000'
            box.shadow.spread = 0
            box.shadow.blur = 0
            }
            return;
          }
        })
      },
      handleShadow(value,option){
         this.options.cardData.map(card=>{
          if(card.id===this.options.focusOn) {
            if(option==='x') card.shadow.offset.x = value
            else if(option==='y') card.shadow.offset.y = value
            else if(option==='color') card.shadow.color = value
            else if(option==='blur') card.shadow.blur = value
            else card.shadow.spread = value
          }
        })
      }
    },
    mounted(){
        document.body.addEventListener("click",(e)=>{
          if(e.altKey){
            this.handleFocus(null)
            this.options.showControlText = null
            
          }
        });    },
   computed : {
    filteredCards(){
    return this.options.cardData.filter(card => card.isSet)
    },
    focusedCard(){
    return this.options.cardData.filter( data => data.id === this.options.focusOn) ;
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
@media only screen and (max-width: 970px) {
  .hide 
  {
    display: none;
  }
  #main{
    margin:auto
  }
}


</style>