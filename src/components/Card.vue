<template>

<div @click="handleDeleteBtn"  >
     <slot></slot>
     <div :class="{outsideBorder:showDeleteBtn}" >
  <b-card no-body class="overflow-hidden" style="max-width: 100%" :class="[colorClass.text, colorClass.background ]" ref="bigDiv" data-mdb-toggle="animation" data-mdb-animation-reset="true" data-mdb-animation="slide-out-right">
    <b-row no-gutters >
      <b-col  :order="imgLeft" sm="12" md="4" >
        <b-card-img :src="img" alt="Image" class="rounded-0 " style="height: 100%;"></b-card-img>
      </b-col>
      <b-col   class="p-4" sm="12" md="8" > 
        <b-card-title>
        <p  @dblclick="modifyText">{{textInput.title}}</p>
       </b-card-title>
        <p  @dblclick="modifyText" style="max-width: 100%;">{{textInput.paragraph}}</p>
       <a href="#" v-if="Sbutton"  class="btn" :class="[buttonSize,buttonColor]" role="button" aria-pressed="true">{{ textInput.button }}</a>

      </b-col>
    </b-row>
  </b-card>
  </div>
</div>
</template>


<script>


export default {
    props: ['img','Sbutton' , 'imgLeft','showDeleteBtn','bgcolor','border','corner','buttonSize','buttonColor','shadow','textInput'] ,
    data(){
        return{
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
      const b= this.border.width+"px "+this.border.style+" "+this.border.color
      this.$refs.bigDiv.style.border = b
      this.$refs.bigDiv.style.borderRadius = this.border.radius+"px"
    },
    handleShadow(){
      const s = this.shadow.offset.x+"px "+this.shadow.offset.y+"px "+this.shadow.blur+"px "+this.shadow.spread+"px "+this.shadow.color
      this.$refs.bigDiv.style.boxShadow = s
    }
    
    } ,
    watch  : {
      bgcolor : function(){
        this.handleBackgroudColor()
      },
      'border.width' : function(){
        this.handleBorder()
      },
      'border.radius' : function(){
        this.handleBorder()
      },
        'border.color' : function(){
        this.handleBorder()
      },
      'border.style' : function(){
        this.handleBorder()
      },
      'shadow.color' : function(){
        this.handleShadow()
      },
      'shadow.blur' : function(){
        this.handleShadow()
      },
      'shadow.spread' : function(){
        this.handleShadow()
      },
    'shadow.offset.x' : function(){
      this.handleShadow()
    },
      'shadow.offset.y' : function(){
        this.handleShadow()
      },
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