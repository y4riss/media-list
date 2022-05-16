<template>

<div @click="handleDeleteBtn"  >
     <slot></slot>
     <div :class="{outsideBorder:showDeleteBtn}" >
  <b-card no-body class="overflow-hidden" style="max-width: 100%" :class="[colorClass.text, colorClass.background ]" ref="bigDiv" >
    <b-row no-gutters >
      <b-col  :order="imgLeft" sm="12" md="4" >
        <b-card-img :src="img" alt="Image" class="rounded-0 " style="height: 100%;"></b-card-img>
      </b-col>
      <b-col   class="p-4" sm="12" md="8" > 
        <b-card-title>
        <p contenteditable="true" @dblclick="modifyText">{{title}}</p>
       </b-card-title>
        <p contenteditable="true" @dblclick="modifyText">{{text}}</p>
        <b-button v-if="Sbutton" href="#" variant="primary">Go somewhere</b-button>
      </b-col>
    </b-row>
  </b-card>
  </div>
</div>
</template>


<script>


export default {
    props: ['img' , 'Sbutton' , 'imgLeft','showDeleteBtn','bgcolor','border','corner'] ,
    data(){
        return{
            text : 'This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content',
            title : 'Heading',
            colorClass: {
              text: null ,
              background: null
            }
        }
    },
    methods : {
      handleDeleteBtn(){
        this.$emit('focus')
      },
      handleBackgroudColor(){
        console.log(this.bgcolor,'ff')
        if (this.bgcolor === 'white'){
          this.colorClass.text = 'text-dark'
          this.colorClass.background = 'bg-white'
        }
        else if (this.bgcolor === 'light gray'){
          this.colorClass.text = 'text-dark'
          this.colorClass.background = 'bg-light'
        }
        else if (this.bgcolor === 'dark gray'){
          this.colorClass.text = 'text-light'
          this.colorClass.background = 'bg-secondary'
        }
        
    },
    modifyText (e){
        this.$emit('modifyText',e) ;
    },
    handleBorder(){
      const borderWidth = this.border+"px"
      this.$refs.bigDiv.style.borderWidth = borderWidth

    },
    handleCorner(){
      const cornerWidth = this.corner+"px"
      this.$refs.bigDiv.style.borderRadius = cornerWidth

    }
    
    } ,
    watch  : {
      bgcolor : function(){
        this.handleBackgroudColor()
      },
      border : function(){
        this.handleBorder()
      },
      corner : function(){
          this.handleCorner()
      }
    }

    }
</script>

<style scoped>
p{
  outline: none;
}

.outsideBorder{
  padding : 1em;
box-shadow: 1px 1px 5px #0cb6cc;}
</style>